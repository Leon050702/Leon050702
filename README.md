name: Refresh profile cards
# Fetches the stats + streak SVGs twice a day and commits them into the repo.
# Why commit instead of hot-linking: the README then renders instantly, works
# offline, and never shows a broken image when the upstream services are down
# or rate-limited. Each card is fetched for BOTH colour schemes.
on:
  schedule:
    - cron: "17 3 * * *" # daily, 03:17 UTC
  workflow_dispatch:
  push:
    branches: [main]
permissions:
  contents: write
concurrency:
  group: profile-cards
  cancel-in-progress: true
jobs:
  cards:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v5
      - name: Fetch cards
        env:
          USERNAME: ${{ github.repository_owner }}
        run: |
          set -uo pipefail
          mkdir -p assets/cards
          # Keep the previous file if the fetch fails - a stale card beats a 404.
          fetch () {
            local url="$1" out="$2"
            if curl -fsSL --retry 3 --retry-delay 2 --max-time 30 "$url" -o "$out.tmp" \
               && grep -qi "<svg" "$out.tmp"; then
              mv "$out.tmp" "$out"
              echo "ok    $out"
            else
              rm -f "$out.tmp"
              echo "skip  $out (service unavailable, keeping previous copy)"
            fi
          }
          STATS="https://github-readme-stats.vercel.app/api?username=${USERNAME}&show_icons=true&include_all_commits=true&count_private=true&hide_border=true&disable_animations=true&rank_icon=github"
          STREAK="https://streak-stats.demolab.com?user=${USERNAME}&hide_border=true&disable_animations=true&border=00000000"
          fetch "${STATS}&bg_color=FAF8F3&title_color=14161A&text_color=5F6672&icon_color=C4462B" \
                assets/cards/stats-light.svg
          fetch "${STATS}&bg_color=0E1116&title_color=F2F0EB&text_color=9BA3AF&icon_color=FF7A55" \
                assets/cards/stats-dark.svg
          fetch "${STREAK}&background=FAF8F3&ring=C4462B&fire=C4462B&currStreakNum=14161A&sideNums=14161A&currStreakLabel=14161A&sideLabels=5F6672&dates=8A929E" \
                assets/cards/streak-light.svg
          fetch "${STREAK}&background=0E1116&ring=FF7A55&fire=FF7A55&currStreakNum=F2F0EB&sideNums=F2F0EB&currStreakLabel=F2F0EB&sideLabels=9BA3AF&dates=6E7681" \
                assets/cards/streak-dark.svg
      - name: Commit if anything changed
        run: |
          git config user.name  "github-actions[bot]"
          git config user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git add assets/cards
          if git diff --staged --quiet; then
            echo "No changes - cards are already current."
          else
            git commit -m "chore: refresh profile cards [skip ci]"
            git push
          fiv


name: Add GitHub Sponsors to Readme
on: [push]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout 🛎️
        uses: actions/checkout@v2

      - name: List current folder location, files and show users GitHub token
        run: |
          pwd
          ls -a
          echo "Your GitHub secrets is ${{ secrets.GITHUB_TOKEN }}."

      - name: Generate Sponsors 💖
        uses: JamesIves/github-sponsors-readme-action@v1.0.8
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          file: 'README.md'

      - name: Deploy to GitHub Pages 🚀
        uses: JamesIves/github-pages-deploy-action@v4
        with:
          branch: main
          folder: '.'

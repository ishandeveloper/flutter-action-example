<center>
<img src="./assets/hero.png"><br>
<h3> Flutter APK Generator Action</h3>
<hr>
</center>

This repository is dedicated to a GitHub Action for generating a new apk and pushing it to the repository, whenever changes are made in master branch.

With ease:

  - Generate new release apk's whenever changes are pushed
  - distribute and test your apps quickly among all collaborators
  - keep a track of every apk release version.

<pre>
THIS REPOSITORY WAS CREATED AS A PART OF ACTIONS HACKATHON HOSTED BY DEV.TO AND GITHUB,
</pre>


### Usage
Example Workflow file

An example workflow to set up your flutter apk generator action quickly.

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: Setting up Flutter SDK
        uses: subosito/flutter-action@v1
        with:
          channel: stable

      - name: Fetch Packages
        run: flutter pub get
      #     - run: flutter test
      - name: Build APK
        run: flutter build apk

      - name: Copy APK To Parent Directory
        run: cp ./build/app/outputs/flutter-apk/app-release.apk ./app.apk

      - name: Commit APK
        run: git add ./app.apk

      - name: Configure Github
        run: |
          git config --local user.email "you@email.com"
          git config --local user.name "yourusername"
          git commit -m "Generated APK" -a

      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}

```

## Learn More

You can learn more about Github actions and Flutter [here](https://docs.github.com/en/actions) and [here](https://flutter.dev/docs) respectively.

##### Made with ♥ by <a href="https://github.com/ishandeveloper">ishandeveloper</a>

[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://github.com/ishandeveloper)
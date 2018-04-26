# ark-gource

### Install requirements (Mac OS X)

```
brew install gource
brew install ffmpeg
```

### Get Ark's repos
https://api.github.com/orgs/arkecosystem/repos?per_page=200

### Use http://www.jsonquerytool.com/ to filter the clone_url from each repo, with the query:

`$.[]clone_url`

### Download all repos
```
git clone https://github.com/ArkEcosystem/wiki.git
git clone https://github.com/ArkEcosystem/ark-js.git
git clone https://github.com/ArkEcosystem/ark-node.git
git clone https://github.com/ArkEcosystem/ark-desktop.git
git clone https://github.com/ArkEcosystem/ark-monitor.git
git clone https://github.com/ArkEcosystem/ark-liteclient-template.git
git clone https://github.com/ArkEcosystem/ark-paperwallet.git
git clone https://github.com/ArkEcosystem/ark-delegate-app.git
git clone https://github.com/ArkEcosystem/AIPs.git
git clone https://github.com/ArkEcosystem/ark-lite-wallet.git
git clone https://github.com/ArkEcosystem/ark-client.git
git clone https://github.com/ArkEcosystem/ark-ios-monitor.git
git clone https://github.com/ArkEcosystem/ark-java.git
git clone https://github.com/ArkEcosystem/ark-java-example.git
git clone https://github.com/ArkEcosystem/arky.git
git clone https://github.com/ArkEcosystem/ark-net.git
git clone https://github.com/ArkEcosystem/ark-go.git
git clone https://github.com/ArkEcosystem/ark-ledger.git
git clone https://github.com/ArkEcosystem/ark-ts.git
git clone https://github.com/ArkEcosystem/nucleid.git
git clone https://github.com/ArkEcosystem/ark-explorer.git
git clone https://github.com/ArkEcosystem/ark-rpc.git
git clone https://github.com/ArkEcosystem/ARKcommander.git
git clone https://github.com/ArkEcosystem/ARK.io-Translations.git
git clone https://github.com/ArkEcosystem/ark-android-monitor.git
git clone https://github.com/ArkEcosystem/ark-mobile.git
git clone https://github.com/ArkEcosystem/ark-deployer.git
git clone https://github.com/ArkEcosystem/pythark.git
git clone https://github.com/ArkEcosystem/ark-kotlin.git
git clone https://github.com/ArkEcosystem/ark-qrcode.git
git clone https://github.com/ArkEcosystem/arkecosystem.github.io.git
git clone https://github.com/ArkEcosystem/ark-azure.git
git clone https://github.com/ArkEcosystem/ARK-Bounty-Program.git
git clone https://github.com/ArkEcosystem/docs.git
git clone https://github.com/ArkEcosystem/ARK-Development-Guidelines.git
git clone https://github.com/ArkEcosystem/ARK-Peers.git
```

### Generate a Gource custom log files for each repository using the --output-custom-log FILE option:
```
gource --output-custom-log wiki.txt wiki
gource --output-custom-log ark-js.txt ark-js
gource --output-custom-log ark-node.txt ark-node
gource --output-custom-log ark-desktop.txt ark-desktop
gource --output-custom-log ark-monitor.txt ark-monitor
gource --output-custom-log ark-liteclient-template.txt ark-liteclient-template
gource --output-custom-log ark-paperwallet.txt ark-paperwallet
gource --output-custom-log ark-delegate-app.txt ark-delegate-app
gource --output-custom-log AIPs.txt AIPs
gource --output-custom-log ark-lite-wallet.txt ark-lite-wallet
gource --output-custom-log ark-client.txt ark-client
gource --output-custom-log ark-ios-monitor.txt ark-ios-monitor
gource --output-custom-log ark-java.txt ark-java
gource --output-custom-log ark-java-example.txt ark-java-example
gource --output-custom-log arky.txt arky
gource --output-custom-log ark-net.txt ark-net
gource --output-custom-log ark-go.txt ark-go
gource --output-custom-log ark-ledger.txt ark-ledger
gource --output-custom-log ark-ts.txt ark-ts
gource --output-custom-log nucleid.txt nucleid
gource --output-custom-log ark-explorer.txt ark-explorer
gource --output-custom-log ark-rpc.txt ark-rpc
gource --output-custom-log ARKcommander.txt ARKcommander
gource --output-custom-log ARK.io-Translations.txt "ARK.io-Translations"
gource --output-custom-log ark-android-monitor.txt ark-android-monitor
gource --output-custom-log ark-mobile.txt ark-mobile
gource --output-custom-log ark-deployer.txt ark-deployer
gource --output-custom-log pythark.txt pythark
gource --output-custom-log ark-kotlin.txt ark-kotlin
gource --output-custom-log ark-qrcode.txt ark-qrcode
gource --output-custom-log arkecosystem.txthub.io.txt "arkecosystemhub.io"
gource --output-custom-log ark-azure.txt ark-azure
gource --output-custom-log ARK-Bounty-Program.txt ARK-Bounty-Program
gource --output-custom-log docs.txt docs
gource --output-custom-log ARK-Development-Guidelines.txt ARK-Development-Guidelines
gource --output-custom-log ARK-Peers.txt ARK-Peers
```

### Join the logs together, and sort them numerically by the first column (the time):

```
cat AIPs.txt ark-azure.txt ark-ios-monitor.txt ark-liteclient-template.txt ark-ts.txt ARK-Bounty-Program.txt ark-client.txt ark-java-example.txt ark-mobile.txt arky.txt ARK-Development-Guidelines.txt ark-delegate-app.txt ark-java.txt ark-monitor.txt docs.txt ARK-Peers.txt ark-deployer.txt ark-js.txt ark-net.txt nucleid.txt ARK.io-Translations.txt ark-desktop.txt ark-kotlin.txt ark-node.txt pythark.txt ARKcommander.txt ark-explorer.txt ark-ledger.txt ark-paperwallet.txt wiki.txt ark-android-monitor.txt ark-go.txt ark-lite-wallet.txt ark-qrcode.txt | sort -n > combined.txt
```

### Feed result into gource:

```
gource combined.txt --seconds-per-day 0.15 --logo ark-logo.png -1920x1080 --file-idle-time 0 --auto-skip-seconds 0.75 --multi-sampling --stop-at-end --highlight-users --hide filenames,mouse,progress --max-files 0 --background-colour 000000 --disable-bloom --font-size 24 --output-ppm-stream - --output-framerate 30 -o - | ffmpeg -y -r 60 -f image2pipe -vcodec ppm -i - -vcodec libx264 -preset ultrafast -pix_fmt yuv420p -crf 1 -threads 0 -bf 0 output.mp4
```

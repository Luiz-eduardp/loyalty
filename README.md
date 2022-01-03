# fidelity (fidelity)

...

## Install the dependencies
```bash
npm install
```

### Start the app in development mode (hot-code reloading, error reporting, etc.)
```bash
quasar dev
```

### Lint the files
```bash
npm run lint
```

### Build the app for production
```bash
quasar build
```

### Customize the configuration
See [Configuring quasar.conf.js](https://quasar.dev/quasar-cli/quasar-conf-js).


$ quasar build -m electron -P always

# ..or the longer form:
$ quasar build --mode electron --publish always



$ quasar dev -m electron






# ..or the longer form:
$ quasar dev --mode electron

# passing extra parameters and/or options to
# underlying "electron" executable:
$ quasar dev -m electron -- --no-sandbox --disable-setuid-sandbox
# when on Windows and using Powershell:
$ quasar dev -m electron '--' --no-sandbox --disable-setuid-sandbox


Building for Production
$ quasar build -m electron

# ..or the longer form:
$ quasar build --mode electron

$ quasar build -m electron -d

# ..or the longer form
$ quasar build -m electron --debug




# sparta-site

A website for the spatial audio VST plug-ins installer, which includes the SPARTA suite, COMPASS suite, HO-DirAC suite, CroPaC-Binaural decoder, and the HO-SIRR application.

The website may be hosted locally with:
```
npm run start 
```

The website can then be viewed using a web browser, through the address this command provides. For example:
```
Web Server is available at //localhost:1313/
```

Note that running this website locally requires hugo and node to be installed. E.g.:
```
brew install hugo
brew install node
npm install shx
```

## Deployment

A github action is automatically run every time a commit is pushed to the master branch, which builds and deploys the website.

The website is hosted here: [https://leomccormack.github.io/sparta-site/](https://leomccormack.github.io/sparta-site/)

## Contributing

We are by no means exports in website design, so if you happen to be a website, Hugo or Doks guru and spot anything that can be improved, then please feel free to do so and submit a pull request.

Any suggestions on how to make the plug-in descriptions, install-instructions, FAQ etc. more useful/informative is also welcome : )

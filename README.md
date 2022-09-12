# i18n for NatSpec

Currently NatSpec does not support internationalization (i18n), this repo is an example of how i18n support could be implemented using NatSpec

## What to translate?
I believe that the only two important things to translate in the metadata are:
* devdoc
* userdoc

## How to include translations?
* Add an additional custom NatSpec field in the contract docs called translation-xx where xx is the language (it, en)
* The translation-xx field contains an IPFS CID pointing to a json containing userdoc and devdoc translated into italian.
    ```
    ...
    /// @title A simulator for trees
    ...
    /// @custom:translation-it ipfs://QmZbQCua5YKZ5ZxT2rdcap31AmyMwNfC6FkzMVBuzN3SYa
    contract Tree {
        ...
    ```
* The standard natspec fields will be used in the case of the user is asking for a language not translated.

## How to use translations?
* After fetching NatSpec docs, search for the translation the user is asking
    * `translation-it` key in the `devdoc` object
* If found get the file from IPFS (secure only if it is not an IPNS CID)

## PRO
* User interfaces finally translated
* Secure and Sourcify compatible, because changing the IPFS CID would cause the metadata hash to change

## CON
* In order to update translation the contract must be redeployed
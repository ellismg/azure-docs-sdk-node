# CustomerProvidedEncryptionKey

All data in Azure Storage is encrypted at-rest using an account-level encryption key.
In versions 2018-06-17 and newer, you can manage the key used to encrypt blob contents
and application metadata per-blob by providing an AES-256 encryption key in requests to the storage service.

``` swift
public struct CustomerProvidedEncryptionKey:​ Codable, Equatable
```

When you use a customer-provided key, Azure Storage does not manage or persist your key.
When writing data to a blob, the provided key is used to encrypt your data before writing it to disk.
A SHA-256 hash of the encryption key is written alongside the blob contents,
and is used to verify that all subsequent operations against the blob use the same encryption key.
This hash cannot be used to retrieve the encryption key or decrypt the contents of the blob.
When reading a blob, the provided key is used to decrypt your data after reading it from disk.
In both cases, the provided encryption key is securely discarded
as soon as the encryption or decryption process completes.

## Inheritance

`Codable`, `Equatable`

## Initializers

### `init(keyData:​)`

Initialize a `CustomerProvidedEncryptionKey` structure.

``` swift
public init(keyData:​ Data)
```

#### Parameters

  - keyData:​ - keyData:​ The binary AES-256 encryption key.

## Properties

### `keyData`

Base64-encoded AES-256 encryption key.

``` swift
let keyData:​ Data
```

### `hash`

Base64-encoded SHA256 of the encryption key.

``` swift
var hash:​ String
```

### `algorithm`

Specifies the algorithm to use when encrypting data using the given key. Must be AES256.

``` swift
let algorithm = "AES256"
```
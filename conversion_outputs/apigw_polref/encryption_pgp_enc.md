{
"title": "PGP encrypt and sign",
"linkTitle": "PGP encrypt and sign",
"date": "2019-10-17",
"description": "You can use the **PGP Encrypt and Sign**\\nfilter to generate a Pretty Good Privacy (PGP)-encrypted message. This filter enables you to configure the PGP public key used when encrypting the message body (the `content.body` attribute). You can also configure advanced options such as whether the message outputs ASCII armor, or whether it uses a symmetrically encrypted integrity protected data packet to protect against modification attacks."
}
﻿
<div id="p_encryption_pgp_enc_overview">

Overview
--------

You can use the **PGP Encrypt and Sign**
filter to generate a Pretty Good Privacy (PGP)-encrypted message. This filter enables you to configure the PGP public key used when encrypting the message body (the `content.body` attribute). You can also configure advanced options such as whether the message outputs ASCII armor, or whether it uses a symmetrically encrypted integrity protected data packet to protect against modification attacks.

**PGP Encrypt and Sign** filter does not encrypt any files attached to your message.

For example, using the default options, the **PGP Encrypt and Sign**
filter creates a PGP-encrypted message such as the following, and overwrites the `content.body` attribute with the encrypted version:

``` {space="preserve"}
-----BEGIN PGP MESSAGE-----
Version:BCPG v1.46
```

``` {space="preserve"}
hQIOA3ePizxHLIA8EAgAmVNAgJO7TXI9vWCJHZS27r4FIfZIYWNc0+MiQ3H+LZrW
29Wageetg5N7cFAbRpG28iKYSE5O0uFMThuWuhnMZ/GtRwMogiRsNyBY0Cq0LKaG
7oIbkjWE1BHdWXQLWW44zYl8ekTWJ4ZPNCemTtHyULB9QwuWx5b6QfAyh1jvFrSN
ub9mQzU8caY7xQrVgWii1tBFOzTcGw6/Vb7AtMZfwGGjqmzYLT5pLozWUKB0gZe1
/7wpWDsHsn+53lrRXdoqwvAhY2AnOLPyrrVsykXS38YtIh9N5D+uCCvgmICej9Ok
iieh1hgGnuzw3VdQ6n3TS0t/Xk3shB95I3IkXU1l4ggAjPSnf9qEuN2u8dsRooNR
J6nYWs/OGwBSj0/MtssoRAcEVYu93tITUXqybduq8CATHGD8at4WRiTLOcndgJTp
0aUU+aOi3l3SsnrlpPSKIu18K9AqFCE+lafdXKlqU2OaGMBbsU22Vy6SkDgSXuGg
EOG0KYHRdrAntHJiO3qrJRTd8BDrPc5PZWUwDfCUWuQRMJiJVp0bxrK8Qzz/Ni7T
XgRSL1cYzAQRsQAbne69On+5n+NWO1Qcx9SnSimBtPOQXJfff+a+Wb45ABj5TdYr
4PCd2OJ0uOapSWfiSA5mZ1sB9hEAR0FidXs1iAploun1qggNYZK94BGGXblnTCzR
ccnARKqWmWanr1VVnp6fs9WI6I3zkiCGTJlQMNa0UKZdEPe1wJb7NHgJFMKrwN1X
3rSVyUWiovnYYMlDGBHG/RWGsTSd0LT7VugtIByefCI2G7WevgLUJbOq+U/0Sh6A
82oMNuWbXbDTp3pfZae/SHqOyEdDp5zsGqZ/F4M7CQFx63XCIBsFA6JRj6GdYqYf
dewuej3WJtRDdHmikjb3o7Utl8fFhKjA9GdEZueG9ls+XcAx21iBT656HRof8wio
oSca8ui3SYbhZ+0uzwImDJ0054P3Xr24+iwI4vlKjiQNY23GjXsVa2rQn6VHT60o
CYo08tDYBH4gyetLAqczCVyh6sff9SqX=qkB0
```

``` {space="preserve"}
-----END PGP MESSAGE-----
```

For an example use case, see [*PGP decrypt and verify* on page 1](encryption_pgp_dec.htm).

You can also use the **PGP Encrypt and Sign**
filter to digitally sign messages passing through the API Gateway pipeline. Messages signed by API Gateway can be verified by the recipient by validating the signature using the public PGP key of the signer. Signed messages received by API Gateway can be verified in the same way.

{{< alert title="Note" color="primary" >}}PGP encryption and signing require two different keys: a public key for encryption and your own private key for signing. {{< /alert >}}

</div>

<div id="p_encryption_pgp_enc_conf">

General settings
----------------

Complete the following field on the **PGP Encrypt and Sign**
window:

**Name**:\
Enter an appropriate name for the filter to display in a policy.

</div>

<div id="p_encryption_pgp_enc_encrypt">

Encrypt and sign settings
-------------------------

Complete the following fields on the **Encrypt and Sign**
tab:

**Encrypt**:\
Select whether to use this filter to PGP encrypt an outgoing message with a public key.

**Encryption Key location (Public Key)**:\
If you selected the **Encrypt**
option, select the location of the public key from one of the following options:

-   **PGP Key Pair list**:\
    Click the browse button on the right, and select a PGP key pair configured in the certificate store. If no PGP key pairs have already been configured, right-click **PGP Key Pairs**, and select **Add PGP Key**. For details on configuring PGP key pairs, see
    [Manage X.509 certificates and keys](/csh?context=619&product=prod-api-gateway-77)
    in the
    [API Gateway Policy Developer Guide](/bundle/APIGateway_77_PolicyDevGuide_allOS_en_HTML5/)
    .
-   **Alias**:\
    Enter the alias name used to look up the PGP key in the certificate store (for example, `My PGP Test Key`). Alternatively, you can enter a selector expression with the name of a message attribute that contains the alias. The value of the selector is expanded at runtime (for example, `${my.pgp.test.key.alias}`).
-   **Message attribute**:\
    Enter a selector expression with the name of the message attribute that contains the key. The value of the selector is expanded at runtime (for example, `${my.pgp.test.public.key}`).

For more details on selectors, see
[Select configuration values at runtime](/csh?context=630&product=prod-api-gateway-77)
in the
[API Gateway Policy Developer Guide](/bundle/APIGateway_77_PolicyDevGuide_allOS_en_HTML5/)
.

**Sign**:\
Select whether to use this filter to sign an outgoing message with a private key.

**Signing Key location (Private Key)**:\
If you selected the **Sign**
option, select the location of the private key from one of the following options:

-   **PGP Key Pair list**:\
    Click the browse button on the right, and select a PGP key pair configured in the certificate store. If no PGP key pairs have already been configured, right-click **PGP Key Pairs**, and select **Add PGP Key**. For details on configuring PGP key pairs, see
    [Manage X.509 certificates and keys](/csh?context=619&product=prod-api-gateway-77)
    in the
    [API Gateway Policy Developer Guide](/bundle/APIGateway_77_PolicyDevGuide_allOS_en_HTML5/)
    .
-   **Alias**:\
    Enter the alias name used to look up the PGP key in the certificate store (for example, `My PGP Test Key`). Alternatively, you can enter a selector expression with the name of a message attribute that contains the alias. The value of the selector is expanded at runtime (for example, `${my.pgp.test.key.alias}`).
-   **Message attribute**:\
    Enter a selector expression with the name of the message attribute that contains the key. The value of the selector is expanded at runtime (for example, `${my.pgp.test.private.key}`).

For more details on selectors, see
[Select configuration values at runtime](/csh?context=630&product=prod-api-gateway-77)
in the
[API Gateway Policy Developer Guide](/bundle/APIGateway_77_PolicyDevGuide_allOS_en_HTML5/)
.

**Signing Method**:\
If you selected to sign but not encrypt the outgoing message, select the signing method from one of the following options:

-   **Compressed**:\
    Compresses the message and creates a hash of the contents before signing. Because the message is contained within the signature this signature can be used in place of the message. The typical use of this method produces a signature in printable ASCII form (ASCII Armor). This option can be turned off to produce a binary signature.
-   **Clear signed**:\
    Clear signing a message leaves the message intact and adds the signature beneath the clear message text. This provides for optional verification of the message signature and contents. The output has the content type `application/pgp-signature`. It is not possible to clear sign binary objects.
-   **Detached signature (MIME)**:\
    Creates a multipart MIME document where the message remains in clear text and the signature is attached as a MIME part.

**Encrypt and Sign Method**:\
If you selected to encrypt and sign the outgoing message, select the encrypt and sign method from one of the following options:

-   **Encrypt and Sign in One Pass**:\
    Encrypts and signs the message in a single pass. This is the default setting. This enables the receiver to decrypt and verify in a single pass.
-   **Encrypt and Sign in Two Passes**:\
    Signs the message in a first pass, and then encrypts it in a second pass. Because the message is signed before it is encrypted, this means that the message must be decrypted first before the signature can be verified.

</div>

<div id="p_encryption_pgp_enc_adv_conf">

Advanced settings
-----------------

Complete the following fields on the **Advanced**
tab:

**ASCII Armor Output**:\
Select whether to output the binary message data as ASCII Armor. ASCII Armor is a special text format used by PGP to convert binary data into printable ASCII text. ASCII Armored data is especially suitable for use in email messages, and is also known as Radix-64 encoding. This option is selected by default.

**Symmetric Encrypted Integrity Protected Data Packet**:\
Select whether the message uses a Symmetrically Encrypted Integrity Protected Data packet. This is a variant of the Symmetrically Encrypted Data packet, and is used detect modifications to the encrypted data. This option is selected by default.

**Symmetric Key Algorithm**:\
Select a symmetric-key algorithm to use to encrypt the data. The default is `CAST5`.

**Hash Algorithm**:\
Select a hash algorithm to use to protect against modification. The default is `SHA1`.

**Compression Algorithm**:\
Select a compression algorithm to use to compress the data. The default is `ZIP`.

</div>

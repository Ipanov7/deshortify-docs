# URL Deshortify <img src="https://cdn-icons.flaticon.com/png/512/1049/premium/1049357.png?token=exp=1646082596~hmac=542ee8d73fb95bc684a14b0bceeb9152" alt="Deshortify logo" style="width:200px"/>

Tired of suspicious shortened URLs? With URL Deshortify you can inspect any endpoint, figure out where it is leading you and if it's safe. Deshortify will:

* find out where the shortened URL is really leading you
* figure out if the landing page is protected with HTTPS
* doublecheck the website certificate and assert its validity

## Example usage
Let's take a shortened url like https://bit.ly/3pkH5T9. Where is it pointing to? Just make a request!

`curl -X GET https://some-endpoint.deshortify.com/inspect?url=https://bit.ly/3pkH5T9`

and you get:

```json
{
  "target_url":"https://github.com/Ipanov7/deshortify-docs"
  "is_tls":true
  "is_redirect":true
  "tls_certificate":"OK"
}
```

## Response details

* `target_url`: the actual URL destination
* `is_tls`: whether the `target_url` is protected by some kind of TLS certificate
* `is_redirect`: if `true`, the inspected URL will redirect to the `target_url`. Otherwise, it is already the final URL
* `tls_certificate`: additional information about the TLS certificate

## TLS certificate statuses

| Status   |      Description |
|:----------:|:----------------|
|OK|The certificate is valid and trustworthy. This is not a guarantee that the target webpage is safe, but it is a starting point|
|WRONG_HOST|The certificate subject does not match the webpage domain|
|EXPIRED|The certificate is no longer valid|
|SELF_SIGNED|The certificate is self-signed|
|UNVERIFIED|Impossible to verify the certificate|


## Try it out!
<a href="https://rapidapi.com/lorisocchipinti/api/url-deshortify" target="_blank">
    <img src="https://files.readme.io/1de5087-rapidapi-badge-light.png" width="215" alt="Try Deshortify!">
</a>

## Credits
Detective Doggie is from [Freepik - Flaticon](https://www.flaticon.com/free-icons/detective)

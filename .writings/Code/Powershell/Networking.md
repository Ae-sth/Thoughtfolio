>PowerShell can use `Invoke-WebRequest` to send HTTP requests.

```powershell
Invoke-WebRequest www.indented.co.uk -Method OPTIONS
```

>If a connection to a web service uses HTTPS (HTTP over Secure Sockets Layer (SSL)), the certificate must be validated before a connection can complete and a request can be completed. If a web service has an invalid certificate, an error will be returned.


```powershell
Invoke-WebRequest https://expired.badssl.com/ -SkipCertificateCheck # to skip the verification

# OR (the complicated way to skip all the time)

Class AcceptAllPolicy: System.Net.ICertificatePolicy { 
	[Boolean] CheckValidationResult( [System.Net.ServicePoint] $servicePoint,
	[System.Security.Cryptography.X509Certificates.X509Certificate] $certificate,
	[System.Net.WebRequest] $webRequest, [Int32] $problem ) { 
		return $true
	} 
} 
[System.Net.ServicePointManager]::CertificatePolicy = [AcceptAllPolicy]::new()
```

>A REST-compliant web service allows a client to interact with the service using a set of predefined stateless operations. REST is not a protocol; it is an architectural style. Whether or not an interface is truly REST-compliant is not particularly relevant when the goal is to use one in PowerShell.

>The `Invoke-RestMethod` command can execute methods exposed by web services. The name of a method is part of the Uniform Resource Identifier (URI); it is important not to confuse this with the Method parameter. The Method parameter is used to describe the HTTP method. <u>By default, `Invoke-RestMethod` uses HTTP GET</u>.


```powershell
# basic invoke
Invoke-RestMethod -Uri https://api.github.com/users/powershell/repos

# To produce the effect of the URL below,
# URL: https://api.github.com/ search/code?q=Get-Content+language:powershell+repo:powershell/powershell.

# You can use,
using assembly System.Web 
$queryString = [System.Web.HttpUtility]::ParseQueryString('') 
$queryString.Add( 'q', 'Get-Content language:powershell repo:powershell/powershell' ) 
$uri = 'https://api.github.com/search/code?{0}' -f $queryString 
Invoke-RestMethod $uri

# OR
Invoke-RestMethod -Uri https://api.github.com/search/code -Body @{ q = 'Get-Content language:powershell repo:powershell/powershell' }

# Invoke-RestMethod converts the body (a Hashtable) to JSON and handles any encoding required. The result of the search is the same whether the body or a query string is used.

```

Few more examples to show other methods and working with authentication,

```powershell
# post request to get a token
$params = @{ 
	Uri = 'https://github.com/login/oauth/access_token' 
	Method = 'POST' 
	Body = @{ 
		client_id = $clientId 
		client_secret = $clientSecret 
		code = $authorizationCode 
	} 
}
$response = Invoke-RestMethod @params 
$token = [System.Web.HttpUtility]::ParseQueryString($response)['access_token']

# using the token
$headers = @{ 
	Authorization = 'token {0}' -f $token 
} 
Invoke-RestMethod 'https://api.github.com/user/emails' -Headers $headers
```



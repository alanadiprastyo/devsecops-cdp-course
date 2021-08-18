Use gosec to find security issues
===============================

Learn how to run static analysis scans on Golang code using gosec
---------

In this scenario, you will learn how to run gosec scan on Golang code.

You will need to download the code, install the SAST tool called gosec and then finally run the SAST scan on the code.

Download the source code
----------
We will do all the exercises locally first in DevSecOps-Box, so let’s start the exercise.

First, we need to download the source code of the project from our git repository.

```
git clone https://gitlab.practical-devsecops.training/pdso/golang.git webapp

cd webapp
```

Install gosec
----------
> GoSec inspects source code for security problems by scanning the Go AST, also can be configured to only run a subset of rules, to exclude certain file paths, and produce reports in different formats
>
> You can find more details about the project at https://github.com/securego/gosec

Our system doesn’t have Golang installed, so we need to install it with the following command.

```
curl -s https://dl.google.com/go/go1.15.1.linux-amd64.tar.gz | tar xvz -C /usr/local
```

We also need to configure GOROOT, GOPATH and PATH variables so golang can find binaries and third party libraries.

```
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
```
Let’s install gosec on the system to perform static analysis.

```
curl -sfL https://raw.githubusercontent.com/securego/gosec/master/install.sh | sh -s v2.4.0
```
output
```
securego/gosec info checking GitHub for tag 'v2.4.0'
securego/gosec info found version: 2.4.0 for v2.4.0/linux/amd64
securego/gosec info installed ./bin/gosec
```

> You guessed it right. Use native tools to install it. For e.g., go get.

```
go get github.com/securego/gosec/v2/cmd/gosec
```
We have successfully installed gosec, let’s explore the functionality it provides us.

```
gosec --help 
```

output

```
gosec - Golang security checker

gosec analyzes Go source code to look for common programming mistakes that
can lead to security problems.

VERSION: 2.4.0
GIT TAG: v2.4.0
BUILD DATE: 2020-07-24T07:54:54Z

USAGE:

        # Check a single package
        $ gosec $GOPATH/src/github.com/example/project

        # Check all packages under the current directory and save results in
        # json format.
        $ gosec -fmt=json -out=results.json ./...

        # Run a specific set of rules (by default all rules will be run):
        $ gosec -include=G101,G203,G401  ./...

        # Run all rules except the provided
        $ gosec -exclude=G101 $GOPATH/src/github.com/example/project/...


OPTIONS:

  -conf string
        Path to optional config file
  -confidence string
        Filter out the issues with a lower confidence than the given value. Valid options are: low, medium, high (default "low")
  -exclude string
        Comma separated list of rules IDs to exclude. (see rule list)
  -exclude-dir value
        Exclude folder from scan (can be specified multiple times)
  -fmt string
        Set output format. Valid options are: json, yaml, csv, junit-xml, html, sonarqube, golint or text (default "text")
  -include string
        Comma separated list of rules IDs to include. (see rule list)
  -log string
        Log messages to file rather than stderr
  -no-fail
        Do not fail the scanning, even if issues were found
  -nosec
        Ignores #nosec comments when set
  -nosec-tag string
        Set an alternative string for #nosec. Some examples: #dontanalyze, #falsepositive
  -out string
        Set output file for results
  -quiet
        Only show output when errors are found
  -severity string
        Filter out the issues with a lower severity than the given value. Valid options are: low, medium, high (default "low")
  -sort
        Sort issues by severity (default true)
  -tags string
        Comma separated list of build tags
  -tests
        Scan tests files
  -version
        Print version and quit with exit code 0


RULES:

        G101: Look for hardcoded credentials
        G102: Bind to all interfaces
        G103: Audit the use of unsafe block
        G104: Audit errors not checked
        G106: Audit the use of ssh.InsecureIgnoreHostKey function
        G107: Url provided to HTTP request as taint input
        G108: Profiling endpoint is automatically exposed
        G109: Converting strconv.Atoi result to int32/int16
        G110: Detect io.Copy instead of io.CopyN when decompression
        G201: SQL query construction using format string
        G202: SQL query construction using string concatenation
        G203: Use of unescaped data in HTML templates
        G204: Audit use of command execution
        G301: Poor file permissions used when creating a directory
        G302: Poor file permissions used when creation file or using chmod
        G303: Creating tempfile using a predictable path
        G304: File path provided as taint input
        G305: File path traversal when extracting zip archive
        G306: Poor file permissions used when writing to a file
        G307: Unsafe defer call of a method returning an error
        G401: Detect the usage of DES, RC4, MD5 or SHA1
        G402: Look for bad TLS connection settings
        G403: Ensure minimum RSA key length of 2048 bits
        G404: Insecure random number source (rand)
        G501: Import blocklist: crypto/md5
        G502: Import blocklist: crypto/des
        G503: Import blocklist: crypto/rc4
        G504: Import blocklist: net/http/cgi
        G505: Import blocklist: crypto/sha1
        G601: Implicit memory aliasing in RangeStmt
```
Run the Scanner
----------

We can perform static analysis on golang code using the following command.

```
gosec ./...
```
output
```
[gosec] 2020/09/23 10:59:00 Including rules: default
[gosec] 2020/09/23 10:59:00 Excluding rules: default
[gosec] 2020/09/23 10:59:00 Import directory: /webapp/vulnerability/idor
[gosec] 2020/09/23 10:59:01 Checking package: idor
[gosec] 2020/09/23 10:59:01 Checking file: /webapp/vulnerability/idor/function.go
[gosec] 2020/09/23 10:59:01 Checking file: /webapp/vulnerability/idor/idor.go
[gosec] 2020/09/23 10:59:01 Import directory: /webapp/vulnerability/xss
[gosec] 2020/09/23 10:59:01 Checking package: xss
[gosec] 2020/09/23 10:59:01 Checking file: /webapp/vulnerability/xss/function.go
[gosec] 2020/09/23 10:59:01 Checking file: /webapp/vulnerability/xss/xss.go
[gosec] 2020/09/23 10:59:01 Import directory: /webapp
[gosec] 2020/09/23 10:59:01 Checking package: main
[gosec] 2020/09/23 10:59:01 Checking file: /webapp/app.go
[gosec] 2020/09/23 10:59:01 Import directory: /webapp/util
[gosec] 2020/09/23 10:59:01 Checking package: util
[gosec] 2020/09/23 10:59:01 Checking file: /webapp/util/cookie.go
[gosec] 2020/09/23 10:59:01 Checking file: /webapp/util/http.go
[gosec] 2020/09/23 10:59:01 Checking file: /webapp/util/template.go
[gosec] 2020/09/23 10:59:01 Import directory: /webapp/util/database
[gosec] 2020/09/23 10:59:02 Checking package: database
[gosec] 2020/09/23 10:59:02 Checking file: /webapp/util/database/database.go
[gosec] 2020/09/23 10:59:02 Import directory: /webapp/setup
[gosec] 2020/09/23 10:59:02 Checking package: setup
[gosec] 2020/09/23 10:59:02 Checking file: /webapp/setup/function.go
[gosec] 2020/09/23 10:59:02 Checking file: /webapp/setup/setup.go
[gosec] 2020/09/23 10:59:02 Import directory: /webapp/util/config
[gosec] 2020/09/23 10:59:02 Checking package: config
[gosec] 2020/09/23 10:59:02 Checking file: /webapp/util/config/config.go
[gosec] 2020/09/23 10:59:02 Import directory: /webapp/vulnerability/csa
[gosec] 2020/09/23 10:59:03 Checking package: csa
[gosec] 2020/09/23 10:59:03 Checking file: /webapp/vulnerability/csa/csa.go
[gosec] 2020/09/23 10:59:03 Import directory: /webapp/vulnerability/xxe
[gosec] 2020/09/23 10:59:03 Checking package: xxe
[gosec] 2020/09/23 10:59:03 Checking file: /webapp/vulnerability/xxe/xxe.go
[gosec] 2020/09/23 10:59:03 Import directory: /webapp/user/session
[gosec] 2020/09/23 10:59:03 Checking package: session
[gosec] 2020/09/23 10:59:03 Checking file: /webapp/user/session/session.go
[gosec] 2020/09/23 10:59:03 Import directory: /webapp/util/middleware
[gosec] 2020/09/23 10:59:03 Checking package: middleware
[gosec] 2020/09/23 10:59:03 Checking file: /webapp/util/middleware/middleware.go
[gosec] 2020/09/23 10:59:03 Import directory: /webapp/vulnerability/sqli
[gosec] 2020/09/23 10:59:03 Checking package: sqli
[gosec] 2020/09/23 10:59:03 Checking file: /webapp/vulnerability/sqli/function.go
[gosec] 2020/09/23 10:59:03 Checking file: /webapp/vulnerability/sqli/sqli.go
[gosec] 2020/09/23 10:59:03 Import directory: /webapp/setting
[gosec] 2020/09/23 10:59:04 Checking package: setting
[gosec] 2020/09/23 10:59:04 Checking file: /webapp/setting/setting.go
[gosec] 2020/09/23 10:59:04 Import directory: /webapp/user
[gosec] 2020/09/23 10:59:04 Checking package: user
[gosec] 2020/09/23 10:59:04 Checking file: /webapp/user/user.go
Results:


[/webapp/util/template.go:45] - G203 (CWE-79): this method will not auto-escape HTML. Verify data is well formed. (Confidence: LOW, Severity: MEDIUM)
    44: func ToHTML(text string)template.HTML{
  > 45:         return template.HTML(text)
    46: }



[/webapp/user/user.go:160] - G401 (CWE-326): Use of weak cryptographic primitive (Confidence: HIGH, Severity: MEDIUM)
    159: func Md5Sum(text string) string {
  > 160:        hasher := md5.New()
    161:        hasher.Write([]byte(text))



[/webapp/user/user.go:8] - G501 (CWE-327): Blocklisted import crypto/md5: weak cryptographic primitive (Confidence: HIGH, Severity: MEDIUM)
    7:  "strconv"
  > 8:  "crypto/md5"
    9:  "database/sql"



[/webapp/vulnerability/sqli/function.go:37-40] - G201 (CWE-89): SQL string formatting (Confidence: HIGH, Severity: MEDIUM)
    36:
  > 37:         getProfileSql := fmt.Sprintf(`SELECT p.user_id, p.full_name, p.city, p.phone_number
  > 38:                                                                 FROM Profile as p,Users as u
  > 39:                                                                 where p.user_id = u.id
  > 40:                                                                 and u.id=%s`, uid) //here is the vulnerable query
    41:         rows, err := DB.Query(getProfileSql)


[...SNIP...]


[/webapp/vulnerability/idor/idor.go:42] - G104 (CWE-703): Errors unhandled. (Confidence: HIGH, Severity: LOW)
    41:         p := NewProfile()
  > 42:         p.GetData(sid)
    43:



[/webapp/user/user.go:161] - G104 (CWE-703): Errors unhandled. (Confidence: HIGH, Severity: LOW)
    160:        hasher := md5.New()
  > 161:        hasher.Write([]byte(text))
    162:        return hex.EncodeToString(hasher.Sum(nil))



Summary:
   Files: 20
   Lines: 1573
   Nosec: 0
  Issues: 23
```

As you can see, we found 23 issues and there were many false positives. We can reduce the bloat and false positives by using custom rules, proper configurations and by using arguments such as –severity high.

```
gosec -exclude=G104 ./...
```
The above command will reduce the bloat but does it also removes real issues?

Exercise
---------

1. Use appropriate gosec options to reduce false positives
2. Ensure you follow the DevSecOps Gospel and best practices
3. Think how you would embed this tool in CI pipeline? and under which build stage?


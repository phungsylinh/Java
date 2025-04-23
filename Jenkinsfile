#!groovy

standardBuild {
    environment = 'golang:1.20'
    mainScript = '''
go version
go build -v hello.go
'''
    postScript = '''
ls -la
./hello
'''
}

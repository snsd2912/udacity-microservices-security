## Evaluating Docker with CIS Benchmark and Docker-bench

### Build Image

```
docker build . -t opensuse/leap:latest -m 256mb --no-cache=true
```

### Install Docker-bench

Clone the Docker-bench repository from GitHub:
```
git clone https://github.com/aquasecurity/docker-bench.git
cd  /docker-bench 
go build -o docker-bench
```

### Analyze Docker

```
./docker-bench --include-test-output > docker-bench.txt 
```
Concatenate the docker-bench.txt file and look for the lines where there is a failure:
```
cat docker-bench.txt | grep FAIL
```
This command returns the checks that failed. In the next demo, we will look at these checks more closely, pick one of the failed checks, harden that check, then rerun Docker-bench to show that the failed check has been fixed.








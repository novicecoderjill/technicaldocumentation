# Installing Hadoop over Ubuntu WSL

Date: March 9, 2024

## Prerequisite
1. Ubuntu installed on Windows machine
   

## Update system

1. Open your Ubuntu terminal

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install openssh-server
```

## Check Java Installation

```bash
sudo apt-get install openjdk-8-jdk
java -version
```

![WindowsTerminal_wWsqbhyUCt](https://github.com/novicecoderjill/technicaldocumentation/assets/121611766/4737d295-afc0-4857-9088-167707bb0e4d)

## Install Hadoop  tar.gz via terminal

[Apache Download Mirrors](https://www.apache.org/dyn/closer.cgi/hadoop/common/hadoop-2.10.2/hadoop-2.10.2.tar.gz)

```bash
wget https://dlcdn.apache.org/hadoop/common/hadoop-2.10.2/hadoop-2.10.2.tar.gz

```

```bash
tar -xzvf hadoop-2.10.2.tar.gz
```

**Important to note: Update the line according to the downloaded version of hadoop**

```bash
sudo mv hadoop-2.10.2 /home/<USER>/hadoop/
```

![WindowsTerminal_WmtohuQHYF](https://github.com/novicecoderjill/technicaldocumentation/assets/121611766/cf5e9388-650a-442c-befe-949e54380403)

## Configuring Hadoop Java Home

```bash
readlink -f /usr/bin/java | sed "s:bin/java::"
```

The path to Java, /usr/bin/java is a symlink to /etc/alternatives/java, which is in turn a symlink to default Java binary. We will use readlink with the -f flag to follow every symlink in every part of the path, recursively. Then, we'll use sed to trim bin/java from the output to give us the correct value for JAVA_HOME.

![WindowsTerminal_0Tu5U02SsZ](https://github.com/novicecoderjill/technicaldocumentation/assets/121611766/95c74f58-5cd8-43fa-96ca-67cd310a6c7e)

```bash
sudo nano /home/<USER>/hadoop/etc/hadoop/hadoop-env.sh
```

In the nano, update JAVA_HOME

```bash
# The java implementation to use.
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre
```

![WindowsTerminal_pqzzjkZsbq](https://github.com/novicecoderjill/technicaldocumentation/assets/121611766/508b9e9a-46f9-4374-8c55-62eb3266e0d4)



## Run Hadoop

```bash
/home/<USER>/hadoop/bin/hadoop
```

![WindowsTerminal_W4ABnqmej7](https://github.com/novicecoderjill/technicaldocumentation/assets/121611766/bc8d2e19-eea6-4598-874e-e07ebdf5e0d4)

```bash
mkdir ~/input
```

```bash
cp /home/<USER>/hadoop/etc/hadoop/*.xml ~/input
```

```bash
/home/<USER>/hadoop/bin/hadoop jar
```

![WindowsTerminal_eXHrcGkdsq](https://github.com/novicecoderjill/technicaldocumentation/assets/121611766/445605e9-da82-4f2f-ad70-899d9b3c877f)


To check xml files pasted to `/input`

![WindowsTerminal_qXyrdmQjwo](https://github.com/novicecoderjill/technicaldocumentation/assets/121611766/c09d3d55-93c1-4137-ae4b-fd44d444cd21)


```bash
cd /home/<USER>/hadoop/share/hadoop/mapreduce
```

```bash
/home/<USER>/hadoop/bin/hadoop jar /home/<USER>/hadoop/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.10.2.jar grep ~/input ~/grep_example 'principal[.]*'
```

![WindowsTerminal_ENROKRs4ZJ](https://github.com/novicecoderjill/technicaldocumentation/assets/121611766/e8e4d8c7-a6c4-48c3-817c-ba607f1adb48)


## Final outcome

```bash
cat ~/grep_example/*
```

![WindowsTerminal_RMIDCkglv3](https://github.com/novicecoderjill/technicaldocumentation/assets/121611766/7c585a3c-533a-40ca-b387-ba40ce2a67e5)

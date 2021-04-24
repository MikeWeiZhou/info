# P2501: Setup WSL2 GUI


## Main Setup
1. Install VcXSrv on Windows host
2. Add to ~/.bashrc:
```
export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2; exit;}'):0.0
export LIBGL_ALWAYS_INDIRECT=1
sudo /etc/init.d/dbus start &> /dev/nulll
```


## VSCode Devcontainer
1. Add to devcontainer.json:
```
"runArgs": {
  "--net=host",
  "--gpus=all"
},
"containerEnv": {
  "DISPLAY": "172.31.240.1:0.0" // IP address of WSL
}
```
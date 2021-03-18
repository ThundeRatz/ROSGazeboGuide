## **Como rodar Gazebo + RVIZ e Windows 10 usando WSL2**
Após a instalação, é necessario instalar uma extensão para reproduzir o Gazebo e Rviz
- Baixar:
https://sourceforge.net/projects/vcxsrv/

Após baixar a extensão

- Execute o Xlaunch
Na aba de configuração de display(select display settings):
- Deixe "Multiple windows" selecionado
- Deixe display number = 0
Na aba de seleção de como iniciar o cliente(select how to start clients):
- Selecione "Start no client"
Na aba de configurações extras(extra settings):
- Deixe selecionado "Clipboard", "Primary Selection" e "Disable acess control"
Após isso é só finalizar a configuração

- Digite no terminal do ubuntu do WSL:
```
export GAZEBO_IP=127.0.0.1
export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0 
export LIBGL_ALWAYS_INDIRECT=0
```
Depois disso, toda vez que o gazebo for executado no ubuntu, uma aba será aberta automaticamente
 
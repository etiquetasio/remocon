## Bem Vindo cliente da etiquetas.io
![remocon-logo](https://user-images.githubusercontent.com/43131904/62931121-ba7ffd80-bdf8-11e9-9e5e-4a0e41450247.png)

### Descrição

remocon é um server de API capaz de executar comandos CLI com um usuário registrado no sistema linux de forma remota através de uma Call API REST.
Você pode restringir os comandos que o usuário pode executar através do Serviço API.

### Escopo da Aplicação
1. *Run Docker remotamente (Linux com Docker)*
2. *One-time code execution (per-user execution)*
3. *Suporta qualquer comando Linux*

### License
MIT

### Requerido o pacote
python2.7
(Official: rpm version supports centos7 and redhat7 versions)

remocon install
```markdown
yum remocon install
# yum install https://github.com/etiquetasio/remocon/raw/master/remocon-1.0.0-1.el7.x86_64.rpm -y

remocon Preferences
# vi /etc/remocon.conf
`[MAIN]
api_host = 0.0.0.0 -> Setar o IP do Serviço
api_port = 5000 -> Setar a porta para o serviço`

remocon start
# systemctl start remocon
```
Agora crie a conta do usuário para que ele rode comandos no Linux
```markdown
Criar usuário
# useradd testman

Gerar Senha
# passwd testman
```
Usando o remocon
```markdown
Request api key para o usuário gerado
# curl -X POST http://192.168.0.222:5000/user/register -H "Content-Type:application/json" -d '{"user":"testman"}'
`{
    "message": [
        "1004",
        "1005",
        "EMghWAZxHl"
    ],
    "status": "success"
}`

How to run the command
# curl -X POST http://192.168.0.222:5000/queue -H "Content-Type:application/json" -d '{"execcmd":"touch finished","user":"testman","key":"EMghWAZxHl"}
```
## Suporte e Contato
suporte@etiquetas.io
https://etiquetas.io

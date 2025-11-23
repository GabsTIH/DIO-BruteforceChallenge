# DIO-BruteforceChallenge
Desafio proposto pela DIO para testar conhecimentos à respeito do Bruteforce e das ferramentas do Kali LInux

## Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux nos protocolos de rede FTP (transferência de arquivos), HTTP (web) e SMB (compartilhamento de recursos).
### CONFIGURAÇÕES INICIAIS

1º - Instalar o Kali Linux e o Metasploitable no Virtual Box <br>
<sup>(no meu caso, estarei utilizando o meu linux mint ao invés do kali linux, mas o recomendado é criar uma máquina virtual com o Kali, pois o mesmo já vem com todas as ferramentas que precisa!)</sup>

<placeholder>

2º - Inicie os dois e faça um snapshot no metasploitable para caso ocorra uma falha ou um comprometimento da máquina, você pode recuperar a partir daquele ponto. Para isso, vá para a guia "MÁQUINA" do virtualbox com o metasploitable aberto, clique em "Criar Snapshot", adicione um nome e uma descrição para a sua snapshop, e clique em ok.

<p align="left">
    <img src="images/print1.png" alt="Snapshot" width="400">
</p>


3º - Acessar o metasploitable utilizando o login padrão: msfadmin, e senha: msfadmin

<p align="left">
    <img src="images/print2.png" alt="Login" width="400">
</p>

4º - Digite o comando "ip a" no metasploitable e anote o ip da máquina que estará na linha inet addr. Este será o ip utilizado para os testes do Kali.

<p align="left">
    <img src="images/print3.png" alt="IP A" width="400">
</p>

5º - Digite o comando "ping -c 3 192.168.XX.XXX" para testar se nossa máquina consegue se comunicar com o ip alvo
Se houve resposta, significa que nossas duas máquinas estão se comunicando sem problemas.

<p align="left">
    <img src="images/print4.png" alt="Ping" width="400">
</p>

<br>

## Simulando um ataque a um servidor FTP para verificar falhas de segurança em um cenário de auditoria.

1º - Faremos uma enumeração para descobrir quais portas estão disponíveis no ip alvo com suspeita de vulnerabilidade.
<br>
O comando que utilizaremos será o seguinte: nmap -sV -p 21,22,80,445,139 192.168.XX.XXX
Se a porta ftp estiver aberta tentaremos conectá-la diretamente.
<p align="left">
    <img src="images/print5A.png" alt="NMap" width="400">
</p>

2º - Ao confirmar as portas, agora tentaremos conectar diretamente ao FTP, com a finalidade de verificar se o mesmo recebe nossa conexão
O comando em questão será: ftp 192.168.XX.XXX
<p align="left">
    <img src="images/print6A.png" alt="FTP failed" width="400">
</p>
Ao se conectar, ele vai pedir para que digitemos um login e uma senha. Como ainda não sabemos ambos, precisaremos fazer um ataque de Brute Force utilizando a ferramenta Medusa para tentar descobrir o login e a senha. Antes de tudo, criaremos duas listas: uma com possíveis nomes de usuários e outra com senhas comuns.

### Criando nomes de usuários e senhas comuns (wordlists) em diferentes arquivos e realizando o ataque

1º - Utilizaremos dois comandos para criar e salvar no Kali Linux arquivos de texto com possíveis nomes de usuários e senhas comuns.
Para usuários utilizaremos: echo -e "user\nmsfadmin\nadmin\nroot" > users.txt
E para senhas utilizaremos: echo -e "123456\npassword\nqwerty\nmsfadmin" > pass.txt

<p align="left">
    <img src="images/print7A.png" alt="Wordlists" width="400">
</p>

2º - Agora partiremos pro ataque com a ferramenta Medusa
Utilizaremos o comando: medusa -h 192.168.XX.XXX -U users.txt -P pass.txt -M ftp -t6

<p align="left">
    <img src="images/print8.png" alt="MedusaAttack1" width="400">
</p>

Como resultado do ataque, foram encontrados o login msfadmin e a senha msfadmin como credenciais válidas. Significando que conseguiremos acessar o sistema via FTP com essas credenciais.

3º - Novamente, entraremos no FTP, confirmando se as credenciais obtidas de fato estão corretas


<p align="left">
    <img src="images/print9.png" alt="MedusaAttackSucessful1" width="400">
</p>


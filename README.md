# 🔐 Ubuntu UFW — Firewall & Security Hardening

## 📌 Sobre o projeto

Este projeto documenta um laboratório prático de configuração e gerenciamento de firewall no Ubuntu Linux utilizando o **UFW (Uncomplicated Firewall)**.

O objetivo foi aplicar conceitos fundamentais de Segurança da Informação, incluindo controle de acesso à rede, princípio do menor privilégio, redução da superfície de ataque e auditoria de configurações.

## 🖥️ Ambiente utilizado

- **Sistema operacional:** Ubuntu Linux
- **Virtualização:** Oracle VirtualBox
- **Ferramentas:** UFW, systemctl, ss
- **Interface:** Terminal Linux
- **Ambiente:** Máquina virtual de laboratório

## 🛡️ 1. Verificação inicial

Inicialmente, foi verificado o estado do firewall:

```bash
sudo ufw status verbose
```

**Resultado:** `Status: inactive`

O UFW estava instalado, porém desativado.

## 🔒 2. Configuração das políticas de segurança

Foi aplicada uma política padrão de bloqueio para conexões de entrada:

```bash
sudo ufw default deny incoming
```

Em seguida, foi configurada a permissão para conexões de saída:

```bash
sudo ufw default allow outgoing
```

Essa configuração utiliza o conceito de **Default Deny**, restringindo novas conexões de entrada que não estejam explicitamente autorizadas.

## ⚙️ 3. Ativação do firewall

```bash
sudo ufw enable
```

**Resultado:** `Firewall is active and enabled on system startup`

O firewall foi ativado e configurado para iniciar automaticamente com o sistema.

## 🔎 4. Identificação de serviços de rede

```bash
sudo ss -tulnp
```

Foram identificados serviços relacionados a DNS, sincronização de horário, descoberta de dispositivos e impressão.

Essa análise permitiu observar sockets de rede e identificar serviços em execução.

## 🌐 5. Criação de regra TCP

Foi criada uma regra temporária permitindo conexões de entrada na porta 8080/TCP:

```bash
sudo ufw allow 8080/tcp
```

A configuração gerou regras para IPv4 e IPv6.

Para verificar as regras:

```bash
sudo ufw status numbered
```

**Resultado:** regras `ALLOW IN` para a porta 8080/TCP.

## 🧹 6. Remoção da regra

Após a análise, a regra temporária foi removida:

```bash
sudo ufw delete allow 8080/tcp
```

A remoção foi confirmada para IPv4 e IPv6.

Essa etapa demonstra a importância de não manter permissões de rede desnecessárias.

## ✅ 7. Auditoria final

```bash
sudo ufw status verbose
```

**Configuração final:**

- Firewall: ativo
- Política de entrada: deny
- Política de saída: allow
- Logs: on (low)
- Encaminhamento: disabled
- Regra temporária TCP 8080: removida

## 📸 Evidências

A captura abaixo mostra uma etapa da configuração realizada no laboratório.

![Captura do laboratório UFW](Captura%20de%20tela%202026-10-16%20111934.png)

## 🧠 Conceitos aplicados

- Network Security
- Firewall Configuration
- Security Hardening
- Default Deny
- Principle of Least Privilege
- TCP/IP
- IPv4 e IPv6
- Security Auditing

## 📚 Conclusão

O laboratório permitiu compreender o funcionamento básico do UFW, configurar políticas de tráfego, identificar serviços de rede e gerenciar regras de firewall.

A atividade reforçou conhecimentos de administração Linux e fundamentos de Cibersegurança por meio de uma implementação prática em ambiente virtualizado.

**Observação:** o laboratório validou a configuração das regras do UFW. Testes de conectividade externa e filtragem de pacotes não fizeram parte desta etapa.

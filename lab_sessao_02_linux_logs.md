# SKODJI DIGITAL — MOD.XX.YY.ZZ

# Laboratório — Sessão 2
## Auditoria de Sistemas Linux e Análise Avançada de Logs

| Informação | Detalhes |
|------------|----------|
| **Curso** | Reskilling |
| **Módulo** | Linux e Cibersegurança |
| **Objetivo de Aprendizagem** | OA2 – Avaliar |
| **Duração da Prática Guiada** | 19:15 – 20:50 |
| **Formador** | Péricles Borges |

---

# Contexto

Um servidor da infraestrutura foi alvo de conexões anómalas. Atuará como analista forense para determinar a origem e o sucesso do ataque, com base na análise de logs de autenticação.

---

# Ambiente Virtual

- **TryHackMe – Intro to Logs (Gratuito)**  
  https://tryhackme.com/room/introtologs

- **TryHackMe – Linux Server Forensics (Gratuito)**  
  https://tryhackme.com/room/linuxserverforensics

---

# Tarefas a Executar

- [ ] Aceder ao laboratório **Intro to Logs** para compreender a mecânica dos registos do sistema.

- [ ] No laboratório **Linux Server Forensics**, navegar até à diretoria de logs do servidor comprometido.

```bash
cd /var/log/
```

---

- [ ] Isolar tentativas falhadas de login.

```bash
grep "Failed password" auth.log
```

---

- [ ] Extrair e contar quais os IPs que mais tentaram autenticar-se no sistema.

```bash
grep "Failed password" auth.log | awk '{print $11}' | sort | uniq -c | sort -nr
```

---

- [ ] Identificar se o atacante obteve sucesso.

```bash
grep -E "Accepted password|Accepted publickey" auth.log
```

---

# Critérios de Entrega

Documente os seguintes pontos diretamente no seu portfólio.

## 1. IP do atacante

```text
10.129.176.64
```

---

## 2. Hora exata do comprometimento (Timestamp)

```text
Jul 17 14:08:09
```

---

## 3. Utilizador afetado

```text
fred
```

---

## 4. Linha temporal do ataque

| Hora | Evento |
|------|--------|
| **14:07:51** | Tentativa falhada. O atacante tenta autenticar-se via SSH com o utilizador **fred** a partir do IP **10.129.176.64** (porta **57072**), resultando em **Failed password**. |
| **14:08:09** | Sucesso (Comprometimento). Apenas **18 segundos** após a falha, o atacante consegue autenticar-se com sucesso (**Accepted password**) mantendo a mesma sessão/porta de origem. |
| **14:47:36** | Novo acesso. O mesmo atacante estabelece uma nova ligação SSH bem-sucedida para o utilizador **fred**, utilizando a porta de origem **44460**. |

---

# Checklist de Submissão (Portfólio GitHub)

- [ ] Criar ou atualizar o ficheiro **sessao-02/README.md**.
- [ ] Incluir os excertos relevantes extraídos dos logs analisados.
- [ ] Efetuar o **commit** e o **push** das alterações para o repositório remoto.

---

> **Percurso Reskilling — Linux e Cibersegurança**  
> **SKODJI DIGITAL**  
> Documento de Apoio ao Aluno
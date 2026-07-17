

Laboratório — Sessão 2
Auditoria de Sistemas Linux e Análise Avançada de Logs

Curso: Reskilling  |  Módulo: Linux e Cibersegurança





Ambiente Virtual

TryHackMe Intro to Logs (Gratuito): https://tryhackme.com/room/introtologs

TryHackMe Linux Server Forensics (Gratuito): https://tryhackme.com/room/linuxserverforensics







Tarefas a Executar

☐  Aceder ao laboratório Intro to Logs para compreender a mecânica dos registos do sistema.

☐  No laboratório Linux Server Forensics, navegar até à diretoria de logs do servidor comprometido:











☐  Isolar tentativas falhadas de login:









☐  Extrair e contar quais os IPs que mais tentaram autenticar-se no sistema:

















☐  Identificar se o atacante obteve sucesso:



Critérios de Entrega

Deve documentar os seguintes pontos diretamente no seu portfólio:

O IP do atacante identificado.

[IP: 10.129.176.64]

A hora exata do comprometimento (timestamp).

[Timestamp: Jul 17 14:08:09]



O utilizador afetado.

[Utilizador: fred]



Uma breve linha temporal do ataque (tentativas falhadas → sucesso).

[14:07:51 — Tentativa Falhada: O atacante tenta autenticar-se via SSH com o utilizador fred a partir do IP 10.129.176.64 (porta 57072), resultando em erro (Failed password).

 14:08:09 — Sucesso (Comprometimento): Apenas 18 segundos após a falha, o atacante consegue acertar na palavra-passe e obtém acesso bem-sucedido ao sistema (Accepted password) mantendo a mesma sessão/porta de origem.

 14:47:36 — Novo Acesso: O mesmo atacante estabelece uma nova ligação SSH bem-sucedida para o utilizador fred, desta vez utilizando a porta de origem 44460]



Checklist de Submissão (Portfólio GitHub)

☐  Criar ou atualizar o ficheiro sessao-02/README.md (formato Markdown) com todos os resultados documentados.

☐  Incluir os excertos relevantes extraídos dos logs analisados.

☐  Efetuar o commit e o push das alterações para o repositório remoto do portfólio.

Percurso Reskilling — Linux e Cibersegurança  |  SKODJI DIGITAL  |  Documento de Apoio ao Aluno


• Objetivo de Aprendizagem: OA3. Aplicar

• Duração da prática guiada: 19:15 – 20:50

• Formador: Péricles Borges

• Contexto: Configuração de uma política defensiva estrita para impedir acessos não autorizados a serviços críticos do servidor, combinando UFW e iptables.

1. Ambiente Virtual

KillerCoda Ubuntu Playground: https://killercoda.com/playgrounds/scenario/ubuntu

TryHackMe Network Security Essentials (Gratuito): https://tryhackme.com/room/networksecurityessentials

2. Tarefas a Executar

 

☐ Verificar o estado atual do UFW:





☐ Alterar as políticas padrão - bloquear entrada, permitir saída:





☐ Criar uma regra específica para permitir acesso SSH apenas na porta padrão:





☐ Simular o bloqueio de um IP malicioso fictício na chain INPUT do iptables:



☐ Guardar o estado permanente/persistente do iptables:



3. Critérios de Entrega

Devem ser documentados os seguintes elementos no seu portfólio individual:

Captura de ecrã ou output de texto das regras UFW ativas: sudo ufw status verbose



Listagem completa de regras do iptables: sudo iptables -L –v





Breve explicação da política aplicada (o que está bloqueado e qual a sua justificação lógica/técnica).

A estratégia defensiva delineada para este servidor combina o uso do UFW (para uma gestão simplificada de políticas globais e portos) e do iptables (para filtragem mais granular e imediata a nível de rede). A lógica técnica baseia-se nos seguintes pilares:

Princípio do Privilégio Mínimo (Default Deny): Com a definição de ufw default deny incoming, estabelece-se uma postura de segurança defensiva estrita. Qualquer tentativa de ligação externa ao servidor é implicitamente bloqueada, a menos que exista uma regra explícita que a autorize. Isto reduz drasticamente a superfície de ataque exposta a ameaças e varrimentos de portas automáticos.

Manutenção da Operabilidade Outbound: A política ufw default allow outgoing garante que o servidor pode continuar a comunicar livremente com o exterior para tarefas essenciais, tais como atualizações de pacotes do sistema (apt update) e resolução de nomes (DNS).

Acesso Remoto Controlado: A abertura explícita da porta 22/tcp (ufw allow 22/tcp) garante a persistência do acesso administrativo remoto via SSH, impedindo que o administrador perca a ligação à máquina ao aplicar a política restritiva de entrada.

Bloqueio de Vetores de Ataque Identificados (iptables): Através da chain INPUT do Netfilter via iptables, aplicou-se um bloqueio imediato e definitivo (DROP) a origens específicas:

IP Externo Fictício (203.0.113.50): Simula a mitigação de um atacante ativo ou endereço IP identificado em relatórios de Threat Intelligence, descartando os pacotes na camada de rede antes que cheguem a qualquer serviço.

IP Local/Loopback (10.128.181.214): Bloqueia o tráfego vindo do próprio IP atribuído à interface de rede do servidor, uma técnica útil em laboratório para simular o isolamento de tráfego interno ou mitigar comportamentos anómalos de spoofing.

4. Checklist de Submissão (Portfólio GitHub)

☐  Criar ou atualizar o diretório e ficheiro sessao-03/README.md com os resultados devidamente estruturados.

☐  Incluir explicitamente os outputs dos comandos 'ufw status verbose' e 'iptables -L -v'.

☐  Executar o commit e push das alterações para o repositório remoto do seu portfólio no GitHub.
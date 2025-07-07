# Monitoramento de Endpoint com Wazuh e Sysmon

<b>Descrição</b>

Esse laboratório foi realizado dentro do ambiente TryHackMe e tem como objetivo mostrar algumas funcionalidades da ferramenta Wazuh e Sysmon. O cenário consiste em realizar investigações nos logs de endpoint da empresa fictícia, visando a detecção de atividades fora do normal.

<b>Ferramentas</b>

<b>Wazuh</b> é uma plataforma open source de solução de segurança para ativos digitais e aprimoramento da postura de segurança cibernética de empresas. Ela oferece monitoramento por meio de seus recursos de Gerenciamento de Informações e Eventos de Segurança(SIEM) e na proteção com a Detecção e Resposta Estendidas(XDR). Seus casos de uso são:

- Avaliação de configuração
- Detecção de malware
- Monitoramento de integridade de arquivos
- Caça à Ameaça
- Análise de dados de log
- Detecção de Vulnerabilidade
- Resposta a incidentes
- Conformidade regulatória
- Higiene de TI
- Segurança de Contêineres
- Gestão Postural
- Proteção de carga de trabalho

<b>Sysmon</b> ou Monitor do Sistema é um serviço e driver de dispositivo do sistema Windows que monitora e registra a atividade do sistema no log de eventos do Windows. Ele fornece informações detalhadas sobre criações de processos, conexões de rede e alterações na hora de criação dos arquivos. Ao coletar os eventos que ele gera usando a Coleção de Eventos do Windows ou agentes SIEM e analisá-los, você pode identificar atividades mal-intencionadas ou anômalas e entender como intrusos e malware operam em sua rede. O serviço é executado como um processo protegido, não permitindo assim uma ampla gama de interações no modo de usuário. O Sysmon inclui os seguintes recursos:

- Registra em log a criação do processo com linha de comando completa para processos atuais e pai.
- Regista o hash dos ficheiros de imagem do processo com SHA1 (a predefinição), MD5, SHA256 ou IMPHASH.
- Inclui um GUID de processo em eventos de criação de processo para permitir a correlação de eventos mesmo quando o Windows reutiliza IDs de processo.
- Inclui um GUID de sessão em cada evento para permitir a correlação de eventos na mesma sessão de logon.
- Registra em log o carregamento de drivers ou DLLs com suas assinaturas e hashes.
- Os logs são abertos para acesso bruto de leitura de discos e volumes.
- Detecta alterações na hora de criação do arquivo para reconhecer quando um arquivo foi realmente criado.
- Recarrega automaticamente a configuração se ela for alterada no Registro.
- Filtragem de regras para incluir ou excluir determinados eventos dinamicamente.
- Gera eventos desde o início do processo de inicialização para capturar atividades feitas até mesmo por malwares sofisticados no modo kernel.

<b>Cenário do Laboratório</b>

<a href='https://postimg.cc/7b9StyPG' target='_blank'><img src='https://i.postimg.cc/L6KvXHrT/ws1.jpg' border='0' alt='ws1'/></a>



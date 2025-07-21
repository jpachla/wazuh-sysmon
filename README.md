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

Iniciando os trabalhos neste laboratório, abrimos a VM e colocamos o IP indicado no browser do TryHackMe para acessarmos a interface Wazuh. Colocamos o login e senha e vamos até os eventos de segurança para ingerir os logs.

<a href="https://ibb.co/svZRymyj"><img src="https://i.ibb.co/hRS9D7Ds/ws2.jpg" alt="ws2" border="0"></a>

Vamos para o primeiro desafio prático...

<a href="https://ibb.co/1YPD1LJN"><img src="https://i.ibb.co/gbf5N3F8/ws3.jpg" alt="ws3" border="0"></a>

Ajustaremos a timeline conforme o dia e a hora do teste.

<a href="https://ibb.co/PZVwhW9p"><img src="https://i.ibb.co/kgPQ8D9n/ws4.jpg" alt="ws4" border="0"></a>

Pesquisamos por "localhost" já que o arquivo estava salvo no host local. A pesquisa resultou em 3 logs para verificarmos.

<a href="https://ibb.co/dwPgpfRq"><img src="https://i.ibb.co/VcgmCLsZ/ws5.jpg" alt="ws5" border="0"></a>

De imediato já observamos o alerta na descrição de execução de arquivo suspeito. Vamos abrir esse log e conferir.

<a href="https://ibb.co/9Qmwr06"><img src="https://i.ibb.co/B0H4CJb/ws6.jpg" alt="ws6" border="0"></a>

Ao abrirmos o log, notamos na linha de comando que foi executado um arquivo excel habilitado para macros(.xlsm). E esse arquivo em questão é a nossa primeira resposta.

<a href="https://ibb.co/G4LWTydT"><img src="https://i.ibb.co/Jw4vQVcQ/ws7.jpg" alt="ws7" border="0"></a>

<a href="https://ibb.co/fGd3dDJK"><img src="https://i.ibb.co/qFYHYJ64/ws8.jpg" alt="ws8" border="0"></a>

<a href="https://ibb.co/DHXk482v"><img src="https://i.ibb.co/W49FnPJM/ws9.jpg" alt="ws9" border="0"></a>

Essa segunda pergunta demandou um certo tempo para verificar nas pesquisas. Coloquei primeiro "schtask" mas não teve êxito. Então foi preciso colocar na busca "scheduler", para assim aparecer 10 resultados de logs. 

<a href="https://ibb.co/JRvTtcCD"><img src="https://i.ibb.co/Kj2gh5mT/ws10.jpg" alt="ws10" border="0"></a>

Então foi necessário investigar os 10 logs para achar o comando, e foi no comando pai (data.win.event.data.parent.CommandLine) que encontramos a resposta.

<a href="https://ibb.co/8gHWhM76"><img src="https://i.ibb.co/VYs7KVq2/ws12.jpg" alt="ws12" border="0"></a>

<a href="https://ibb.co/KjpxFGh1"><img src="https://i.ibb.co/rGR24t0W/ws13.jpg" alt="ws13" border="0"></a>

<a href="https://ibb.co/dwzXFC0W"><img src="https://i.ibb.co/HfkR6wDF/ws14.jpg" alt="ws14" border="0"></a>

A resposta para esta pergunta podemos encontrarmos na resposta anterior ao observarmos a linha de comando.

<a href="https://ibb.co/HLVm6HGp"><img src="https://i.ibb.co/LD84mZ9h/ws15.jpg" alt="ws15" border="0"></a>

<a href="https://ibb.co/fz8nVPCX"><img src="https://i.ibb.co/xtmfKRM2/ws16.jpg" alt="ws16" border="0"></a>

<a href="https://ibb.co/VYq22bWP"><img src="https://i.ibb.co/60WggGRf/ws17.jpg" alt="ws17" border="0"></a>

Ao analisarmos a linha de comando, iremos perceber que há uma string Base64, que nada mais é um esquema de codificação binário-texto em sequência caracteres string ASCII. Para decodificarmos essa string, utilizaremos a ferramenta web CyberChef que analisa e decodifica dados.

<a href="https://ibb.co/ynL7LxbY"><img src="https://i.ibb.co/Z6y7ybkY/ws18.jpg" alt="ws18" border="0"></a>

Colocamos a string Base64 e obteremos a nossa resposta.

<a href="https://ibb.co/mVDC2cR5"><img src="https://i.ibb.co/7dYJZ1St/ws19.jpg" alt="ws19" border="0"></a>

<a href="https://ibb.co/Pvfn1cyH"><img src="https://i.ibb.co/9kCLyb05/ws20.jpg" alt="ws20" border="0"></a>

<a href="https://ibb.co/JRHcsqfG"><img src="https://i.ibb.co/QFMJKk2T/ws21.jpg" alt="ws21" border="0"></a>















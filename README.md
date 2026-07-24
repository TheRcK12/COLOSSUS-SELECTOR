# COLOSSUS-SELECTOR
1. Objetivos
   
1.1 Objetivo Geral
O principal objetivo do projeto COLOSSUS consiste no desenvolvimento de uma plataforma desktop de alto desempenho destinada ao processamento inteligente de grandes volumes de dados comerciais, automatizando integralmente a preparação de bases utilizadas em operações de telemarketing, cobrança, retenção, relacionamento e vendas.
O sistema foi concebido para eliminar processos manuais repetitivos, reduzir significativamente o tempo necessário para preparação de mailings e aumentar a confiabilidade das informações utilizadas pelas equipes comerciais.
Além da simples organização dos dados, o COLOSSUS busca estabelecer um novo padrão de processamento, onde diferentes fontes de informação possam ser integradas automaticamente em um único fluxo operacional, permitindo que milhões de registros sejam analisados em poucos minutos.
Outro objetivo importante consiste em fornecer aos gestores uma visão detalhada sobre todo o processamento realizado pelo sistema. Para isso, foram desenvolvidos dashboards, indicadores estatísticos, relatórios analíticos e mecanismos de diagnóstico que permitem acompanhar cada etapa da geração dos mailings.
O projeto também foi desenvolvido pensando em sua evolução contínua. Sua arquitetura modular possibilita que novos filtros, novas regras de negócio, novos relatórios e novas funcionalidades sejam incorporados futuramente sem comprometer a estabilidade do sistema.
Dessa maneira, o COLOSSUS deixa de ser apenas um software de processamento de dados e passa a atuar como uma plataforma de inteligência operacional, capaz de auxiliar diretamente na tomada de decisões estratégicas relacionadas às campanhas comerciais.

________________________________________

1.2 Objetivos Específicos

Para alcançar o objetivo geral proposto, foram definidos diversos objetivos específicos durante a fase de levantamento de requisitos.
O primeiro deles consiste na criação de um mecanismo universal de leitura de arquivos capaz de reconhecer automaticamente diferentes formatos de entrada, priorizando arquivos Parquet devido ao seu elevado desempenho, mantendo compatibilidade com planilhas Excel e arquivos CSV.
Outro objetivo fundamental foi desenvolver um sistema capaz de processar simultaneamente múltiplas bases comerciais distribuídas em diferentes diretórios, permitindo que grandes volumes de dados sejam consolidados automaticamente durante uma única execução.
Também foi estabelecida como prioridade a implementação de mecanismos inteligentes de validação capazes de identificar inconsistências presentes nos dados recebidos.

________________________________________

2. Proposta do Sistema
   
O COLOSSUS foi idealizado para atuar como o núcleo central de processamento de dados das operações comerciais.
Sua proposta consiste em substituir uma série de processos manuais, normalmente executados utilizando planilhas eletrônicas e pequenos scripts independentes, por um fluxo único, automatizado e altamente otimizado.
Antes do desenvolvimento do sistema, era comum que diferentes profissionais executassem etapas distintas da preparação dos mailings.
Inicialmente eram realizadas leituras individuais de cada base comercial.
Em seguida iniciava-se a padronização das colunas, alteração manual de nomes de campos, remoção de registros inválidos, eliminação de duplicidades, validação dos telefones, cruzamento com listas de bloqueio, conferência dos arquivos da URA, separação por estado, geração dos lotes e elaboração dos relatórios.
Todo esse procedimento poderia consumir diversas horas de trabalho, principalmente quando envolvia bases superiores a dez milhões de registros.
Além do elevado tempo de processamento, existia uma grande possibilidade de falhas humanas durante cada etapa da preparação.
O COLOSSUS foi desenvolvido justamente para eliminar esse problema.
Sua arquitetura organiza todo o processamento em um pipeline inteligente, onde cada etapa possui uma responsabilidade específica.

________________________________________

3. Planejamento do Projeto
   
O desenvolvimento do COLOSSUS foi conduzido seguindo uma metodologia de evolução contínua, onde cada nova funcionalidade foi incorporada de maneira incremental, permitindo que o sistema fosse constantemente validado durante sua construção. Diferentemente de projetos tradicionais, cuja implementação ocorre somente após a conclusão completa do planejamento, o COLOSSUS passou por sucessivas fases de aprimoramento, sempre priorizando estabilidade, desempenho e compatibilidade com versões anteriores.
Durante todo o desenvolvimento buscou-se construir uma arquitetura suficientemente flexível para suportar futuras expansões sem necessidade de reescrever grandes partes do sistema. Essa decisão permitiu que novas funcionalidades fossem incorporadas ao longo do tempo, acompanhando as necessidades operacionais identificadas durante a utilização prática do software.
O planejamento também considerou aspectos relacionados ao desempenho computacional. Desde as primeiras versões ficou evidente que o crescimento constante das bases comerciais exigiria uma arquitetura capaz de processar dezenas de milhões de registros utilizando recursos computacionais limitados. Dessa forma, diversas decisões arquitetônicas foram tomadas visando reduzir o consumo de memória RAM, aumentar a velocidade de leitura dos arquivos e minimizar o tempo total necessário para geração dos mailings.
Outro fator considerado durante o planejamento foi a facilidade de utilização. Embora o sistema execute operações extremamente complexas em seu núcleo, toda a interação do usuário deveria ocorrer de maneira simples e intuitiva. Por esse motivo, grande parte do esforço de desenvolvimento foi direcionada à construção de uma interface gráfica organizada, permitindo que operadores sem conhecimentos técnicos em programação pudessem utilizar todas as funcionalidades disponíveis.
A modularização do sistema também foi definida como um requisito estratégico. Em vez de concentrar toda a lógica em um único arquivo de código, optou-se por dividir o projeto em diversos módulos independentes, cada um responsável por uma etapa específica do processamento. Essa organização facilita futuras manutenções, reduz conflitos entre funcionalidades e torna o projeto significativamente mais escalável.
Além disso, o planejamento contemplou a adoção de tecnologias modernas voltadas ao processamento analítico de dados, substituindo soluções convencionais por ferramentas mais eficientes. A utilização do DuckDB como mecanismo principal de processamento, aliada ao uso de arquivos Parquet como formato preferencial de armazenamento, constitui um dos principais diferenciais técnicos do COLOSSUS.
Todas essas decisões foram tomadas considerando não apenas as necessidades atuais das operações comerciais, mas também o potencial crescimento do sistema nos próximos anos.

________________________________________

4. Concepção

A fase de concepção teve como principal objetivo compreender profundamente os problemas enfrentados pelas operações comerciais durante a preparação de mailings.
Inicialmente foram analisadas diversas rotinas executadas manualmente pelas equipes responsáveis pelo tratamento das bases de dados. Essa análise permitiu identificar gargalos operacionais que consumiam grande quantidade de tempo e estavam sujeitos a erros humanos.
Observou-se que a preparação de uma única campanha exigia a realização de inúmeras tarefas repetitivas, como leitura individual de diferentes arquivos, padronização de colunas, validação de documentos, organização de telefones, eliminação de registros duplicados, cruzamentos com listas de bloqueio e geração manual de relatórios.
Além disso, verificou-se que diferentes fornecedores utilizavam estruturas completamente distintas para armazenar informações semelhantes. Enquanto algumas bases apresentavam colunas padronizadas, outras utilizavam nomenclaturas diferentes para representar os mesmos dados, dificultando significativamente sua integração.
Outro problema identificado durante essa etapa foi o crescimento constante do volume de informações manipuladas pelas operações. Em muitos casos, uma única campanha podia envolver dezenas de milhões de registros distribuídos entre centenas de arquivos diferentes.
Ferramentas convencionais, como planilhas eletrônicas, apresentavam limitações severas de desempenho nessas situações, tornando inviável a continuidade do modelo de processamento utilizado anteriormente.
Com base nessas observações, definiu-se que o COLOSSUS deveria atuar como um sistema centralizador, responsável por automatizar todas as etapas envolvidas na preparação das bases comerciais.

________________________________________

4.1 Construção

A fase de construção corresponde ao período de implementação efetiva do sistema.
Durante essa etapa, cada módulo anteriormente especificado foi desenvolvido individualmente, sendo posteriormente integrado aos demais componentes da plataforma.
Inicialmente foram implementados os mecanismos responsáveis pela leitura dos arquivos de entrada.
Em seguida iniciou-se o desenvolvimento das rotinas de validação de dados, responsáveis pela identificação automática de inconsistências presentes nas bases comerciais.
Com o avanço do projeto foram incorporadas funcionalidades cada vez mais sofisticadas, incluindo mecanismos inteligentes de deduplicação, identificação automática de Unidade Federativa, correção de números telefônicos, integração com arquivos de viabilidade e cruzamentos com históricos da URA.
Uma das decisões mais importantes tomadas durante essa etapa foi a substituição gradual do processamento tradicional baseado exclusivamente em DataFrames por uma arquitetura híbrida utilizando DuckDB.
Essa mudança representou um marco importante na evolução do projeto, proporcionando ganhos significativos de desempenho durante praticamente todas as etapas do processamento.
Outro avanço relevante ocorreu com a implementação do sistema de cache inteligente.
Esse mecanismo permite que arquivos previamente processados não precisem ser lidos novamente em execuções futuras, reduzindo significativamente o tempo necessário para abertura do sistema e geração de novos mailings.
Durante a construção também foram desenvolvidos os módulos responsáveis pela geração automática de dashboards, relatórios estatísticos e diagnósticos operacionais, permitindo que os usuários acompanhem detalhadamente cada etapa do processamento.
Ao longo do desenvolvimento, todas as funcionalidades implementadas passaram por ciclos constantes de validação, garantindo estabilidade antes da incorporação definitiva ao sistema.


# Proposta
Você é um desenvolvedor de software em uma empresa de tecnologia renomada. Sua equipe foi encarregada de um projeto crítico: migrar uma aplicação web legado, que atualmente está hospedada em servidores locais, para a nuvem da AWS. A aplicação tem enfrentado sérios problemas de escalabilidade e disponibilidade, prejudicando a experiência dos usuários e a reputação da empresa. Sua missão é garantir que essa migração seja feita de forma suave, minimizando o tempo de inatividade e aproveitando ao máximo os benefícios que a nuvem pode oferecer.

Você começa sua jornada analisando a arquitetura atual da aplicação. Identifica pontos críticos que precisam ser abordados para garantir uma transição bem-sucedida. Sabendo que a AWS oferece uma vasta gama de serviços que podem resolver os problemas de escalabilidade e disponibilidade que sua aplicação enfrenta, mas precisa planejar cuidadosamente cada etapa do processo de migração.

Primeiro, você realiza uma auditoria completa da infraestrutura atual. Elencando quais são as dependências da aplicação e os pontos fracos que precisam ser abordados. Em seguida, você mapeia os serviços da AWS que serão necessários. Desde instâncias EC2 para hospedar os servidores até serviços de banco de dados gerenciados como o RDS.

Com o planejamento em mãos, você começa a migrar a aplicação para a AWS. Configura as instâncias EC2, transfere os dados para o RDS e implementa uma solução de balanceamento de carga para distribuir o tráfego de forma eficiente.

Durante o processo, você realiza testes extensivos para garantir que a aplicação funcione corretamente na nova infraestrutura e que a migração não cause interrupções significativas para os usuários.

Após a migração, você configura ferramentas de monitoramento como o CloudWatch para acompanhar o desempenho da aplicação e identificar quaisquer problemas em tempo real. Também configura auto-scaling para garantir que a aplicação possa lidar com picos de tráfego sem comprometer a performance.

Desafio:
1. Quais são as principais etapas que você seguiria no planejamento e execução da migração de uma aplicação legado para a AWS? Detalhe o processo de auditoria da infraestrutura atual, a seleção dos serviços AWS apropriados e a execução da migração.
2. Como você garantiria que a aplicação migre para a AWS sem causar interrupções significativas para os usuários? Descreva os métodos e ferramentas que utilizaria para testar a aplicação durante a migração e para minimizar o tempo de inatividade.
3. Quais benefícios específicos da nuvem AWS você espera aproveitar após a migração e como planeja otimizar o desempenho da aplicação na nova infraestrutura?

# Projeto

## 1. Quais são as principais etapas que você seguiria no planejamento e execução da migração de uma aplicação legado para a AWS? Detalhe o processo de auditoria da infraestrutura atual, a seleção dos serviços AWS apropriados e a execução da migração.

Pensando na estratégia de migração refatorando para o sistema legado, o primeiro passo seria revisar a arquitetura atual, procurando identificar blocos da aplicação para redesenhar, visando construir uma arquitetura nativa da cloud AWS. Isso é, utilizar aplicações em contêineres (ECS/EKS) ou instancias (EC2) com ELB e Auto Scaling, bancos de dados gerenciados (RDS/DynamoDB/ElasticCache), se possível reescrever aplicações em serviços serverless como o AWS Lambda para tornar toda a infraestrutura capaz de reagir a aumentos e diminuições de demanda de forma automática.

A execução da refatoração pode ser feita utilizando estratégias de migração tais como a blue-green deployment (criação de uma versão refatorada em paralelo e realizando a migração somente após essa passar em todos os checks) ou a canary releases (migração gradual do tráfego para a nova aplicação visando detectar problemas antes de realizar a migração completa).

## 2. Como você garantiria que a aplicação migre para a AWS sem causar interrupções significativas para os usuários? Descreva os métodos e ferramentas que utilizaria para testar a aplicação durante a migração e para minimizar o tempo de inatividade.

Como foi dito anteriormente, idealmente, deve-se utilizar estratégias de migração como a blue-green deployment ou a canary releases que permite realizar uma migração, diminuído os impactos de possíveis problemas. Dentro de ferramentas, pode-se utilizar o AWS CloudWatch (monitoramento), AWS Backup e AWS CodePipeline.

## 3. Quais benefícios específicos da nuvem AWS você espera aproveitar após a migração e como planeja otimizar o desempenho da aplicação na nova infraestrutura?

A migração para a AWS irá providenciar melhorias em respostas a incrementos e diminuições de demanda (Auto Scaling), alta tolerância a desastres e disponibilidade (implementação em múltiplas AZ), diminuição em gastos humanos com gerenciamento de banco de dados (RDS, DynamoDB e ElasticCache), diminuição de latência (CloudFront).
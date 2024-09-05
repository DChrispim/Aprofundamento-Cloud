# Proposta

Você é o gerente de TI de um hospital de médio porte chamado HealthCare Central. O hospital está crescendo rapidamente, atendendo um número cada vez maior de pacientes e expandindo seus serviços médicos. Com isso, as necessidades de infraestrutura de TI também estão aumentando. A diretoria está considerando migrar os sistemas atuais para a nuvem para melhorar a eficiência e a qualidade do atendimento. Sua missão é liderar esse projeto e garantir que a transição seja suave e benéfica para o hospital.

Desafio: A decisão de migrar para a nuvem não é simples. Embora os benefícios sejam claros – como escalabilidade, flexibilidade e potencial redução de custos – há várias preocupações que você precisa abordar. Entre elas, as questões de segurança dos dados dos pacientes, os custos a longo prazo e a integração dos novos sistemas na nuvem com os sistemas legados do hospital.

Orientação: Para lidar com esse desafio, você decide adotar uma abordagem estruturada. Primeiro, você realizará uma análise detalhada dos requisitos do hospital e dos diferentes modelos de implantação de nuvem disponíveis (pública, privada, híbrida e multi-nuvem). Você também fará um levantamento dos provedores de serviços de nuvem, avaliando suas ofertas em termos de segurança, custo-benefício e capacidade de integração com sistemas legados.

Você planeja dividir o projeto em fases:

1. Planejamento e Análise: Levantar todos os requisitos, avaliar os riscos e benefícios, e escolher o modelo de nuvem mais adequado.
2. Prova de Conceito (PoC): Implementar um pequeno projeto piloto para testar a viabilidade e identificar possíveis problemas.
3. Implementação: Migrar os sistemas em fases, começando pelos menos críticos, para minimizar os riscos.
4. Monitoramento e Otimização: Acompanhar a performance e fazer ajustes necessários para garantir que os objetivos do projeto sejam atingidos.

Sua estratégia envolve comunicação constante com todas as partes interessadas, incluindo a equipe médica, a equipe de segurança, os desenvolvedores e a diretoria. Você também planeja realizar treinamentos para garantir que todos estejam preparados para trabalhar com os novos sistemas na nuvem.

Questões que você deve levar em consideração ao escrever sua solução:

1. Segurança: Quais medidas específicas você implementaria para garantir a segurança dos dados dos pacientes na nuvem, considerando as preocupações com possíveis vulnerabilidades e ataques cibernéticos?
2. Custos: Como você gerenciaria os custos da migração e operação na nuvem, garantindo que o hospital obtenha o melhor retorno sobre o investimento?
3. Integração com Sistemas Legados: Qual seria sua estratégia para integrar os sistemas legados com os novos sistemas na nuvem, minimizando a interrupção dos serviços hospitalares e garantindo a compatibilidade?

# Projeto de migração

## 1. Segurança: Quais medidas específicas você implementaria para garantir a segurança dos dados dos pacientes na nuvem, considerando as preocupações com possíveis vulnerabilidades e ataques cibernéticos?

Todos os dados armazenados em sistemas brasileiros precisam seguir as leis e normas brasileiras. A principal lei, nesse caso, é a LGPD (Lei n.º 13.709/2018), que regula o tratamento e armazenamento de dados pessoais. Nela, podemos citar dois pontos principais (fonte: [Princípios da LGPD](https://www.gov.br/esporte/pt-br/acesso-a-informacao/lgpd/principios-da-lgpd)):

- **Segurança:** trata-se da utilização de medidas técnicas e administrativas qualificadas para proteger os dados pessoais de acessos não autorizados e de situações acidentais ou ilícitas de destruição, perda, alteração, comunicação ou difusão;
- **Responsabilização e prestação de contas:** demonstração, pelo Controlador ou pelo Operador, de todas as medidas eficazes e capazes de comprovar o cumprimento da lei e a eficácia das medidas aplicadas.

Outras normas precisam ser observadas no caso de um sistema hospitalar pois este trata de dados médicos. As normas relevantes aqui são a [Resolução CFM n.º 1.821/2007](https://www.gov.br/conarq/pt-br/legislacao-arquivistica/resolucoes/resolucao-cfm-no-1-821-de-11-de-julho-de-2007), [Resolução CFM n.º 1.643/2002](https://www.in.gov.br/web/dou/-/resolucao-cfm-n-2.314-de-20-de-abril-de-2022-397602852), [RDC 302/2005 e RDC 63/2011](https://www.gov.br/anvisa/pt-br/assuntos/servicosdesaude/seguranca-do-paciente/legislacao). De forma resumida, ao nosso caso, elas exigem:

- Confidencialidade, controle de acesso e armazenamento por 20 anos dos dados dos pacientes.

Outras normas internacionais podem ser observadas (como Health Insurance Portability and Accountability Act - HIPAA, General Data Protection Regulation - GDPR, ISO/IEC 27001 e NIST Cybersecurity Framework), mas iremos manter o nosso caso voltado ao mercado brasileiro.

Usando como base os pontos anteriores, podemos descrever estratégias para garantir que as normas sejam cumpridas.

- **Criptografia de Dados:**
    - **Objetivo:** Garantir o controle de acesso aos dados. Os principais pontos a serem observados aqui são:
        - Criptografia em trânsito utilizando protocolos de segurança como TLS/SSL.
        - Criptografia em repouso dos dados armazenados utilizando algoritmos robustos como AES-256.
- **Gerenciamento de Acessos:**
    - **Objetivo:** Controlar o acesso aos dados, apenas os funcionários necessários podem fazer esse acesso. Os principais pontos são:
        - Utilizar políticas de identidades e acessos para grupos e indivíduos com controle granular e vencimento automático programada.
        - Utilizar o princípio do menor privilégio.
- **Boas práticas de segurança:**
    - Realizar auditorias regulares por terceiros.
    - Implementação de políticas de conformidade e rastreabilidade.
    - Usar autenticação multifatorial para todas as contas.
    - Gerenciamento de chaves de acesso programáticas.
- **Monitoramento e Detecção de Ameaças:**
    - **Objetivo:** Utilização de sistema de monitoramento e prevenção de ataques cibernéticos. Os principais pontos aqui são:
        - Utilizar medidas de segurança de rede contra ataques DoS e DDoS.
        - Coletar e analisar logs de segurança.
        - Utilizar detecção de ameaças internas, ou violação de normas, utilizando padrões de acesso dos usuários.
        - Incentivar a equipe de segurança de TI a se atualizar com os novos tipos norma e padrões contra novos tipos de ataques cibernéticos.
- **Backup e Recuperação de Desastres:**
    - **Objetivo:** Utilizar backups automáticos, implementar esquema de recuperação em caso de desastres. Os principais pontos aqui são:
        - Programar o armazenamento de dados por um período não inferior a 20 anos nos casos descritos na norma.
        - Backups automáticos e regulares em lugares distintos.
        - Planejar esquema de recuperação de desastres considerando diferentes cenários.

Finalizando, podemos ressaltar que aqui apenas desenvolvemos os pontos referentes à segurança de dados em uma parte da infraestrutura de TI, mas essas diretrizes devem ser observadas em todos os níveis da infraestrutura de TI.

## 2. Custos: Como você gerenciaria os custos da migração e operação na nuvem, garantindo que o hospital obtenha o melhor retorno sobre o investimento?

Os custos de migração e operação na nuvem dependem de muitos fatores técnicos, de modo que uma análise com esse nível de detalhes é inviável sem essas informações. Todavia, podemos abordar alguns pontos principais a serem observados. O ponto inicial a ser realizado é uma análise dos custos totais da infraestrutura, chamado de Custo Total de Propriedade (Total Cost of Ownership - TCO). O TCO da infraestrutura no local inclui custos com infraestrutura, manutenção, pessoal, entre outros. Em seguida, deve-se realizar esse mesmo processo para a infraestrutura na nuvem. Normalmente existem estimadores de TCO nos principais provedores de nuvens públicas, mas esse processo envolve escolhas técnicas e estratégicas complexas. Podemos enumerar alguns dos principais pontos a serem observados.

- Escolha de método de migração para cada serviço de TI. Normalmente se utiliza a técnica dos 5 R's que coloca as cinco opções de migração de serviço como: Rehost (ou lift-and-shift), Refactor, Rearchitect, Rebuild e Replace. Cada escolha envolve custos de serviço, custo de migração, tempo e pessoal específicos, além de depender dos diferentes serviços do provedor de nuvem privada. Essa escolha é a mais importante e impactante no custo final.
- Escolher o modelo de preço para cada serviço de TI. Diferentes serviços possuem custos e modelos de cobrança distintos. A principal diferença aqui entre a nuvem privada e a nuvem pública é a opção de se escolher modelos não-fixos de cobrança. Entre eles podemos destacar:
- Modelos pay-as-you-go, onde é cobrado pelo serviço utilizado sem um compromisso anterior.
- Modelos com reserva de uso, onde é acordado um preço com desconto pelo uso do serviço mesmo que ele não seja realmente utilizado. Possui opções flexíveis, mas com um desconto menor.
- Modelos pay-as-you-go de recursos ociosos, onde são ofertados recursos ociosos a preços menores, mas que podem ser interrompidos com um aviso de minutos.
- Utilizar modelos compatíveis com auto escalabilidade para serviços com demanda dinâmica. Isso diminui os custos sem impactar na usabilidade do serviço.
- Escolher o tipo de armazenamento e política de migração de ciclo de vida. Existem vários serviços com diferentes características e custos para armazenamento de arquivos. É importante estudar o padrão de acesso atual e as normas aplicáveis, essas características vão ditar a escolha de serviço e o ciclo de vida do arquivo (migração para serviços mais baratos, mas com tempo de acesso maior) até a sua exclusão final (depois do tempo legal requerido).
- Utilizar ferramentas de monitoramento e agregação de custos. Uma infraestrutura em nuvem pública pode possuir muitos serviços em diferentes setores da instituição. É importante agregar e monitorar esses custos. Isso é indispensável para procurar opções de desconto por faixa de uso para toda a instituição.

Essas são algumas das práticas que devem ser adotadas para obter o maior retorno pelo investimento realizado em migração para uma nuvem pública.

## 3. Integração com Sistemas Legados: Qual seria sua estratégia para integrar os sistemas legados com os novos sistemas na nuvem, minimizando a interrupção dos serviços hospitalares e garantindo a compatibilidade?

Como foi descrito na pergunta anterior, normalmente em uma migração de serviços de TI pode-se utilizar a técnica dos 5 R's (Rehost ou Lift-and-Shift, Refactor, Rearchitect, Rebuild e Replace) onde cada opção leva a diferentes custos de serviço, custo de migração, tempo e pessoal e depende do que oferecido por cada provedor de nuvem privada. Aqui vamos explorar pontos fortes e fracos, custos e dificuldades de aplicação levando em conta diferentes tipos de serviços legados.

- Rehost ou lift-and-shift consiste em migrar o serviço para a nuvem privada sem modificações. É uma forma rápida de migração, oferece poucos problemas de interrupção e incompatibilidade, porém que geralmente poderia ser optimizada em termos de funcionamento e/ou custo. Essa opção nem sempre é viável dependendo do serviço legado.
- Refactor consiste em adaptar partes do sistema legado antes de fazer a migração para a nuvem privada. Em comparação ao rehost, o número de sistemas que podem ser migrados com essa estratégia é maior e pode-se planejar a integração com serviços da nuvem privada. Podem, aqui teremos de fazer modificações no serviço, o que pode acarretar uma demora maior de migração, custos adicionais e possíveis problemas de compatibilidade de API.
- Rearchitect é uma das formas mais complexas de migração, pois envolve refazer a arquitetura do sistema legado, mas oferece o maior ganho de combatibilidade com a infraestrutura e serviços oferecidos pela nuvem privada. Pode resultar em menores custos operacionais, pelo uso de tecnologias como microsserviços, containers e automações, mas certamente possui custos maiores em termos de planejamento e migração. Esse último deve ser feito de forma cuidadosa para não impactar a operação.
- Rebuild significa refazer o sistema legado. Essa solução é ideal quando o sistema legado precisa ser substituído obrigatoriamente devido a problemas de integração ou impossibilidade de modernização. Aqui teremos custos de planejamento altos, mas com uma possível integração total com o ambiente da nuvem.
- Replace consiste em migrar para uma solução SaaS da nuvem. Os casos para se utilizar essa estratégia são similares aos do Rearchitect e Rebuild, mas aqui devemos observar outros fatores como conformidade da solução de terceiro, estratégias de mercado e ponderar sobre o controle e customização sobre o serviço.

Esses são os pontos a serem observados em cada estratégia de migração de sistemas legados para o ambiente da nuvem.
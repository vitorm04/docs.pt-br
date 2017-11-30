---
title: principais argumentos
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | principais argumentos"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b557d0b641bfe95c025cadb13f82c3f8927f4bc8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="key-takeaways"></a>Principais argumentos

Como um resumo e pedidas, a seguir estão as mais importantes conclusões deste guia.

**Benefícios do uso de contêineres.** Soluções com base em contêiner fornecem o benefício importante de economias de custo como contêineres são uma solução de problemas de implantação causada pela falta de dependências em ambientes de produção. Contêineres de melhorar significativamente as operações de produção e DevOps.

**Contêineres serão onipresentes.** Contêineres do docker estão se tornando o verdadeiro padrão do setor de contêiner, os fornecedores mais significativos na ecossistemas Windows e Linux com suporte. Isso inclui AWS Amazon, Microsoft, Google e IBM. Em breve, o Docker provavelmente será onipresente em data centers de nuvem e local.

**Contêineres como uma unidade de implantação.** Um contêiner do Docker está se tornando a unidade padrão de implantação para qualquer serviço ou aplicativo baseado em servidor.

**Microservices.** A arquitetura microservices está se tornando a abordagem preferencial para aplicativos de missão crítica distribuídos e grandes ou complexas com base em vários subsistemas independentes na forma de serviços autônomos. Em uma arquitetura baseada em microsserviço, o aplicativo é compilado como uma coleção de serviços que podem ser desenvolvidos, testados, com controle de versão, implantado e dimensionada de modo independente; Isso pode incluir qualquer banco de dados autônomo relacionado.

**Design controlado por domínio e SOA.** Os padrões de arquitetura microservices derivam de arquitetura orientada a serviços (SOA) e design orientado a domínio (DDD). Ao projetar e desenvolver microservices para ambientes com o surgimento de formatação de um domínio específico de regras de negócio, é importante levar em conta DDD abordagens e padrões.

**Microservices desafios.** Microservices oferecem muitos recursos avançados, como implantação independente, os limites de subsistema de alta segurança e diversidade de tecnologia. No entanto, elas também geram muitos novos desafios relacionados ao desenvolvimento de aplicativos distribuídos, como fragmentada e modelos de dados independentes, a comunicação resiliente entre microservices, consistência eventual e a complexidade operacional resultante agregar informações de log e monitoramentos de vários microservices. Esses aspectos introduzem um nível de complexidade maior que um aplicativo monolítico tradicional. Como resultado, apenas os cenários específicos são adequados para aplicativos baseados em microsserviço. Isso inclui aplicativos grandes e complexos com vários subsistemas em evolução; Nesses casos, vale a pena investir em uma arquitetura de software mais complexa, pois ele fornecerá melhor a longo prazo da agilidade e a manutenção do aplicativo.

**Contêineres para qualquer aplicativo.** Contêineres são convenientes para microservices, mas não são exclusivos para eles. Contêineres também podem ser usados com aplicativos monolíticos, incluindo aplicativos herdados com base no .NET Framework tradicional e modernizado por meio de contêineres do Windows. Os benefícios de usar o Docker, como resolver vários problemas de implantação de produção e fornecer ambientes de desenvolvimento e teste de última geração, se aplicam a vários tipos diferentes de aplicativos.

**CLI versus IDE.** Com as ferramentas da Microsoft, você pode desenvolver aplicativos .NET em contêineres usando a abordagem preferencial. Você pode desenvolver com uma CLI e um ambiente com base no editor usando a CLI do Docker e o código do Visual Studio. Ou você pode usar uma abordagem centrada em IDE com Visual Studio e seus recursos exclusivos para Docker, como podem depurar aplicativos de contêiner vários.

**Aplicativos de nuvem resilientes.** Em sistemas baseados em nuvem e sistemas distribuídos em geral, há sempre o risco de falha parcial. Como clientes e serviços são processos separados (contêineres), um serviço pode não ser capaz de responder de forma oportuna de uma solicitação do cliente. Por exemplo, um serviço pode ser pressionada devido a uma falha parcial ou de manutenção; o serviço pode estar sobrecarregado e respondendo muito lenta para solicitações; ou pode simplesmente não ser acessível por um curto período devido a problemas de rede. Portanto, um aplicativo baseado em nuvem deve adotar as falhas e ter uma estratégia para responder a essas falhas. Essas estratégias podem incluir políticas de repetição (reenviar mensagens ou tentar novamente solicitações) e padrões de implementação disjuntor para evitar exponencial de carga de solicitações repetidas. Basicamente, os aplicativos baseados em nuvem devem ter mecanismos resilientes — personalizado aqueles tanto aquelas com base na infraestrutura de nuvem, como estruturas de alto nível de orchestrators ou barramentos de serviço.

**Segurança.** Em nosso mundo moderno de contêineres e microservices pode expor vulnerabilidades de novo. Segurança básica do aplicativo é baseada na autenticação e autorização; Existem várias maneiras para implementá-las. No entanto, a segurança de contêiner inclui outros componentes fundamentais que resultam em aplicativos inerentemente mais seguros. Um elemento essencial da criação de aplicativos mais seguros é ter uma maneira segura de se comunicar com outros sistemas e aplicativos, algo que geralmente requer credenciais, tokens, senhas e outros tipos de informações confidenciais — normalmente conhecido como segredos do aplicativo. Qualquer solução de segurança deve seguir as práticas recomendadas de segurança, como a criptografia de segredos em trânsito; criptografar os segredos em repouso; e impedindo segredos vazamento acidentalmente quando consumido pelo aplicativo final. Esses segredos precisam ser armazenados e mantidos em segurança em algum lugar. Para ajudar com a segurança, você pode tirar proveito da infraestrutura do orchestrator seu escolhida ou da infraestrutura de nuvem como o Cofre de chaves do Azure e as maneiras em que ele fornece código do aplicativo para usá-lo.

**Orchestrators.** Com base em contêiner orchestrators como as fornecidas no serviço de contêiner do Azure (Kubernetes Mesos DC/OS e Docker Swarm) e o Azure Service Fabric são indispensáveis para qualquer aplicativo pronto para produção microsserviço em qualquer contêiner vários aplicativo com uma complexidade significativa, escalabilidade e constante evolução. Este guia introduziu orchestrators e sua função em soluções com base em contêiner e microsserviço. Se as necessidades do aplicativo estiver movendo em direção a complexos aplicativos em contêineres, você achará útil para buscar recursos adicionais para saber mais sobre orchestrators

>[!div class="step-by-step"]
[Anterior] (secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)

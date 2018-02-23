---
title: Principais aspectos a serem lembrados
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Principais aspectos a serem lembrados"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2dbcfbe28f5461b7a40e8b0b49dbcf5e31490d70
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="key-takeaways"></a>Principais aspectos a serem lembrados

A seguir, encontram-se as conclusões mais importantes deste guia, que servem como um resumo dos principais aspectos a serem lembrados.

**Benefícios do uso de contêineres.** Soluções baseadas em contêineres fornecem benefícios importantes para economia de custo, visto que contêineres são uma solução para problemas de implantação causados pela falta de dependências em ambientes de produção. Portanto, os contêineres melhoram significativamente as operações de produção e DevOps.

**Contêineres serão onipresentes.** Contêineres baseados no Docker estão se tornando o verdadeiro padrão no setor de contêineres, compatíveis com os fornecedores mais significativos nos ecossistemas do Windows e do Linux. Isso inclui Microsoft, Amazon AWS, Google e IBM. No futuro próximo, o Docker provavelmente será onipresente em qualquer datacenter na nuvem e local.

**Contêineres como uma unidade de implantação.** Um contêiner do Docker está se tornando a unidade padrão de implantação para qualquer serviço ou aplicativo baseado em servidor.

**Microsserviços.** A arquitetura de microsserviços está se tornando a abordagem preferencial para aplicativos críticos grandes ou complexos e distribuídos baseados em diversos subsistemas independentes na forma de serviços autônomos. Em uma arquitetura baseada em microsserviço, o aplicativo é criado como uma coleção de serviços que podem ser desenvolvidos, testados, implantados, dimensionados e ter as versões controladas de forma independente. Isso pode incluir qualquer banco de dados autônomo relacionado.

**Design controlado por domínio e SOA.** Os padrões de arquitetura de microsserviços derivam da SOA (arquitetura orientada a serviços) e do DDD (design controlado por domínio). Ao projetar e desenvolver microsserviços para ambientes com regras de negócio em evolução que definem um domínio específico, é importante levar em conta as abordagens e padrões do DDD.

**Desafios dos microsserviços.** Os microsserviços oferecem muitos recursos avançados, como implantação independente, fortes limites de subsistema e diversidade tecnológica. No entanto, eles também apresentam vários novos desafios relacionados com o desenvolvimento de aplicativos distribuídos, como modelos de dados fragmentados e independentes, comunicação resiliente entre microsserviços, consistência eventual e complexidade operacional como resultado da combinação de registros em log e monitoramento de informações de diversos microsserviços. Esses aspectos geram um nível mais alto de complexidade que um aplicativo monolítico tradicional. Assim, apenas cenários específicos são adequados para aplicativos baseados em microsserviço. Isso inclui aplicativos grandes e complexos com vários subsistemas em evolução. Nesses casos, vale a pena investir em uma arquitetura de software mais complexa, que oferecerá melhor agilidade a longo prazo e manutenção do aplicativo.

**Contêineres para qualquer aplicativo.** Contêineres são convenientes para microsserviços, mas não são exclusivos para eles. Contêineres também podem ser usados com aplicativos monolíticos, incluindo aplicativos herdados baseados no .NET Framework tradicional e modernizados por meio de contêineres do Windows. Os benefícios de usar o Docker, como resolver vários problemas entre as fases de implantação e produção e fornecer ambientes de desenvolvimento e teste de última geração, aplicam-se a vários tipos diferentes de aplicativos.

**CLI versus IDE.** Com as ferramentas da Microsoft, é possível desenvolver aplicativos .NET em contêineres usando sua abordagem preferencial. Você pode desenvolver com uma CLI e um ambiente baseado em editor usando a CLI do Docker e o Visual Studio Code. Outra opção é usar uma abordagem centrada em IDE com Visual Studio e seus recursos exclusivos para Docker, como depurar aplicativos de vários contêineres.

**Aplicativos de nuvem resilientes.** Em sistemas baseados em nuvem e sistemas distribuídos em geral, há sempre o risco de falha parcial. Como clientes e serviços são processos separados (contêineres), um serviço pode não ser capaz de responder de forma oportuna a uma solicitação do cliente. Por exemplo, um serviço pode estar inoperante por conta de uma falha parcial ou para manutenção; estar sobrecarregado e respondendo a solicitações de maneira extremamente lenta ou pode simplesmente não estar acessível durante um curto período devido a problemas de rede. Portanto, um aplicativo baseado em nuvem deve adotar essas falhas e ter uma estratégia para responder a elas. Essas estratégias podem incluir políticas de repetição (reenviar mensagens ou repetir solicitações) e padrões de implementação disjuntor para evitar uma carga exponencial de solicitações repetidas. Basicamente, os aplicativos baseados em nuvem devem ter mecanismos resilientes — personalizados ou baseados na infraestrutura de nuvem, como estruturas de alto nível de orquestradores ou barramentos de serviço.

**Segurança.** O mundo moderno de contêineres e microsserviços pode expor novas vulnerabilidades. A segurança básica do aplicativo se baseia em autenticação e autorização; e existem diversas maneiras de implementá-las. No entanto, a segurança do contêiner tem componentes fundamentais que geram aplicativos inerentemente mais seguros. Um elemento crítico da criação de aplicativos mais seguros é ter uma maneira segura de se comunicar com outros sistemas e aplicativos, algo que geralmente requer credenciais, tokens, senhas e outros tipos de informações confidenciais — normalmente conhecidos como segredos do aplicativo. Qualquer solução de segurança deve seguir as melhores práticas de segurança, como a criptografia de segredos em trânsito e em repouso e a prevenção contra o vazamento acidental de segredos quando consumidos pelo aplicativo final. Esses segredos precisam ser armazenados e mantidos em segurança em algum lugar. Para ajudar com a segurança, você pode tirar proveito da infraestrutura do orquestrador de sua escolha ou de uma infraestrutura de nuvem como o Azure Key Vault e as maneiras que o código do aplicativo pode usá-lo.

**Orquestradores.** Orquestradores baseados em contêineres como os fornecidos no Serviço de Contêiner do Azure (Kubernetes, Mesos DC/OS e Docker Swarm) e no Azure Service Fabric são indispensáveis para qualquer aplicativo pronto para produção baseado em microsserviço e com vários contêineres com necessidades significativas de complexidade, escalabilidade e em constante evolução. Este guia apresentou os orquestradores e sua função em soluções baseadas em microsserviços e contêineres. Se suas necessidades apontam para aplicativos complexos em contêineres, pode ser útil procurar outros recursos para saber mais sobre os orquestradores

>[!div class="step-by-step"]
[Anterior] (secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)

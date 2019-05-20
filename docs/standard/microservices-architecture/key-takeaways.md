---
title: Principais aspectos a serem lembrados
description: Saiba quais são os principais aspectos a serem lembrados do guia/livro eletrônico “Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres” para ter uma visão geral de alto nível dos problemas envolvidos ao usar uma arquitetura de microsserviços, como as vantagens e desvantagens, os padrões de DDD para design e desenvolvimento, bem como a resiliência, a segurança e o uso de orquestradores.
ms.date: 10/19/2018
ms.openlocfilehash: 3b8b7be9b3903c64221cba7c6abdb1e38f5d944f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639696"
---
# <a name="key-takeaways"></a>Principais aspectos a serem lembrados

A seguir, encontram-se as conclusões mais importantes deste guia, que servem como um resumo dos principais aspectos a serem lembrados.

**Benefícios do uso de contêineres.** As soluções baseadas em contêiner oferecem uma importante economia de custo porque ajudam a reduzir os problemas de implantação causados por dependências com falha em ambientes de produção. Portanto, os contêineres melhoram significativamente as operações de produção e DevOps.

**Contêineres serão onipresentes.** Os contêineres baseados no Docker estão se tornando o verdadeiro padrão no setor, com suporte dos principais fornecedores nos ecossistemas do Windows e do Linux, como Microsoft, Amazon AWS, Google e IBM. Provavelmente, em breve o Docker será predominante nos data centers de nuvem e locais.

**Contêineres como uma unidade de implantação.** Um contêiner do Docker está se tornando a unidade padrão de implantação para qualquer serviço ou aplicativo baseado em servidor.

**Microsserviços.** A arquitetura de microsserviços está se tornando a abordagem preferencial para aplicativos críticos grandes ou complexos e distribuídos baseados em diversos subsistemas independentes na forma de serviços autônomos. Em uma arquitetura baseada em microsserviço, o aplicativo é criado em uma coleção de serviços que podem ser desenvolvidos, testados, implantados e ter as versões controladas de forma independente. Cada serviço pode incluir qualquer banco de dados autônomo relacionado.

**Design controlado por domínio e SOA.** Os padrões de arquitetura de microsserviços derivam da SOA (arquitetura orientada a serviços) e do DDD (design controlado por domínio). Ao projetar e desenvolver microsserviços para ambientes com necessidades e regras dos negócios em evolução, é importante considerar as abordagens e os padrões de DDD.

**Desafios dos microsserviços.** Os microsserviços oferecem muitos recursos avançados, como implantação independente, fortes limites de subsistema e diversidade tecnológica. No entanto, eles também apresentam vários novos desafios relacionados com o desenvolvimento de aplicativos distribuídos, como modelos de dados fragmentados e independentes, comunicação resiliente entre microsserviços, consistência eventual e complexidade operacional como resultado da combinação de registros em log e monitoramento de informações de diversos microsserviços. Esses aspectos geram um nível de complexidade muito maior do que um aplicativo monolítico tradicional. Assim, apenas cenários específicos são adequados para aplicativos baseados em microsserviço. Isso inclui aplicativos grandes e complexos com vários subsistemas em evolução. Nesses casos, vale a pena investir em uma arquitetura de software mais complexa, pois ela fornecerá uma agilidade e uma manutenção de aplicativos melhores a longo prazo.

**Contêineres para qualquer aplicativo.** Os contêineres são convenientes para os microsserviços, mas também podem ser úteis para aplicativos monolíticos baseados no .NET Framework tradicional, quando são usados contêineres do Windows. Os benefícios de usar o Docker, como resolver vários problemas entre as fases de implantação e produção e fornecer ambientes de desenvolvimento e teste de última geração, aplicam-se a vários tipos de aplicativos diferentes.

**CLI versus IDE.** Com as ferramentas da Microsoft, é possível desenvolver aplicativos .NET em contêineres usando sua abordagem preferencial. Você pode desenvolver com uma CLI e um ambiente baseado em editor usando a CLI do Docker e o Visual Studio Code. Outra opção é usar uma abordagem centrada em IDE com o Visual Studio e seus recursos exclusivos para Docker, como a depuração de aplicativos de vários contêineres.

**Aplicativos de nuvem resilientes.** Em sistemas baseados em nuvem e sistemas distribuídos em geral, há sempre o risco de falha parcial. Como clientes e serviços são processos separados (contêineres), um serviço pode não ser capaz de responder de forma oportuna a uma solicitação do cliente. Por exemplo, um serviço pode estar inativo por causa de uma falha parcial ou de manutenção, estar sobrecarregado e respondendo a solicitações de maneira extremamente lenta ou simplesmente não estar acessível durante um curto período devido a problemas de rede. Portanto, um aplicativo baseado em nuvem deve adotar essas falhas e ter uma estratégia para responder a elas. Essas estratégias podem incluir políticas de repetição (reenviar mensagens ou repetir solicitações) e padrões de implementação disjuntor para evitar uma carga exponencial de solicitações repetidas. Basicamente, os aplicativos baseados em nuvem precisam ter mecanismos resilientes, seja com base na infraestrutura de nuvem ou personalizados, como os de alto nível fornecidos pelos orquestradores ou barramentos de serviço.

**Segurança.** O mundo moderno de contêineres e microsserviços pode expor novas vulnerabilidades. Há várias maneiras de implementar a segurança básica de aplicativo, com base em autenticação e autorização. No entanto, a segurança do contêiner precisa considerar os principais componentes adicionais que resultam em aplicativos inerentemente mais seguros. Um elemento crítico da criação de aplicativos mais seguros é implantar uma maneira segura de comunicar-se com outros aplicativos e sistemas, algo que geralmente requer credenciais, tokens, senhas e assim por diante, conhecidos como segredos do aplicativo. Toda solução de segurança precisa seguir as práticas recomendadas de segurança, como criptografia de segredos quando em trânsito e em repouso, e impedir que os segredos vazem ao serem consumidos pelo aplicativo final. Esses segredos precisam ser armazenados e mantidos em segurança, como quando o Azure Key Vault é usado.

**Orquestradores.** Os orquestradores baseados em contêiner, como o Serviço de Kubernetes do Azure e o Azure Service Fabric são uma parte fundamental de qualquer microsserviço e aplicativo baseado em contêiner significativo. Esses aplicativos apresentam alta complexidade, necessidades de escalabilidade e constante evolução. Este guia apresentou os orquestradores e sua função em soluções baseadas em microsserviços e contêineres. Se suas necessidades de aplicativo estão exigindo aplicativos complexos em contêineres, pode ser útil procurar outros recursos para saber mais sobre os orquestradores.

>[!div class="step-by-step"]
>[Anterior](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)

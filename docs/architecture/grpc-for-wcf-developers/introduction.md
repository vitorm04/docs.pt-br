---
title: Introdução-gRPC para desenvolvedores do WCF
description: Introdução
ms.date: 09/02/2019
ms.openlocfilehash: 3fb7ae440f65cc2daa2a2c984d01d0c0c1eac0aa
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967613"
---
# <a name="introduction"></a>Introdução

Ajudar os computadores a se comunicarem entre si tem sido uma das principais preocupaçãos da idade digital. Em particular, há um esforço contínuo para determinar o mecanismo de comunicação remota ideal que se adequará às demandas de interoperabilidade da infraestrutura atual. Como você pode imaginar, esse mecanismo muda conforme as demandas ou a infraestrutura evolui.

O lançamento do .NET Core 3,0 marca uma mudança no modo como a Microsoft fornece soluções de comunicação remota para os desenvolvedores que desejam fornecer serviços em uma variedade de plataformas. O .NET Core não oferece Windows Communication Foundation (WCF) pronto para uso, mas, com o lançamento da versão ASP.NET Core 3,0, ele fornece a funcionalidade interna de gRPC.

o gRPC é uma estrutura popular na Comunidade de software mais ampla, usada por desenvolvedores em várias linguagens de programação para cenários de RPC modernos. A Comunidade e o ecossistema são vibrantes e ativos, com suporte para o protocolo gRPC que está sendo adicionado a componentes de infraestrutura como kubernetes, malhas de serviço, balanceadores de carga e muito mais. Esses fatores, bem como seu desempenho, eficiência e compatibilidade entre plataformas, tornam o gRPC uma opção natural para novos aplicativos e aplicativos WCF migrando para o .NET Core.

## <a name="history"></a>Histórico

O princípio fundamental de uma rede de computadores como nada mais do que um grupo de computadores que trocam dados entre si para atingir um conjunto de tarefas inter-relacionadas não mudou desde seu início. No entanto, a complexidade, a escala e as expectativas cresceram exponencialmente.  

Durante os anos 90, a ênfase tinha se concentrado principalmente em aprimorar redes internas usando a mesma linguagem e plataformas. O TCP/IP tornou-se o padrão ouro para esse tipo de comunicação.

No entanto, o foco em breve mudou para a melhor maneira de otimizar a comunicação entre várias plataformas, promovendo uma abordagem independente de linguagem. A SOA (arquitetura orientada a serviços) forneceu uma estrutura para unir de forma flexível uma ampla coleção de serviços que poderiam ser fornecidos a um aplicativo.

O desenvolvimento de *Serviços Web* ocorreu quando todas as principais plataformas podiam acessar a Internet, mas eles ainda não podiam interagir entre si. Os serviços Web têm padrões e protocolos abertos, incluindo:

- XML para marcação e código de dados;
- SOAP (Simple Object Access Protocol) para transferir dados;
- WSDL (Web Services Definition Language) – descreve e conecta o serviço Web ao aplicativo cliente; *e*
- UDDI (integração de descoberta de descrição universal) – permite que os serviços Web sejam detectáveis por outros serviços

O SOAP define as regras pelas quais os elementos distribuídos de um aplicativo podem se comunicar entre si mesmo se estiverem em plataformas diferentes. O SOAP é baseado em XML e, portanto, é legível. O sacrifício para tornar o SOAP facilmente compreendido é o tamanho; Mensagens SOAP são maiores que mensagens em protocolos comparáveis. O SOAP foi projetado para dividir aplicativos monolíticos em formulários de vários componentes sem perder a segurança ou o controle. Portanto, o WCF foi projetado para trabalhar com esse tipo de sistema, ao contrário de gRPC, que começou como um sistema distribuído. O WCF abordou algumas dessas limitações ao desenvolver e documentar protocolos de extensão proprietários para a pilha SOAP, mas com o custo de falta de suporte de outras plataformas.

Windows Communication Foundation é uma estrutura para a criação de serviços. Ele foi projetado na 2000s inicial para ajudar os desenvolvedores usando a SOA inicial a gerenciar as complexidades de trabalhar com SOAP. Embora ele remova o requisito para que o desenvolvedor escreva seus próprios protocolos SOAP, o WCF ainda usa SOAP para habilitar a interoperabilidade com outros sistemas. O WCF também foi projetado para fornecer soluções em vários protocolos (HTTP/1.1, NetTCP e assim por diante).

## <a name="microservices"></a>Microsserviços

Em arquiteturas de microserviço, aplicativos grandes são criados como uma coleção de serviços modulares menores. Cada componente faz uma tarefa ou processo específico, e os componentes são projetados para funcionar intercorretamente, mas podem ser isolados conforme necessário.

As vantagens dos microserviços incluem:

- As alterações e atualizações podem ser manipuladas de forma independente.
- O tratamento de erros se torna mais eficiente, pois os problemas podem ser rastreados para serviços específicos que são, então, isolados, recriados, testados e reimplantados independentemente dos outros serviços.
- A escalabilidade pode ser confinada para instâncias ou serviços específicos, em vez de todo o aplicativo.
- O desenvolvimento pode ocorrer em várias equipes, com menos conflitos do que ocorre quando muitas equipes trabalham em uma única base de código.

A mudança para aumentar a virtualização, a computação em nuvem, os contêineres e os Internet das Coisas contribuíram para o aumento contínuo de microserviços. No entanto, os microserviços não estão sem seus desafios. A infra-estrutura fragmentada/descentralizada colocou mais ênfase na necessidade de simplicidade e velocidade ao se comunicar entre os serviços. Isso, por sua vez, atraiu atenção para a natureza mais trabalhoso e condelito de SOAP.

Ele estava nesse ambiente que o gRPC foi iniciado, 10 anos depois que a Microsoft lançou o WCF pela primeira vez. Evoluiu diretamente do RPC de infraestrutura interna (Stubby) do Google, o gRPC nunca foi baseado nos mesmos padrões e protocolos que informaram os parâmetros de muitas RPCs anteriores. Além disso, o gRPC era apenas baseado em HTTP/2 e é por isso que ele pode desenhar nos novos recursos fornecidos pelo protocolo de transporte avançado. Em particular, streaming bidirecional, mensagens binárias e multiplexação.

## <a name="about-this-guide"></a>Sobre este guia

Este guia aborda os principais recursos do gRPC. Os capítulos iniciais tomam uma visão geral dos principais recursos do WCF e os comparamos ao gRPC. Ele identifica onde estão as correlações diretas entre o WCF e o gRPC e também onde o gRPC oferece uma vantagem. Onde não há nenhuma correlação entre o WCF e o gRPC ou onde gRPC não é capaz de oferecer uma solução equivalente ao WCF, este guia irá sugerir soluções alternativas ou locais para obter mais informações.

Usando um conjunto de aplicativos WCF de exemplo, o capítulo 5 é uma análise aprofundada de uma conversão dos principais tipos de serviço WCF (solicitação-resposta simples, unidirecional e streaming) para seus equivalentes em gRPC.

A seção final do livro analisa como obter o melhor de gRPC na prática, incluindo o uso de ferramentas adicionais como contêineres do Docker ou kubernetes para aproveitar a eficiência do gRPC e uma visão detalhada do monitoramento com registro em log, métricas e distribuídos rastreio.

## <a name="whom-this-guide-is-for"></a>A quem este guia se destina

Este guia foi escrito para desenvolvedores que trabalham em .NET Framework ou .NET Core que usaram anteriormente o WCF e que estão buscando migrar seus aplicativos para um ambiente de RPC moderno para .NET Core 3,0 e versões posteriores. O guia também pode ser usado mais geralmente para os desenvolvedores que estão atualizando ou considerando a atualização para o .NET Core 3,0 que desejam usar as ferramentas de gRPC internas.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](grpc-overview.md)

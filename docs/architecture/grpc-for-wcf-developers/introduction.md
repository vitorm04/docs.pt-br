---
title: Introdução - gRPC para desenvolvedores WCF
description: Introdução
ms.date: 09/02/2019
ms.openlocfilehash: 41f470eb02a77b1b6a26a7d4c2ca347ad07d828d
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988928"
---
# <a name="introduction"></a>Introdução

Ajudar as máquinas a se comunicarem entre si tem sido uma das principais preocupações da era digital. Em particular, há um esforço contínuo para determinar o mecanismo de comunicação remota ideal que se adequa às demandas de interoperabilidade da infra-estrutura atual. Como você pode imaginar, esse mecanismo muda à medida que as demandas ou a infra-estrutura evoluem.

O lançamento do .NET Core 3.0 marca uma mudança na maneira como a Microsoft oferece soluções de comunicação remota para desenvolvedores que desejam fornecer serviços em uma variedade de plataformas. O .NET Core não oferece o Windows Communication Foundation (WCF) fora da caixa, mas, com o lançamento do ASP.NET Core 3.0, ele fornece funcionalidade gRPC incorporada.

gRPC é uma estrutura popular na comunidade de software mais ampla. É usado por desenvolvedores em muitas linguagens de programação para cenários RPC modernos. A comunidade e o ecossistema são vibrantes e ativos. O suporte ao protocolo gRPC está sendo adicionado a componentes de infra-estrutura como Kubernetes, caixas de serviço, balanceadores de carga e muito mais. Esses fatores, juntamente com seu desempenho, eficiência e compatibilidade entre plataformas, tornam o gRPC uma escolha natural para novos aplicativos e aplicativos WCF que se deslocam para o .NET Core.

## <a name="history"></a>Histórico

O princípio fundamental de uma rede de computadores como nada mais do que um grupo de computadores trocando dados entre si para alcançar um conjunto de tarefas interrelacionadas não mudou desde a sua criação. Mas a complexidade, escala e expectativas cresceram exponencialmente.  

Durante a década de 1990, a ênfase foi principalmente na melhoria das redes internas que usavam a mesma linguagem e plataformas. O TCP/IP tornou-se o padrão-ouro para este tipo de comunicação.

O foco logo mudou para a melhor forma de otimizar a comunicação em várias plataformas, promovendo uma abordagem agnóstica de linguagem. A arquitetura orientada a serviços (SOA) forneceu uma estrutura para acoplar vagamente uma ampla coleção de serviços que poderiam ser prestados a um aplicativo.

O desenvolvimento de *serviços web* ocorreu quando todas as principais plataformas podiam acessar a internet, mas ainda não conseguiam interagir entre si. Os serviços web têm padrões e protocolos abertos, incluindo:

- XML para dados de marcação e código.
- Protocolo simples de acesso a objetos (SOAP) para transferir dados.
- Linguagem de definição de serviços web (WSDL) para descrever e conectar serviços web a aplicativos clientes.
- Universal Description, Discovery e Integration (UDDI) para tornar os serviços web descobertos por outros serviços.

Soap define as regras pelas quais elementos distribuídos de um aplicativo podem se comunicar entre si, mesmo que estejam em plataformas diferentes. Soap é baseado em XML, então é legível por humanos. O sacrifício por fazer SOAP facilmente compreendido é o tamanho; As mensagens SOAP são maiores que as mensagens em protocolos comparáveis. Soap foi projetado para quebrar aplicações monolíticas em forma multicomponente sem perder a segurança ou o controle. Assim, o WCF foi projetado para trabalhar com esse tipo de sistema, ao contrário do gRPC, que começou como um sistema distribuído. O WCF abordou algumas dessas limitações ao desenvolver e documentar protocolos de extensão proprietários para a pilha SOAP, mas ao custo da falta de suporte de outras plataformas.

A Windows Communication Foundation é uma estrutura para serviços de construção. Foi projetado no início dos anos 2000 para ajudar os desenvolvedores que usam o SOA inicial para gerenciar as complexidades de trabalhar com SOAP. Embora remova a exigência de que os desenvolvedores escrevam seus próprios protocolos SOAP, o WCF ainda usa SOAP para permitir a interoperabilidade com outros sistemas. O WCF também foi projetado para fornecer soluções em vários protocolos (HTTP/1.1, Net.TCP e assim por diante).

## <a name="microservices"></a>Microsserviços

Em arquiteturas de microserviços, grandes aplicações são construídas como uma coleção de serviços modulares menores. Cada componente faz uma tarefa ou processo específico, e os componentes são projetados para funcionar interoperavelmente, mas podem ser isolados conforme necessário.

As vantagens dos microserviços incluem:

- Alterações e upgrades podem ser tratados de forma independente.
- O manuseio de erros torna-se mais eficiente porque os problemas podem ser rastreados para serviços específicos que são então isolados, reconstruídos, testados e reimplantados independentemente dos outros serviços.
- A escalabilidade pode ser limitada a instâncias ou serviços específicos, em vez de toda a aplicação.
- O desenvolvimento pode acontecer em várias equipes, com menos atrito do que ocorre quando muitas equipes trabalham em uma única base de código.

O movimento para o aumento da virtualização, da computação em nuvem, dos contêineres e da Internet das Coisas tem contribuído para o aumento contínuo dos microsserviços. Mas os microsserviços não são sem seus desafios. A infra-estrutura fragmentada/descentralizada deu mais ênfase à necessidade de simplicidade e rapidez na comunicação entre os serviços. Isso, por sua vez, chamou a atenção para a natureza às vezes trabalhosa e contorcida do SABÃO.

Foi nesse ambiente que o gRPC foi lançado, 10 anos após a Microsoft lançar o WCF pela primeira vez. Evoluído diretamente da infra-estrutura interna do Google RPC (Stubby), o gRPC nunca foi baseado nos mesmos padrões e protocolos que haviam informado os parâmetros de muitos RPCs anteriores. E o gRPC só foi baseado em HTTP/2. É por isso que ele poderia se basear nas novas capacidades que o protocolo avançado de transporte forneceu. Em particular, streaming bidirecional, mensagens binárias e multiplexação.

## <a name="about-this-guide"></a>Sobre este guia

Este guia abrange as principais características do gRPC. Os primeiros capítulos analisam as principais características do WCF e as comparam com as do gRPC. Identifica onde há correlações diretas entre WCF e gRPC e também onde o gRPC oferece uma vantagem. Quando não há correlação entre WCF e gRPC, ou quando o gRPC não é capaz de oferecer uma solução equivalente ao WCF, este guia sugerirá soluções de solução ou para onde ir para obter mais informações.

Usando um conjunto de aplicativos WCF de amostra, o Capítulo 5 é um olhar profundo para converter os principais tipos de serviço WCF (simples solicitação-resposta, unidirecional e streaming) para seus equivalentes em gRPC.

A seção final do livro analisa como obter o melhor do gRPC na prática. Esta seção inclui informações sobre o uso de ferramentas adicionais, como contêineres Docker ou Kubernetes, para aproveitar a eficiência do gRPC. Ele também inclui um olhar detalhado sobre o monitoramento com registro, métricas e rastreamento distribuído.

## <a name="who-this-guide-is-for"></a>A quem esse guia se destina

Este guia foi escrito para desenvolvedores que trabalham em .NET Framework ou .NET Core que usaram o WCF e que estão buscando migrar seus aplicativos para um ambiente RPC moderno para versões .NET Core 3.0 e posteriores. O guia também pode ser útil de forma mais geral para desenvolvedores que atualizam ou consideram atualizar para o .NET Core 3.0 e que desejam usar as ferramentas gRPC incorporadas.

>[!div class="step-by-step"]
>[Próximo](index.md)
>[anterior](grpc-overview.md)

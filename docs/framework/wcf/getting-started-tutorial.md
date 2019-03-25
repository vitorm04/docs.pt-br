---
title: 'Tutorial: Introdução a aplicativos do Windows Communication Foundation'
description: Esses tutoriais fornece uma introdução para a criação de aplicativos do WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 66211cfcf2b742e43eccbefb2bc7c4bd1147b05b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408854"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Tutorial: Introdução a aplicativos do Windows Communication Foundation
A seguinte série de tutoriais apresentam a você para o Windows Communication Foundation (WCF) experiência de programação. Trabalhar com esses tutoriais na ordem lhe dará um entendimento introdutório das etapas necessárias para criar aplicativos do WCF. Depois de terminar, você terá um serviço WCF em execução e um cliente do WCF que chama o serviço. 

O tutorial presume que você está usando o Visual Studio como ambiente de desenvolvimento. Se você estiver usando outro ambiente de desenvolvimento, ignore as instruções específicas do Visual Studio. 

Para aplicativos de WCF de exemplo que você pode baixar e executar, consulte [exemplos do Windows Communication Foundation](samples/index.md). Para obter uma introdução aos exemplos, consulte [exemplo de Introdução](samples/getting-started-sample.md).

Para obter informações mais detalhadas sobre a criação de serviços e clientes, consulte [programação de WCF básica](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>Tutoriais do WCF

Os três primeiros tutoriais descrevem como definir um contrato de serviço do WCF, como implementá-lo e como hospedá-lo. O serviço que você cria é auto-hospedado em um aplicativo de console. Você também pode hospedar serviços no Microsoft Internet Information Services (IIS). Para obter mais informações, confira [Como: Hospedar um serviço WCF no IIS](feature-details/how-to-host-a-wcf-service-in-iis.md). Embora você pode usar código para configurar o serviço no tutorial, você também pode [configurar os serviços dentro de um arquivo de configuração](configuring-services-using-configuration-files.md). 

- [Tutorial: Definir um contrato de serviço](how-to-define-a-wcf-service-contract.md)

    Você pode criar um contrato do WCF com uma interface definida pelo usuário. Este contrato define a funcionalidade que o serviço expõe.

- [Tutorial: Implementar um contrato de serviço](how-to-implement-a-wcf-contract.md)

    Depois de definir um contrato, você deve implementá-la com uma classe de serviço.

- [Tutorial: Hospedar e executar um serviço básico](how-to-host-and-run-a-basic-wcf-service.md)

    Configurar um ponto de extremidade para o serviço e hospedar o serviço em um aplicativo de console. Para um serviço se torne ativa, você deve configurá-lo e hospedá-lo em um ambiente de tempo de execução. Esse ambiente de tempo de execução cria o serviço e controla seu contexto e o tempo de vida.

Os próximos dois tutoriais descrevem como criar, configurar e usar um aplicativo cliente para chamar as operações de serviço expõe. Os serviços publicam metadados que definem as informações que um aplicativo cliente precisa para se comunicar com o serviço. Visual Studio automatiza o processo de acesso a esses metadados e usa-o para construir o aplicativo cliente para o serviço. Se você decidir não usar o Visual Studio, você pode usar o [ferramenta de utilitário de metadados ServiceModel (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) em vez disso.

- [Tutorial: Criar um cliente](how-to-create-a-wcf-client.md)

    Recupere metadados para a criação de um proxy de cliente WCF de um serviço WCF. Recuperar metadados, usando o Visual Studio para adicionar uma referência de serviço ou você pode usar a ferramenta Utilitário de metadados ServiceModel. Especifique o ponto de extremidade que o cliente usa para acessar o serviço.

- [Tutorial: Usar um cliente](how-to-use-a-wcf-client.md)

    Use o proxy de cliente do WCF para chamar as operações de serviço.

## <a name="reference"></a>Referência

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Consulte também

- [Visão geral conceitual](conceptual-overview.md)
- [Guia de documentação](guide-to-the-documentation.md)
- [O que é o Windows Communication Foundation](whats-wcf.md)
- [Detalhes de recursos do WCF](feature-details/index.md)
- [Ciclo de vida de programação básico](basic-programming-lifecycle.md)
- [Compilando clientes](building-clients.md)
- [Programação de WCF básica](basic-wcf-programming.md)
- [Como: Criar um contrato duplex](feature-details/how-to-create-a-duplex-contract.md)
- [Como: Serviços do Access com um contrato duplex](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Como: Use Svcutil.exe para baixar documentos de metadados](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Como: Publicar metadados para um serviço usando um arquivo de configuração](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Usando associações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md)
- [Exemplo de Introdução](samples/getting-started-sample.md)
- [Exemplos do Windows Communication Foundation](samples/index.md)
- [Auto-hospedagem](samples/self-host.md)



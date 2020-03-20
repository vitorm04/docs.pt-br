---
title: 'Tutorial: Comece com os aplicativos da Windows Communication Foundation'
description: Esses tutoriais fornecem uma introdução para criar aplicativos WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184116"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Tutorial: Comece com os aplicativos da Windows Communication Foundation
A série a seguir de tutoriais apresenta a experiência de programação da Windows Communication Foundation (WCF). Trabalhar através desses tutoriais em ordem lhe dará uma compreensão introdutória das etapas necessárias para criar aplicativos WCF. Depois de terminar, você terá um serviço WCF em execução e um cliente WCF que chama o serviço.

O tutorial pressupõe que você está usando o Visual Studio como ambiente de desenvolvimento. Se você estiver usando outro ambiente de desenvolvimento, ignore as instruções específicas do Visual Studio.

Para obter amostras de aplicativos WCF que você pode baixar e executar, consulte [amostras do Windows Communication Foundation](samples/index.md). Para uma introdução às amostras, consulte [A amostra de Início](samples/getting-started-sample.md).

Para obter informações mais detalhadas sobre a criação de serviços e clientes, consulte [programação Básica do WCF](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>Tutoriais do WCF

Os três primeiros tutoriais descrevem como definir um contrato de serviço WCF, como implementá-lo e como hospedá-lo. O serviço que você cria é auto-hospedado dentro de um aplicativo de console. Você também pode hospedar serviços em Serviços de Informações da Internet (IIS) da Microsoft. Para obter mais informações, consulte [Como hospedar um serviço WCF no IIS](feature-details/how-to-host-a-wcf-service-in-iis.md). Embora você use código para configurar o serviço no tutorial, você também pode [configurar serviços dentro de um arquivo de configuração](configuring-services-using-configuration-files.md).

- [Tutorial: Defina um contrato de serviço](how-to-define-a-wcf-service-contract.md)

    Você cria um contrato WCF com uma interface definida pelo usuário. Este contrato define a funcionalidade que o serviço expõe.

- [Tutorial: Implementar um contrato de serviço](how-to-implement-a-wcf-contract.md)

    Depois de definir um contrato, você deve implementá-lo com uma classe de serviço.

- [Tutorial: Hospede e execute um serviço básico](how-to-host-and-run-a-basic-wcf-service.md)

    Configure um ponto final para o serviço e hospede o serviço em um aplicativo de console. Para que um serviço se torne ativo, você deve configurá-lo e hospedá-lo em um ambiente de tempo de execução. Esse ambiente de tempo de execução cria o serviço e controla seu contexto e vida útil.

Os dois próximos tutoriais descrevem como criar, configurar e usar um aplicativo cliente para chamar as operações que o serviço expõe. Os serviços publicam metadados que definem as informações que um aplicativo cliente precisa para se comunicar com o serviço. O Visual Studio automatiza o processo de acesso a esses metadados e os utiliza para construir o aplicativo cliente para o serviço. Se você decidir não usar o Visual Studio, você pode usar a [ferramenta ServiceModel Metadata Utility *(Svcutil.exe)*](servicemodel-metadata-utility-tool-svcutil-exe.md) em vez disso.

- [Tutorial: Crie um cliente](how-to-create-a-wcf-client.md)

    Recupere metadados para criar um proxy de cliente WCF a partir de um serviço WCF. Você recupera metadados usando o Visual Studio para adicionar uma referência de serviço ou pode usar a ferramenta ServiceModel Metadata Utility. Você especifica o ponto final que o cliente usa para acessar o serviço.

- [Tutorial: Use um cliente](how-to-use-a-wcf-client.md)

    Use o proxy do cliente WCF para chamar as operações de serviço.

## <a name="reference"></a>Referência

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Confira também

- [Visão geral conceitual](conceptual-overview.md)
- [Guia da documentação](guide-to-the-documentation.md)
- [O que é a Windows Communication Foundation](whats-wcf.md)
- [Detalhes de recursos do WCF](feature-details/index.md)
- [Ciclo de vida da programação básica](basic-programming-lifecycle.md)
- [Construindo clientes](building-clients.md)
- [Programação básica do WCF](basic-wcf-programming.md)
- [Como: Criar um contrato duplex](feature-details/how-to-create-a-duplex-contract.md)
- [Como: Acessar serviços com contrato duplex](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Ferramenta serviceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Como: Usar svcutil.exe para baixar documentos de metadados](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Como: Publicar metadados para um serviço usando um arquivo de configuração](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Usando vinculações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md)
- [Obtendo amostra de início](samples/getting-started-sample.md)
- [Amostras da Windows Communication Foundation](samples/index.md)
- [Auto-hospedagem](samples/self-host.md)

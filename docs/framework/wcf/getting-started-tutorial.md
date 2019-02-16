---
title: Introdução ao Tutorial1
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 2bd0b7e0d927e53f70515cfa124034a4cacc5ce7
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332241"
---
# <a name="getting-started-tutorial"></a>Guia de introdução ao tutorial
Os tópicos contidos nesta seção destinam-se a fornecer uma exposição rápida para o Windows Communication Foundation (WCF) experiência de programação. Eles devem ser concluídos na ordem da lista que se encontra na parte inferior deste tópico. Trabalhar com este tutorial fornece uma compreensão introdutória das etapas necessárias para criar o cliente e um serviço WCF aplicativos. Um serviço expõe um ou mais pontos de extremidade, sendo que cada um deles expõe uma ou mais operações de serviço. O *ponto de extremidade* de um serviço Especifica um endereço em que o serviço pode ser encontrado, uma associação que contém as informações que descrevem como um cliente deve se comunicar com o serviço e um contrato que define a funcionalidade fornecida pelo serviço a seus clientes.

 Após concluir a sequência de tópicos neste tutorial, você terá um serviço em execução e um cliente que chama o serviço. Os três primeiros tópicos descrevem como definir um contrato de serviço, como implementá-lo e como hospedar o serviço. O serviço criado é auto-hospedado em um aplicativo de console. Os serviços também podem ser hospedados no IIS (Serviços de Informações da Internet). Para obter mais informações sobre como fazer isso, confira [Como: Hospedar um serviço WCF no IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md). O serviço está configurado no código; no entanto, os serviços também podem ser configurados em um arquivo de configuração. Para obter mais informações sobre como usar um arquivo de configuração, consulte [Configurando serviços usando arquivos de configuração](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).

 Os três tópicos a seguir descrevem como criar um proxy do cliente, configurar o aplicativo cliente e usar o proxy do cliente para chamar a operação de serviço exposta pelo serviço. Os serviços publicam metadados que definem as informações que um aplicativo cliente precisa para se comunicar com o serviço. Visual Studio 2012 automatiza o processo de acesso a esses metadados e usa-o para construir e configurar o aplicativo cliente para o serviço. Se você não estiver usando o Visual Studio 2012, você pode usar o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para construir e configurar o aplicativo cliente para o serviço.

Os tópicos nesta seção pressupõem que você esteja usando o Visual Studio como ambiente de desenvolvimento. Se você estiver usando outro ambiente de desenvolvimento, ignore as instruções específicas do Visual Studio.

Para aplicativos de exemplo que podem ser baixados no seu disco rígido e executar, consulte os tópicos [exemplos do Windows Communication Foundation (WCF)](./samples/index.md). Para este tópico, consulte, em particular, o [Introdução ao](../../../docs/framework/wcf/samples/getting-started-sample.md).

Para obter informações mais detalhadas sobre a criação de serviços e clientes, consulte [programação WCF básica](../../../docs/framework/wcf/basic-wcf-programming.md).

## <a name="in-this-section"></a>Nesta seção
 [Como: Definir um contrato de serviço](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)

 Descreve como criar um contrato do WCF usando uma interface definida pelo usuário. O contrato define a funcionalidade exposta pelo serviço.

 [Como: Implementar um contrato de serviço](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

 Descreve como implementar um contrato de serviço. Após ser definido, um contrato deve ser implementado com uma classe de serviço.

 [Como: Hospedar e executar um serviço básico](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)

 Descreve como configurar um ponto de extremidade para o serviço no código e como hospedar o serviço em um aplicativo de console. Para se tornar ativo, um serviço deve ser configurado e hospedado em um ambiente de tempo de execução. Esse ambiente cria o serviço e controla seu contexto e tempo de vida.

 [Como: Criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

 Descreve como recuperar metadados usados para criar um proxy de cliente WCF de um serviço WCF. Esse processo usa a funcionalidade Adicionar referência de serviço dentro do Visual Studio.

 [Como: Configurar um cliente](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

 Descreve como configurar um cliente WCF. A configuração do cliente requer a especificação do ponto de extremidade que o cliente usa para acessar o serviço.

 [Como: Usar um cliente](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

 Descreve como usar o proxy de cliente do WCF para invocar operações de serviço.

## <a name="reference"></a>Referência

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="related-sections"></a>Seções relacionadas

- [Exemplos do Windows Communication Foundation (WCF)](./samples/index.md)
- [Ciclo de vida de programação básica](../../../docs/framework/wcf/basic-programming-lifecycle.md)

## <a name="see-also"></a>Consulte também

- [Visão geral conceitual](../../../docs/framework/wcf/conceptual-overview.md)
- [Guia da documentação](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [O que é o Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)
- [Detalhes de recursos do WCF](../../../docs/framework/wcf/feature-details/index.md)

---
title: "Pontos de extremidade: endereços, associações e contratos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1ee80307e0db82f4744970844754a910e81ca3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Pontos de extremidade: endereços, associações e contratos
Toda a comunicação com um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço ocorre por meio de *pontos de extremidade* do serviço. Pontos de extremidade de fornecem aos clientes acesso para a funcionalidade oferecida por um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
 Cada ponto de extremidade consiste em quatro propriedades:  
  
-   Um endereço que indica onde o ponto de extremidade pode ser encontrado.  
  
-   Uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade.  
  
-   Um contrato que identifica as operações disponíveis.  
  
-   Um conjunto de comportamentos que especifique os detalhes de implementação de local do ponto de extremidade.  
  
 Este tópico aborda essa estrutura de ponto de extremidade e explica como ele é representado no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de objeto.  
  
## <a name="the-structure-of-an-endpoint"></a>A estrutura de um ponto de extremidade  
 Cada ponto de extremidade consiste no seguinte:  
  
-   Endereço: O endereço identifica exclusivamente o ponto de extremidade e informa o potencial de consumidores do serviço onde ele está localizado. Ele é representado no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de objeto, o <xref:System.ServiceModel.EndpointAddress> classe. Um <xref:System.ServiceModel.EndpointAddress> classe contém:  
  
    -   Um <xref:System.ServiceModel.EndpointAddress.Uri%2A> propriedade, que representa o endereço do serviço.  
  
    -   Um <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade, que representa a identidade de segurança do serviço e uma coleção de cabeçalhos de mensagem opcional. Os cabeçalhos de mensagem opcional são usados para fornecer mais e obter mais informações de endereçamento para identificar ou interagir com o ponto de extremidade.  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Especificando um endereço de ponto de extremidade](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   Vinculação: A associação especifica como se comunicar com o ponto de extremidade. Isso inclui:  
  
    -   O protocolo de transporte a ser usado (por exemplo, TCP ou HTTP).  
  
    -   A codificação a ser usada para as mensagens (por exemplo, texto ou binário).  
  
    -   Os requisitos de segurança necessários (por exemplo, SSL ou SOAP segurança de mensagem).  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Visão geral de associações do WCF](../../../../docs/framework/wcf/bindings-overview.md). Uma associação é representada no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de objeto pela classe base abstrata <xref:System.ServiceModel.Channels.Binding>. Na maioria dos cenários, os usuários podem usar uma das associações fornecidas pelo sistema. Para obter mais informações, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
-   Contratos: O contrato descreve qual funcionalidade expõe o ponto de extremidade para o cliente. Especifica um contrato:  
  
    -   As operações que podem ser chamadas por um cliente.  
  
    -   O formato da mensagem.  
  
    -   O tipo de dados necessários para chamar a operação ou parâmetros de entrada.  
  
    -   Que tipo de mensagem de resposta ou processamento em que o cliente pode esperar.  
  
     Para obter mais informações sobre como definir um contrato, consulte [criar contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
-   Comportamentos: Você pode usar os comportamentos de ponto de extremidade para personalizar o comportamento local do ponto de extremidade de serviço. Comportamentos de ponto de extremidade alcançar isso participando no processo de criação um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tempo de execução. Um exemplo de um comportamento de ponto de extremidade é o <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> propriedade, que permite que você especifique um endereço de escutando diferente que o endereço SOAP ou WSDL Web Services Description Language (). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## <a name="defining-endpoints"></a>Definir pontos de extremidade  
 Você pode especificar o ponto de extremidade para um serviço usando código imperativa ou declarativamente por meio da configuração. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Como: criar um ponto de extremidade de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) e [como: criar um ponto de extremidade de serviço em código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 Esta seção explica a finalidade de associações, pontos de extremidade e endereços; mostra como configurar uma associação e um ponto de extremidade; e demonstra como usar o `ClientVia` comportamento e `ListenUri` propriedade.  
  
 [Endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 Descreve como os pontos de extremidade são resolvidos em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Bindings](../../../../docs/framework/wcf/feature-details/bindings.md) (Associações)  
 Descreve como as associações são usadas para especificar o transporte, a codificação e detalhes de protocolo necessárias para clientes e serviços para se comunicar entre si.  
  
 [Contratos](../../../../docs/framework/wcf/feature-details/contracts.md)  
 Descreve como os contratos definem os métodos de um serviço.  
  
 [Como: criar um ponto de extremidade de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Descreve como criar um ponto de extremidade de serviço na configuração.  
  
 [Como: criar um ponto de extremidade de serviço em código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Descreve como criar um ponto de extremidade de serviço em código.  
  
 [Como: usar o Svcutil.exe para validar o código de serviço compilado](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 Descreve como detectar erros nas configurações e implementações de serviço sem hospedar o serviço usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="see-also"></a>Consulte também  
 [Configuring Services](../../../../docs/framework/wcf/configuring-services.md) (Configurando serviços)  
 [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)

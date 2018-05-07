---
title: 'Pontos de extremidade: endereços, associações e contratos'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 0909d1d10ab8932f27f7ca6cba6207d57fa4f4cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Pontos de extremidade: endereços, associações e contratos
Toda a comunicação com um serviço do Windows Communication Foundation (WCF) ocorre por meio de *pontos de extremidade* do serviço. Pontos de extremidade de fornecem aos clientes acesso para a funcionalidade oferecida por um serviço WCF.  
  
 Cada ponto de extremidade consiste em quatro propriedades:  
  
-   Um endereço que indica onde o ponto de extremidade pode ser encontrado.  
  
-   Uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade.  
  
-   Um contrato que identifica as operações disponíveis.  
  
-   Um conjunto de comportamentos que especifique os detalhes de implementação de local do ponto de extremidade.  
  
 Este tópico aborda essa estrutura de ponto de extremidade e explica como ele é representado no modelo de objeto do WCF.  
  
## <a name="the-structure-of-an-endpoint"></a>A estrutura de um ponto de extremidade  
 Cada ponto de extremidade consiste no seguinte:  
  
-   Endereço: O endereço identifica exclusivamente o ponto de extremidade e informa o potencial de consumidores do serviço onde ele está localizado. Ela é representada no modelo de objeto WCF, a <xref:System.ServiceModel.EndpointAddress> classe. Um <xref:System.ServiceModel.EndpointAddress> classe contém:  
  
    -   Um <xref:System.ServiceModel.EndpointAddress.Uri%2A> propriedade, que representa o endereço do serviço.  
  
    -   Um <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade, que representa a identidade de segurança do serviço e uma coleção de cabeçalhos de mensagem opcional. Os cabeçalhos de mensagem opcional são usados para fornecer mais e obter mais informações de endereçamento para identificar ou interagir com o ponto de extremidade.  
  
     Para obter mais informações, consulte [especificando um endereço de ponto de extremidade](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   Vinculação: A associação especifica como se comunicar com o ponto de extremidade. Isso inclui:  
  
    -   O protocolo de transporte a ser usado (por exemplo, TCP ou HTTP).  
  
    -   A codificação a ser usada para as mensagens (por exemplo, texto ou binário).  
  
    -   Os requisitos de segurança necessários (por exemplo, SSL ou SOAP segurança de mensagem).  
  
     Para obter mais informações, consulte [visão geral de associações do WCF](../../../../docs/framework/wcf/bindings-overview.md). Uma associação é representada no modelo de objeto WCF, a classe base abstrata <xref:System.ServiceModel.Channels.Binding>. Na maioria dos cenários, os usuários podem usar uma das associações fornecidas pelo sistema. Para obter mais informações, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
-   Contratos: O contrato descreve qual funcionalidade expõe o ponto de extremidade para o cliente. Especifica um contrato:  
  
    -   As operações que podem ser chamadas por um cliente.  
  
    -   O formato da mensagem.  
  
    -   O tipo de dados necessários para chamar a operação ou parâmetros de entrada.  
  
    -   Que tipo de mensagem de resposta ou processamento em que o cliente pode esperar.  
  
     Para obter mais informações sobre como definir um contrato, consulte [criar contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
-   Comportamentos: Você pode usar os comportamentos de ponto de extremidade para personalizar o comportamento local do ponto de extremidade de serviço. Comportamentos de ponto de extremidade conseguir isso participando no processo de criação de um WCFruntime. Um exemplo de um comportamento de ponto de extremidade é o <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> propriedade, que permite que você especifique um endereço de escutando diferente que o endereço SOAP ou WSDL Web Services Description Language (). Para obter mais informações, consulte [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## <a name="defining-endpoints"></a>Definir pontos de extremidade  
 Você pode especificar o ponto de extremidade para um serviço usando código imperativa ou declarativamente por meio da configuração. Para obter mais informações, consulte [como: criar um ponto de extremidade de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) e [como: criar um ponto de extremidade de serviço em código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 Esta seção explica a finalidade de associações, pontos de extremidade e endereços; mostra como configurar uma associação e um ponto de extremidade; e demonstra como usar o `ClientVia` comportamento e `ListenUri` propriedade.  
  
 [Endereços](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 Descreve como os pontos de extremidade são resolvidos no WCF.  
  
 [Associações](../../../../docs/framework/wcf/feature-details/bindings.md)  
 Descreve como as associações são usadas para especificar o transporte, a codificação e detalhes de protocolo necessárias para clientes e serviços para se comunicar entre si.  
  
 [Contratos](../../../../docs/framework/wcf/feature-details/contracts.md)  
 Descreve como os contratos definem os métodos de um serviço.  
  
 [Como criar um ponto de extremidade de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Descreve como criar um ponto de extremidade de serviço na configuração.  
  
 [Como criar um ponto de extremidade de serviço no código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Descreve como criar um ponto de extremidade de serviço em código.  
  
 [Como usar o Svcutil.exe para validar o código de serviço compilado](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 Descreve como detectar erros nas configurações e implementações de serviço sem hospedar o serviço usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="see-also"></a>Consulte também  
 [Configurando serviços](../../../../docs/framework/wcf/configuring-services.md)  
 [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)

---
title: Associações do Windows Communcation Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: 1930826cf51d67ceb789e20920ca42f04d1adc1b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873066"
---
# <a name="windows-communication-foundation-bindings"></a>Associações do Windows Communication Foundation
Windows Communication Foundation (WCF) separa como o software para um aplicativo é escrito de como ele se comunica com outros softwares. Associações são usadas para especificar o transporte, codificação e detalhes do protocolo necessárias para clientes e serviços para se comunicar entre si. O WCF usa associações para gerar a representação subjacente de transmissão do ponto de extremidade, portanto, a maioria dos detalhes da associação deve ser aceito por terceiros que estão se comunicando. A maneira mais fácil de fazer isso é para clientes de um serviço usar a mesma associação que o ponto de extremidade para o serviço usa. Para obter mais informações sobre como fazer isso, consulte [usando associações para clientes e configurar o Windows Communication Foundation Services](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb).  
  
 Uma associação é composta por uma coleção de elementos de associação. Cada elemento descreve alguns aspectos de como o ponto de extremidade se comunica com clientes. Uma associação deve incluir pelo menos um elemento de associação de transporte, pelo menos um elemento de associação de codificação de mensagem (o que o elemento de associação de transporte pode fornecer por padrão), e qualquer número de outros elementos de associação de protocolo. O processo que cria um tempo de execução fora essa descrição permite que cada elemento de associação contribuir com código para esse tempo de execução.  
  
 O WCF fornece ligações que contêm as seleções comuns de elementos de associação. Eles podem ser usados com suas configurações padrão ou você pode modificar esses valores padrão acordo com os requisitos de usuário. Essas associações fornecidas pelo sistema têm propriedades que permitem o controle direto sobre os elementos de associação e suas configurações. Você pode facilmente trabalhar lado a lado com várias versões de uma associação, dando a cada versão da associação de seu próprio nome. Para obter detalhes, consulte [Configuring System-Provided associações](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Se você precisar de uma coleção de elementos de associação não fornecido por uma dessas associações fornecidas pelo sistema, você pode criar uma associação personalizada que consiste a coleção de elementos necessários de associação. Essas associações personalizadas são fáceis de criar e requer uma nova classe, mas eles não fornecem propriedades para controlar os elementos de associação ou suas configurações. Você pode acessar os elementos de associação e modificar suas configurações por meio da coleção em que os contém. Para obter detalhes, consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Configurando associações fornecidas pelo sistema](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Descreve como usar e modificar as associações que o WCF fornece para dar suporte a cenários comuns.  
  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 Descreve como definir associações do Windows Communication Foundation (WCF) para serviços e clientes imperativa no código e declarativamente usando a configuração.  
  
 [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Descreve o que um <xref:System.ServiceModel.Channels.CustomBinding> é e quando ele é usado.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)

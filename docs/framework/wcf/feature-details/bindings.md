---
title: Associações do Windows Communcation Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: e69cd500c50e9d76824d0e438a1af86f3a722c52
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780683"
---
# <a name="windows-communication-foundation-bindings"></a>Associações do Windows Communication Foundation
Windows Communication Foundation (WCF) separa como o software para um aplicativo é escrito de como ele se comunica com outros softwares. Associações são usadas para especificar o transporte, codificação e detalhes do protocolo necessárias para clientes e serviços para se comunicar entre si. O WCF usa associações para gerar a representação subjacente de transmissão do ponto de extremidade, portanto, a maioria dos detalhes da associação deve ser aceito por terceiros que estão se comunicando. A maneira mais fácil de fazer isso é para clientes de um serviço usar a mesma associação que o ponto de extremidade para o serviço usa. Para obter mais informações sobre como fazer isso, consulte [usando associações para configurar os serviços e clientes](~/docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
 Uma associação é composta por uma coleção de elementos de associação. Cada elemento descreve alguns aspectos de como o ponto de extremidade se comunica com clientes. Uma associação deve incluir pelo menos um elemento de associação de transporte, pelo menos um elemento de associação de codificação de mensagem (o que o elemento de associação de transporte pode fornecer por padrão), e qualquer número de outros elementos de associação de protocolo. O processo que cria um tempo de execução fora essa descrição permite que cada elemento de associação contribuir com código para esse tempo de execução.  
  
 O WCF fornece ligações que contêm as seleções comuns de elementos de associação. Eles podem ser usados com suas configurações padrão ou você pode modificar esses valores padrão acordo com os requisitos de usuário. Essas associações fornecidas pelo sistema têm propriedades que permitem o controle direto sobre os elementos de associação e suas configurações. Você pode facilmente trabalhar lado a lado com várias versões de uma associação, dando a cada versão da associação de seu próprio nome. Para obter detalhes, consulte [Configuring System-Provided associações](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Se você precisar de uma coleção de elementos de associação não fornecido por uma dessas associações fornecidas pelo sistema, você pode criar uma associação personalizada que consiste a coleção de elementos necessários de associação. Essas associações personalizadas são fáceis de criar e requer uma nova classe, mas eles não fornecem propriedades para controlar os elementos de associação ou suas configurações. Você pode acessar os elementos de associação e modificar suas configurações por meio da coleção em que os contém. Para obter detalhes, consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Configurando associações fornecidas pelo sistema](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Descreve como usar e modificar as associações que o WCF fornece para dar suporte a cenários comuns.  
  
 [Usando associações para configurar serviços e clientes](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 Descreve como definir associações do Windows Communication Foundation (WCF) para serviços e clientes imperativa no código e declarativamente usando a configuração.  
  
 [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Descreve o que um <xref:System.ServiceModel.Channels.CustomBinding> é e quando ele é usado.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)

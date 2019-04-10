---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 775f93f319c136a29a32ffaa1dfabc12ee081b29
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227503"
---
# <a name="bindingelementextensions"></a>\<bindingElementExtensions>
Esta seção permite o uso de um elemento de associação personalizada de um computador ou arquivo de configuração do aplicativo. Você pode adicionar um elemento de associação personalizado a essa coleção usando o `add` palavra-chave e a configuração o `type` atributo do elemento a ser uma extensão de elemento de associação, bem como o `name` de atributo para o elemento de associação personalizada.  
  
 As extensões de associação permitem ao usuário criar elementos de associação definidas pelo usuário para uso como parte de ligações personalizadas. Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.BindingElement>. No arquivo de configuração, o `bindingElementExtensions` seção é usada para definir um elemento de extensão.  
  
 O exemplo a seguir usa o `add` elemento, bem como o `name` atributo a ser adicionado a uma extensão de associação para o `bindingElementExtensions` seção do arquivo de configuração.  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingElementExtensions>
      <add name="udpTransport"
           type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingElementExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Para adicionar capacidades de configuração para o elemento, o usuário precisa para escrever e registrar um `bindingElementExtensionSection` elemento. Para obter mais informações sobre isso, consulte o <xref:System.Configuration> documentação.  
  
 Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de uma ligação personalizada, conforme mostrado no exemplo a seguir.  
  
```xml  
<customBinding>
  <binding name="test2">
    <udpTransport />
    <binaryMessageEncoding maxReadPoolSize="211"
                           maxWritePoolSize="2132"
                           maxSessionSize="3141" />
  </binding>
</customBinding>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)

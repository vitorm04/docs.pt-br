---
title: '&lt;bindingExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: f99b38ede66dbecb44f9e8e67f921943071672ca
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750769"
---
# <a name="ltbindingextensionsgt"></a>&lt;bindingExtensions&gt;
Esta seção permite o uso de uma associação definida pelo usuário de um computador ou arquivo de configuração do aplicativo. Você pode adicionar uma associação definida pelo usuário para esta coleção usando o `add` palavra-chave e a configuração de `type` atributo do elemento para uma associação definida pelo usuário, bem como a `name` atributo para o nome do usuário definido associação.  
  
 Extensões de associação permitem que o usuário crie associações definidas pelo usuário para uso como parte de uma configuração de ponto de extremidade. Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.Binding>.  
  
 O exemplo a seguir usa o `add` elemento, bem como o `name` atributo para adicionar uma extensão de associação para o `bindingElementExtensions` seção do arquivo de configuração.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingExtensions>  
           <add name="MyBinding" type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Para adicionar recursos de configuração para o elemento, o usuário precisa para escrever e registrar um `bindingSection` elemento. Para obter mais informações sobre isso, consulte o <xref:System.Configuration> documentação.  
  
 Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de um ponto de extremidade, conforme mostrado no exemplo a seguir.  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)

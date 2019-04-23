---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: ed55701e45d8580e37cf4776de6b9c5241e0548c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113029"
---
# <a name="bindingextensions"></a>\<bindingExtensions>
Esta seção permite o uso de uma associação definida pelo usuário de um computador ou arquivo de configuração do aplicativo. Você pode adicionar uma associação definida pelo usuário a essa coleção usando o `add` palavra-chave e a configuração o `type` atributo do elemento para uma associação definida pelo usuário, bem como o `name` atributo para o nome do usuário de associação definida pelo.  
  
 As extensões de associação permitem ao usuário crie associações definidas pelo usuário para uso como parte de uma configuração de ponto de extremidade. Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.Binding>.  
  
 O exemplo a seguir usa o `add` elemento, bem como o `name` atributo a ser adicionado a uma extensão de associação para o `bindingElementExtensions` seção do arquivo de configuração.  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Para adicionar capacidades de configuração para o elemento, o usuário precisa para escrever e registrar um `bindingSection` elemento. Para obter mais informações sobre isso, consulte o <xref:System.Configuration> documentação.  
  
 Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de um ponto de extremidade, conforme mostrado no exemplo a seguir.  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a>Consulte também

- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)

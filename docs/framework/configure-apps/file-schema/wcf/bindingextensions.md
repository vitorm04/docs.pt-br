---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 34ba198de33ae4aa1882d13f74bd2d538999a0c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919783"
---
# <a name="bindingextensions"></a>\<> bindingExtensions
Esta seção habilita o uso de uma associação definida pelo usuário de um computador ou arquivo de configuração de aplicativo. Você pode adicionar uma associação definida pelo usuário a essa coleção usando a `add` palavra-chave e definindo `type` o atributo do elemento como uma associação definida pelo usuário, bem como o `name` atributo para o nome da associação definida pelo usuário.  
  
 As extensões de associação permitem que o usuário crie associações definidas pelo usuário para uso como parte de uma configuração de ponto de extremidade. Programaticamente, uma extensão de associação é um tipo que implementa <xref:System.ServiceModel.Channels.Binding>a classe abstrata.  
  
 O exemplo a seguir usa `add` o elemento, bem como o `name` atributo para adicionar `bindingElementExtensions` uma extensão de associação à seção do arquivo de configuração.  
  
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
  
 Para adicionar habilidades de configuração ao elemento, o usuário precisa escrever e registrar um `bindingSection` elemento. Para obter mais informações sobre isso, consulte <xref:System.Configuration> a documentação.  
  
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

- [Estendendo associações](../../../wcf/extending/extending-bindings.md)

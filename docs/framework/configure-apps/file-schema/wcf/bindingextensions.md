---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039138"
---
# <a name="bindingextensions"></a>\<bindingExtensions >

Esta seção habilita o uso de uma associação definida pelo usuário de um computador ou arquivo de configuração de aplicativo. Você pode adicionar uma associação definida pelo usuário a essa coleção usando a palavra-chave `add` e definindo o atributo `type` do elemento como uma associação definida pelo usuário, bem como o atributo `name` como o nome da associação definida pelo usuário.

As extensões de associação permitem que o usuário crie associações definidas pelo usuário para uso como parte de uma configuração de ponto de extremidade. Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.Binding>.

O exemplo a seguir usa o elemento `add`, bem como o atributo `name` para adicionar uma extensão de associação à seção `bindingExtensions` do arquivo de configuração:

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

Para adicionar habilidades de configuração ao elemento, o usuário precisa escrever e registrar um `bindingSection` elemento. Para obter mais informações sobre isso, consulte a documentação do <xref:System.Configuration>.

Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de um ponto de extremidade, conforme mostrado no exemplo a seguir:

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

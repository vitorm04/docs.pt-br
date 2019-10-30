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
# <a name="bindingextensions"></a><span data-ttu-id="9333c-101">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="9333c-101">\<bindingExtensions></span></span>

<span data-ttu-id="9333c-102">Esta seção habilita o uso de uma associação definida pelo usuário de um computador ou arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9333c-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="9333c-103">Você pode adicionar uma associação definida pelo usuário a essa coleção usando a palavra-chave `add` e definindo o atributo `type` do elemento como uma associação definida pelo usuário, bem como o atributo `name` como o nome da associação definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9333c-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>

<span data-ttu-id="9333c-104">As extensões de associação permitem que o usuário crie associações definidas pelo usuário para uso como parte de uma configuração de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9333c-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="9333c-105">Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="9333c-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>

<span data-ttu-id="9333c-106">O exemplo a seguir usa o elemento `add`, bem como o atributo `name` para adicionar uma extensão de associação à seção `bindingExtensions` do arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="9333c-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingExtensions` section of the configuration file:</span></span>

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

<span data-ttu-id="9333c-107">Para adicionar habilidades de configuração ao elemento, o usuário precisa escrever e registrar um `bindingSection` elemento.</span><span class="sxs-lookup"><span data-stu-id="9333c-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="9333c-108">Para obter mais informações sobre isso, consulte a documentação do <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="9333c-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>

<span data-ttu-id="9333c-109">Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de um ponto de extremidade, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9333c-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example:</span></span>

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a><span data-ttu-id="9333c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9333c-110">See also</span></span>

- [<span data-ttu-id="9333c-111">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="9333c-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)

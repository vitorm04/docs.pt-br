---
title: '&lt;bindingExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 2b0e3fe417d76a08b7dd3295b68a179c3d9acefc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672881"
---
# <a name="ltbindingextensionsgt"></a><span data-ttu-id="98de3-102">&lt;bindingExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="98de3-102">&lt;bindingExtensions&gt;</span></span>
<span data-ttu-id="98de3-103">Esta seção permite o uso de uma associação definida pelo usuário de um computador ou arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98de3-103">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="98de3-104">Você pode adicionar uma associação definida pelo usuário a essa coleção usando o `add` palavra-chave e a configuração o `type` atributo do elemento para uma associação definida pelo usuário, bem como o `name` atributo para o nome do usuário de associação definida pelo.</span><span class="sxs-lookup"><span data-stu-id="98de3-104">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="98de3-105">As extensões de associação permitem ao usuário crie associações definidas pelo usuário para uso como parte de uma configuração de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="98de3-105">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="98de3-106">Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="98de3-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="98de3-107">O exemplo a seguir usa o `add` elemento, bem como o `name` atributo a ser adicionado a uma extensão de associação para o `bindingElementExtensions` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="98de3-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="98de3-108">Para adicionar capacidades de configuração para o elemento, o usuário precisa para escrever e registrar um `bindingSection` elemento.</span><span class="sxs-lookup"><span data-stu-id="98de3-108">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="98de3-109">Para obter mais informações sobre isso, consulte o <xref:System.Configuration> documentação.</span><span class="sxs-lookup"><span data-stu-id="98de3-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="98de3-110">Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de um ponto de extremidade, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="98de3-110">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="98de3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98de3-111">See also</span></span>
- [<span data-ttu-id="98de3-112">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="98de3-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)

---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: c323a65ace332d2ecd1e03330dddbe7ca17ff5bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69926362"
---
# \<bindingElementExtensions>
<span data-ttu-id="b3cfb-101">Esta seção habilita o uso de um elemento de associação personalizado de um computador ou arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b3cfb-101">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="b3cfb-102">Você pode adicionar um elemento de associação personalizado a essa coleção usando a `add` palavra-chave e definindo o `type` atributo do elemento como uma extensão de elemento de associação, bem como o `name` atributo para o elemento de associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="b3cfb-102">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="b3cfb-103">As extensões de associação permitem que o usuário crie elementos de associação definidos pelo usuário para uso como parte de associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="b3cfb-103">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="b3cfb-104">Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.BindingElement> .</span><span class="sxs-lookup"><span data-stu-id="b3cfb-104">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="b3cfb-105">No arquivo de configuração, a `bindingElementExtensions` seção é usada para definir um elemento de extensão.</span><span class="sxs-lookup"><span data-stu-id="b3cfb-105">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="b3cfb-106">O exemplo a seguir usa o `add` elemento, bem como o `name` atributo para adicionar uma extensão de associação à `bindingElementExtensions` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b3cfb-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="b3cfb-107">Para adicionar habilidades de configuração ao elemento, o usuário precisa escrever e registrar um `bindingElementExtensionSection` elemento.</span><span class="sxs-lookup"><span data-stu-id="b3cfb-107">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="b3cfb-108">Para obter mais informações sobre isso, consulte a <xref:System.Configuration> documentação.</span><span class="sxs-lookup"><span data-stu-id="b3cfb-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="b3cfb-109">Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de uma associação personalizada, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b3cfb-109">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3cfb-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3cfb-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="b3cfb-111">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="b3cfb-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)

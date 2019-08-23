---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: c323a65ace332d2ecd1e03330dddbe7ca17ff5bd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926362"
---
# <a name="bindingelementextensions"></a><span data-ttu-id="34765-101">\<bindingElementExtensions></span><span class="sxs-lookup"><span data-stu-id="34765-101">\<bindingElementExtensions></span></span>
<span data-ttu-id="34765-102">Esta seção habilita o uso de um elemento de associação personalizado de um computador ou arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34765-102">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="34765-103">Você pode adicionar um elemento de associação personalizado a essa coleção usando a `add` palavra-chave e definindo `type` o atributo do elemento como uma extensão de elemento de associação, bem como `name` o atributo para o elemento de associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="34765-103">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="34765-104">As extensões de associação permitem que o usuário crie elementos de associação definidos pelo usuário para uso como parte de associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="34765-104">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="34765-105">Programaticamente, uma extensão de associação é um tipo que implementa <xref:System.ServiceModel.Channels.BindingElement>a classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="34765-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="34765-106">No arquivo de configuração, a `bindingElementExtensions` seção é usada para definir um elemento de extensão.</span><span class="sxs-lookup"><span data-stu-id="34765-106">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="34765-107">O exemplo a seguir usa `add` o elemento, bem como o `name` atributo para adicionar `bindingElementExtensions` uma extensão de associação à seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="34765-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="34765-108">Para adicionar habilidades de configuração ao elemento, o usuário precisa escrever e registrar um `bindingElementExtensionSection` elemento.</span><span class="sxs-lookup"><span data-stu-id="34765-108">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="34765-109">Para obter mais informações sobre isso, consulte <xref:System.Configuration> a documentação.</span><span class="sxs-lookup"><span data-stu-id="34765-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="34765-110">Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de uma associação personalizada, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="34765-110">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34765-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34765-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="34765-112">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="34765-112">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)

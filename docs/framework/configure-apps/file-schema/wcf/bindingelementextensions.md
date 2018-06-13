---
title: '&lt;bindingElementExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: a93474a4f86fac2a6b211652e3ddc86901cf197f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747743"
---
# <a name="ltbindingelementextensionsgt"></a><span data-ttu-id="b5195-102">&lt;bindingElementExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="b5195-102">&lt;bindingElementExtensions&gt;</span></span>
<span data-ttu-id="b5195-103">Esta seção permite o uso de um elemento de associação personalizada de um computador ou arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5195-103">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="b5195-104">Você pode adicionar um elemento de associação personalizada para esta coleção usando o `add` palavra-chave e a configuração a `type` atributo do elemento para uma extensão de elemento de associação, bem como a `name` de atributo para o elemento de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="b5195-104">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="b5195-105">Extensões de associação permitem que o usuário criar elementos de associação definida pelo usuário para uso como parte de associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="b5195-105">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="b5195-106">Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b5195-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="b5195-107">No arquivo de configuração, o `bindingElementExtensions` seção é usada para definir um elemento de extensão.</span><span class="sxs-lookup"><span data-stu-id="b5195-107">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="b5195-108">O exemplo a seguir usa o `add` elemento, bem como o `name` atributo para adicionar uma extensão de associação para o `bindingElementExtensions` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b5195-108">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingElementExtensions>  
           <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingElementExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b5195-109">Para adicionar recursos de configuração para o elemento, o usuário precisa para escrever e registrar um `bindingElementExtensionSection` elemento.</span><span class="sxs-lookup"><span data-stu-id="b5195-109">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="b5195-110">Para obter mais informações sobre isso, consulte o <xref:System.Configuration> documentação.</span><span class="sxs-lookup"><span data-stu-id="b5195-110">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="b5195-111">Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de uma associação personalizada, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b5195-111">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5195-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5195-112">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [<span data-ttu-id="b5195-113">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="b5195-113">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)

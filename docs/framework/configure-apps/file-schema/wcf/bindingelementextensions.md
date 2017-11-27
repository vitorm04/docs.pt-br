---
title: '&lt;bindingElementExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b12752980e43944bb73f8adfde04bfb2d4dadf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingelementextensionsgt"></a><span data-ttu-id="0554f-102">&lt;bindingElementExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="0554f-102">&lt;bindingElementExtensions&gt;</span></span>
<span data-ttu-id="0554f-103">Esta seção permite o uso de um elemento de associação personalizada de um computador ou arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0554f-103">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="0554f-104">Você pode adicionar um elemento de associação personalizada para esta coleção usando o `add` palavra-chave e a configuração a `type` atributo do elemento para uma extensão de elemento de associação, bem como a `name` de atributo para o elemento de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0554f-104">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="0554f-105">Extensões de associação permitem que o usuário criar elementos de associação definida pelo usuário para uso como parte de associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="0554f-105">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="0554f-106">Programaticamente, uma extensão de associação é um tipo que implementa a classe abstrata <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="0554f-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="0554f-107">No arquivo de configuração, o `bindingElementExtensions` seção é usada para definir um elemento de extensão.</span><span class="sxs-lookup"><span data-stu-id="0554f-107">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="0554f-108">O exemplo a seguir usa o `add` elemento, bem como o `name` atributo para adicionar uma extensão de associação para o `bindingElementExtensions` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0554f-108">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="0554f-109">Para adicionar recursos de configuração para o elemento, o usuário precisa para escrever e registrar um `bindingElementExtensionSection` elemento.</span><span class="sxs-lookup"><span data-stu-id="0554f-109">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="0554f-110">Para obter mais informações sobre isso, consulte o <xref:System.Configuration> documentação.</span><span class="sxs-lookup"><span data-stu-id="0554f-110">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="0554f-111">Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada como parte de uma associação personalizada, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0554f-111">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0554f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0554f-112">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [<span data-ttu-id="0554f-113">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="0554f-113">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)

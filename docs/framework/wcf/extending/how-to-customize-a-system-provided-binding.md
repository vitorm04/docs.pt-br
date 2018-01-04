---
title: "Como personalizar uma associação fornecida pelo sistema"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9b048b5c57d174ac921793ee8677622b88a0595
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="219d6-102">Como personalizar uma associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="219d6-102">How to: Customize a System-Provided Binding</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="219d6-103">inclui várias associações fornecidas pelo sistema que permitem configurar algumas das propriedades dos elementos de associação subjacente, mas não todas as propriedades.</span><span class="sxs-lookup"><span data-stu-id="219d6-103"> includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="219d6-104">Este tópico demonstra como definir propriedades nos elementos de associação para criar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="219d6-104">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="219d6-105">como criar diretamente e configurar os elementos de associação sem usar as associações fornecidas pelo sistema, consulte [personalizado associações](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="219d6-105"> how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="219d6-106">Criando e estendendo associações personalizadas, consulte [estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="219d6-106"> creating and extending custom bindings, see [Extending Bindings](../../../../docs/framework/wcf/extending/extending-bindings.md).</span></span>  
  
 <span data-ttu-id="219d6-107">Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] todas as associações são compostas de *elementos de associação*.</span><span class="sxs-lookup"><span data-stu-id="219d6-107">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="219d6-108">Cada elemento de associação derivado de <xref:System.ServiceModel.Channels.BindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="219d6-108">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="219d6-109">Associações fornecidas pelo sistema, como <xref:System.ServiceModel.BasicHttpBinding> criar e configurar seus próprios elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="219d6-109">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="219d6-110">Este tópico mostra como acessar e alterar as propriedades desses elementos de associação, que não são diretamente expostos na associação; Especificamente, o <xref:System.ServiceModel.BasicHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="219d6-110">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="219d6-111">Os elementos de associação individuais estão contidos em uma coleção representada pelo <xref:System.ServiceModel.Channels.BindingElementCollection> de classe e são adicionados nesta ordem: fluxo de transações, sessão confiável, segurança, Duplex compostos, unidirecional, segurança de fluxo, codificação de mensagem e transporte.</span><span class="sxs-lookup"><span data-stu-id="219d6-111">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="219d6-112">Observe que nem todos os elementos de associação listados são necessários em cada associação.</span><span class="sxs-lookup"><span data-stu-id="219d6-112">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="219d6-113">Elementos de associação definida pelo usuário também podem ser exibido nesta coleção de elemento de associação e devem aparecer na mesma ordem conforme descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="219d6-113">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="219d6-114">Por exemplo, um transporte definido pelo usuário deve ser o último elemento da coleção de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="219d6-114">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="219d6-115">O <xref:System.ServiceModel.BasicHttpBinding> classe contém três elementos de associação:</span><span class="sxs-lookup"><span data-stu-id="219d6-115">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1.  <span data-ttu-id="219d6-116">Um elemento de associação ou opcional de segurança de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> classe usada com o transporte HTTP (segurança em nível de mensagem) ou o <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> classe, que é usado quando a camada de transporte fornece segurança, no caso do transporte HTTPS é usado.</span><span class="sxs-lookup"><span data-stu-id="219d6-116">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2.  <span data-ttu-id="219d6-117">Um codificador de mensagem necessário ou elemento de associação <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ou <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="219d6-117">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3.  <span data-ttu-id="219d6-118">Um transporte necessário ou elemento de associação <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, ou <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="219d6-118">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="219d6-119">Neste exemplo, podemos criar uma instância da associação, gerar um *associação personalizada* , examine os elementos de associação na associação personalizada e, ao encontrar o elemento de associação HTTP, vamos definir seu `KeepAliveEnabled` propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="219d6-119">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="219d6-120">O `KeepAliveEnabled` propriedade não é exposta diretamente no `BasicHttpBinding`, portanto, é necessário criar uma associação personalizada para navegar até o elemento de associação e defina essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="219d6-120">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="219d6-121">Para modificar uma associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="219d6-121">To modify a system-provided binding</span></span>  
  
1.  <span data-ttu-id="219d6-122">Criar uma instância do <xref:System.ServiceModel.BasicHttpBinding> de classe e defina o modo de segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="219d6-122">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  <span data-ttu-id="219d6-123">Criar uma associação personalizada de associação e criar um <xref:System.ServiceModel.Channels.BindingElementCollection> classe a partir de uma das propriedades da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="219d6-123">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  <span data-ttu-id="219d6-124">Percorra a <xref:System.ServiceModel.Channels.BindingElementCollection> classe, e quando você encontrar o <xref:System.ServiceModel.Channels.HttpTransportBindingElement> classe, defina seu <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="219d6-124">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="219d6-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="219d6-125">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="219d6-126">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="219d6-126">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)

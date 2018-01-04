---
title: "Como implementar uma propriedade de dependência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d63e66b2458fa4ff21a227bdc2898d97e5eb30f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="f3953-102">Como implementar uma propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="f3953-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="f3953-103">Este exemplo mostra como fazer uma [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] propriedade com um <xref:System.Windows.DependencyProperty> campo, portanto, definir uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="f3953-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="f3953-104">Ao definir suas próprias propriedades, se deseja dar suporte a muitos aspectos de funcionalidades do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], incluindo estilos, vinculação de dados, herança, animação e valores padrão, você deve implementá-las como uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="f3953-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3953-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3953-105">Example</span></span>  
 <span data-ttu-id="f3953-106">O exemplo a seguir registra pela primeira vez uma propriedade de dependência chamando o <xref:System.Windows.DependencyProperty.Register%2A> método.</span><span class="sxs-lookup"><span data-stu-id="f3953-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="f3953-107">O nome do campo de identificador que você usa para armazenar o nome e características da propriedade de dependência devem ser o <xref:System.Windows.DependencyProperty.Name%2A> escolhido para a propriedade de dependência como parte do <xref:System.Windows.DependencyProperty.Register%2A> chamada anexada pela cadeia de caracteres literal `Property`.</span><span class="sxs-lookup"><span data-stu-id="f3953-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="f3953-108">Por exemplo, se você registrar uma propriedade de dependência com um <xref:System.Windows.DependencyProperty.Name%2A> de `Location`, em seguida, o campo de identificador que você definir para a propriedade de dependência deve ser nomeado `LocationProperty`.</span><span class="sxs-lookup"><span data-stu-id="f3953-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="f3953-109">Neste exemplo, o nome da propriedade de dependência e sua [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] acessador é `State`; o campo identificador é `StateProperty`; o tipo da propriedade é <xref:System.Boolean>; e o tipo que registra a propriedade de dependência é `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="f3953-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="f3953-110">Se você não conseguir seguir esse padrão de nomenclatura, os designers poderão não relatar sua propriedade corretamente e determinados aspectos do aplicativo de estilo do sistema de propriedade poderão não se comportar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="f3953-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="f3953-111">Também é possível especificar metadados padrão para uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="f3953-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="f3953-112">Esse exemplo registra o valor padrão da propriedade de dependência `State` como `false`.</span><span class="sxs-lookup"><span data-stu-id="f3953-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="f3953-113">Para obter mais informações sobre como e por que implementar uma propriedade de dependência, em vez de simplesmente dar suporte a uma propriedade [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] com um campo privado, consulte a [Visão geral das propriedades de dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f3953-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3953-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3953-114">See Also</span></span>  
 [<span data-ttu-id="f3953-115">Visão geral das propriedades da dependência</span><span class="sxs-lookup"><span data-stu-id="f3953-115">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="f3953-116">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="f3953-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)

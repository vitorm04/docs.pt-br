---
title: "Como adicionar um tipo de proprietário para uma propriedade de dependência"
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
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b93934c8f84a7257445b530e27896342bdd73aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="a33a4-102">Como adicionar um tipo de proprietário para uma propriedade de dependência</span><span class="sxs-lookup"><span data-stu-id="a33a4-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="a33a4-103">Este exemplo mostra como adicionar uma classe como um proprietário de uma propriedade de dependência registrado para um tipo diferente.</span><span class="sxs-lookup"><span data-stu-id="a33a4-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="a33a4-104">Ao fazer isso, o leitor de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e o sistema de propriedade podem reconhecer a classe como um proprietário adicional da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a33a4-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="a33a4-105">Adicionar como proprietário opcionalmente permite que a classe de adição forneça os metadados específicos do tipo.</span><span class="sxs-lookup"><span data-stu-id="a33a4-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="a33a4-106">No exemplo a seguir, `StateProperty` é uma propriedade registrada pela classe `MyStateControl`.</span><span class="sxs-lookup"><span data-stu-id="a33a4-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="a33a4-107">A classe `UnrelatedStateControl` se adiciona como um proprietário do `StateProperty` usando o <xref:System.Windows.DependencyProperty.AddOwner%2A> método, especificamente usando a assinatura que permite que novos metadados para a propriedade de dependência conforme ela existe no tipo de adição.</span><span class="sxs-lookup"><span data-stu-id="a33a4-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="a33a4-108">Observe que você deve fornecer acessadores de [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] para a propriedade semelhantes ao exemplo mostrado no exemplo o [Implemente uma propriedade de dependência](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md), bem como expor novamente o identificador de propriedade de dependência na classe que está sendo adicionado como proprietário.</span><span class="sxs-lookup"><span data-stu-id="a33a4-108">Notice that you should provide [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] accessors for the property similar to the example shown in the [Implement a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="a33a4-109">Sem wrappers, a propriedade de dependência ainda funcionariam da perspectiva do acesso programático usando <xref:System.Windows.DependencyObject.GetValue%2A> ou <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="a33a4-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="a33a4-110">Mas, geralmente, você deseja corresponder esse comportamento de propriedade e sistema com os wrappers da propriedade [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a33a4-110">But you typically want to parallel this property-system behavior with the [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property wrappers.</span></span> <span data-ttu-id="a33a4-111">Os wrappers facilitam a definição da propriedade de dependência de forma programática e tornam possível definir as propriedades como atributos [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a33a4-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="a33a4-112">Para saber como substituir metadados padrão, consulte [Substituir metadados para uma propriedade de dependência](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span><span class="sxs-lookup"><span data-stu-id="a33a4-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a33a4-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a33a4-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="a33a4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a33a4-114">See Also</span></span>  
 [<span data-ttu-id="a33a4-115">Propriedades de dependência personalizada</span><span class="sxs-lookup"><span data-stu-id="a33a4-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="a33a4-116">Visão geral das propriedades da dependência</span><span class="sxs-lookup"><span data-stu-id="a33a4-116">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)

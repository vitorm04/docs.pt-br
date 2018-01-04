---
title: Como definir e referenciar um recurso
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173be3048f7bf082db2eef2ea21eb1e0319f9a43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-reference-a-resource"></a><span data-ttu-id="cf51b-102">Como definir e referenciar um recurso</span><span class="sxs-lookup"><span data-stu-id="cf51b-102">How to: Define and Reference a Resource</span></span>
<span data-ttu-id="cf51b-103">Esse exemplo mostra como definir um recurso e fazer referência a ele usando um atributo em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf51b-103">This example shows how to define a resource and reference it by using an attribute in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf51b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf51b-104">Example</span></span>  
 <span data-ttu-id="cf51b-105">O exemplo a seguir define dois tipos de recursos: um <xref:System.Windows.Media.SolidColorBrush> recursos e várias <xref:System.Windows.Style> recursos.</span><span class="sxs-lookup"><span data-stu-id="cf51b-105">The following example defines two types of resources: a <xref:System.Windows.Media.SolidColorBrush> resource, and several <xref:System.Windows.Style> resources.</span></span> <span data-ttu-id="cf51b-106">O <xref:System.Windows.Media.SolidColorBrush> recurso `MyBrush` é usada para fornecer o valor de várias propriedades que recebem um <xref:System.Windows.Media.Brush> tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="cf51b-106">The <xref:System.Windows.Media.SolidColorBrush> resource `MyBrush` is used to provide the value of several properties that each take a <xref:System.Windows.Media.Brush> type value.</span></span> <span data-ttu-id="cf51b-107">O <xref:System.Windows.Style> recursos `PageBackground`, `TitleText` e `Label` cada destino de um determinado tipo de controle.</span><span class="sxs-lookup"><span data-stu-id="cf51b-107">The <xref:System.Windows.Style> resources `PageBackground`, `TitleText` and `Label` each target a particular control type.</span></span> <span data-ttu-id="cf51b-108">Os estilos definem uma variedade de diferentes propriedades nos controles de destino, quando o recurso de estilo é referenciado por chave de recurso e é usado para definir o <xref:System.Windows.FrameworkElement.Style%2A> propriedade de vários elementos de controle específicos definidos em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf51b-108">The styles set a variety of different properties on the targeted controls, when that style resource is referenced by resource key and is used to set the <xref:System.Windows.FrameworkElement.Style%2A> property of several specific control elements defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="cf51b-109">Observe que uma das propriedades dentro dos setters do estilo `Label` também fazem referência ao recurso `MyBrush` definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="cf51b-109">Note that one of the properties within the setters of the `Label` style also references the `MyBrush` resource defined earlier.</span></span> <span data-ttu-id="cf51b-110">Essa é uma técnica comum, mas é importante lembrar que os recursos são analisados e inseridos em um dicionário de recursos na ordem em que são apresentados.</span><span class="sxs-lookup"><span data-stu-id="cf51b-110">This is a common technique, but it is important to remember that resources are parsed and entered into a resource dictionary in the order that they are given.</span></span> <span data-ttu-id="cf51b-111">Recursos também serão solicitados pela ordem encontrada no dicionário se você usar a [Extensão de marcação StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) para fazer referência a eles de dentro de outro recurso.</span><span class="sxs-lookup"><span data-stu-id="cf51b-111">Resources are also requested by the order found within the dictionary if you use the [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) to reference them from within another resource.</span></span> <span data-ttu-id="cf51b-112">Verifique se os recursos aos quais você fez referência são definidos anteriormente na coleção de recursos da qual esse recurso é solicitado.</span><span class="sxs-lookup"><span data-stu-id="cf51b-112">Make sure that any resource that you reference is defined earlier within the resources collection than where that resource is then requested.</span></span> <span data-ttu-id="cf51b-113">Se necessário, você pode contornar a ordem estrita de criação de referências de recursos usando uma [Extensão de marcação DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) para fazer referência ao recurso no tempo de execução, porém você sempre deve estar ciente que essa técnica DynamicResource traz consequências para o desempenho.</span><span class="sxs-lookup"><span data-stu-id="cf51b-113">If necessary, you can work around the strict creation order of resource refererences by using a [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) to reference the resource at runtime instead, but you should be aware that this DynamicResource technique has performance consequences.</span></span> <span data-ttu-id="cf51b-114">Para ver mais detalhes, consulte [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="cf51b-114">For details, see [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a><span data-ttu-id="cf51b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf51b-115">See Also</span></span>  
 [<span data-ttu-id="cf51b-116">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="cf51b-116">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="cf51b-117">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="cf51b-117">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)

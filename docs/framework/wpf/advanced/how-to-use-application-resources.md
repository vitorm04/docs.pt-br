---
title: Como usar recursos do aplicativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23f49481806d386bece1ad0634dd635c9eaf51f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="13792-102">Como usar recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="13792-102">How to: Use Application Resources</span></span>
<span data-ttu-id="13792-103">Esse exemplo demonstra como usar recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13792-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13792-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13792-104">Example</span></span>  
 <span data-ttu-id="13792-105">O exemplo a seguir mostra um arquivo de definição de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13792-105">The following example shows an application definition file.</span></span> <span data-ttu-id="13792-106">O arquivo de definição de aplicativo define uma seção de recursos (um valor para o <xref:System.Windows.Application.Resources%2A> propriedade).</span><span class="sxs-lookup"><span data-stu-id="13792-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="13792-107">Recursos definidos no nível do aplicativo podem ser acessados por todas as outras páginas que fazem parte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13792-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="13792-108">Nesse caso, o recurso é um estilo declarado.</span><span class="sxs-lookup"><span data-stu-id="13792-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="13792-109">Como um estilo completo que inclui um modelo de controle pode ser demorado, este exemplo omite o modelo de controle que é definido dentro do <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> setter de propriedade do estilo.</span><span class="sxs-lookup"><span data-stu-id="13792-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="13792-110">A exemplo a seguir mostra um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] página que referencia o recurso no nível do aplicativo que o exemplo anterior definiu.</span><span class="sxs-lookup"><span data-stu-id="13792-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="13792-111">O recurso referenciado usando um [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) que especifica a chave de recurso exclusivo para o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="13792-111">The resource is referenced by using a     [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="13792-112">Nenhum recurso com chave de "GelButton" é encontrado na página atual, portanto, o escopo da pesquisa de recursos para o recurso solicitado continua além da página atual e até os recursos de nível de aplicativo definidos.</span><span class="sxs-lookup"><span data-stu-id="13792-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="13792-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13792-113">See Also</span></span>  
 [<span data-ttu-id="13792-114">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="13792-114">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="13792-115">Visão geral do gerenciamento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="13792-115">Application Management Overview</span></span>](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [<span data-ttu-id="13792-116">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="13792-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)

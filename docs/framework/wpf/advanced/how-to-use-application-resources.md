---
title: Como usar recursos do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
ms.openlocfilehash: e4114466fa8016f8e31100d7a37038b0abfdccca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460260"
---
# <a name="how-to-use-application-resources"></a><span data-ttu-id="9729f-102">Como usar recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="9729f-102">How to: Use Application Resources</span></span>
<span data-ttu-id="9729f-103">Esse exemplo demonstra como usar recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9729f-103">This example shows how to use application resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9729f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9729f-104">Example</span></span>  
 <span data-ttu-id="9729f-105">O exemplo a seguir mostra um arquivo de definição de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9729f-105">The following example shows an application definition file.</span></span> <span data-ttu-id="9729f-106">O arquivo de definição de aplicativo define uma seção de recurso (um valor para a propriedade <xref:System.Windows.Application.Resources%2A>).</span><span class="sxs-lookup"><span data-stu-id="9729f-106">The application definition file defines a resource section (a value for the <xref:System.Windows.Application.Resources%2A> property).</span></span> <span data-ttu-id="9729f-107">Recursos definidos no nível do aplicativo podem ser acessados por todas as outras páginas que fazem parte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9729f-107">Resources defined at the application level can be accessed by all other pages that are part of the application.</span></span> <span data-ttu-id="9729f-108">Nesse caso, o recurso é um estilo declarado.</span><span class="sxs-lookup"><span data-stu-id="9729f-108">In this case, the resource is a declared style.</span></span> <span data-ttu-id="9729f-109">Como um estilo completo que inclui um modelo de controle pode ser longo, este exemplo omite o modelo de controle que é definido no setter da propriedade de <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> do estilo.</span><span class="sxs-lookup"><span data-stu-id="9729f-109">Because a complete style that includes a control template can be lengthy, this example omits the control template that is defined within the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property setter of the style.</span></span>  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 <span data-ttu-id="9729f-110">O exemplo a seguir mostra uma página [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que faz referência ao recurso de nível de aplicativo que o exemplo anterior definiu.</span><span class="sxs-lookup"><span data-stu-id="9729f-110">The following example shows a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page that references the application-level resource that the previous example defined.</span></span> <span data-ttu-id="9729f-111">O recurso é referenciado usando uma [extensão de marcação StaticResource](staticresource-markup-extension.md) que especifica a chave de recurso exclusiva para o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="9729f-111">The resource is referenced by using a     [StaticResource Markup Extension](staticresource-markup-extension.md) that specifies the unique resource key for the requested resource.</span></span> <span data-ttu-id="9729f-112">Nenhum recurso com chave de "GelButton" é encontrado na página atual, portanto, o escopo da pesquisa de recursos para o recurso solicitado continua além da página atual e até os recursos de nível de aplicativo definidos.</span><span class="sxs-lookup"><span data-stu-id="9729f-112">No resource with key of "GelButton" is found in the current page, so the resource lookup scope for the requested resource continues beyond the current page and into the defined application-level resources.</span></span>  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a><span data-ttu-id="9729f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9729f-113">See also</span></span>

- [<span data-ttu-id="9729f-114">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="9729f-114">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="9729f-115">Visão geral do gerenciamento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="9729f-115">Application Management Overview</span></span>](../app-development/application-management-overview.md)
- [<span data-ttu-id="9729f-116">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="9729f-116">How-to Topics</span></span>](resources-how-to-topics.md)

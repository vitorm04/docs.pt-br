---
title: Acessar objetos inseridos usando automação de interface de usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 110407079b37bce13bb6037d5755d2ef16a40214
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043961"
---
# <a name="access-embedded-objects-using-ui-automation"></a><span data-ttu-id="3325e-102">Acessar objetos inseridos usando automação de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="3325e-102">Access Embedded Objects Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="3325e-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="3325e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3325e-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3325e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="3325e-105">Este tópico mostra como [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o pode ser usado para expor objetos inseridos no conteúdo de um controle de texto.</span><span class="sxs-lookup"><span data-stu-id="3325e-105">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose objects embedded within the content of a text control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3325e-106">Os objetos inseridos podem incluir imagens, hiperlinks, botões, tabelas ou controles ActiveX.</span><span class="sxs-lookup"><span data-stu-id="3325e-106">Embedded objects can include images, hyperlinks, buttons, tables, or ActiveX controls.</span></span>  
  
 <span data-ttu-id="3325e-107">Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] objetos inseridos são considerados filhos do provedor de texto.</span><span class="sxs-lookup"><span data-stu-id="3325e-107">Embedded objects are considered children of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="3325e-108">Isso permite que eles sejam expostos por meio da mesma estrutura de árvore de automação da [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] interface do usuário que todos os outros elementos.</span><span class="sxs-lookup"><span data-stu-id="3325e-108">This allows them to be exposed through the same UI Automation tree structure as all other [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="3325e-109">A funcionalidade, por sua vez, é exposta por meio dos padrões de controle normalmente exigidos pelo tipo de controle objetos inseridos (por exemplo, já que os hiperlinks são baseados em texto, eles terão suporte <xref:System.Windows.Automation.TextPattern>).</span><span class="sxs-lookup"><span data-stu-id="3325e-109">Functionality, in turn, is exposed through the control patterns typically required by the embedded objects control type (for example, since hyperlinks are text-based they will support <xref:System.Windows.Automation.TextPattern>).</span></span>  
  
 <span data-ttu-id="3325e-110">![Objetos inseridos em um contêiner de texto.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span><span class="sxs-lookup"><span data-stu-id="3325e-110">![Embedded objects in a text container.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")</span></span>  
<span data-ttu-id="3325e-111">Um documento de exemplo com conteúdo textual ("você sabia?" ...) e dois objetos incorporados (uma imagem de um baixo e um hiperlink de texto), usados como um destino para os exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="3325e-111">A sample document with textual content, ("Did You Know?"…) and two embedded objects (a picture of a whale and a text hyperlink), used as a target for the code examples.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3325e-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3325e-112">Example</span></span>  
 <span data-ttu-id="3325e-113">O exemplo de código a seguir demonstra como recuperar uma coleção de objetos inseridos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dentro de um provedor de texto.</span><span class="sxs-lookup"><span data-stu-id="3325e-113">The following code example demonstrates how to retrieve a collection of embedded objects from within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="3325e-114">Para o documento de exemplo fornecido na introdução, dois objetos seriam retornados (um elemento Image e um elemento Text).</span><span class="sxs-lookup"><span data-stu-id="3325e-114">For the sample document provided in the introduction, two objects would be returned (an image element and a text element).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3325e-115">O elemento Image deve ter algum texto intrínseco associado a ele, que descreve a imagem, normalmente em <xref:System.Windows.Automation.AutomationElement.NameProperty> seu (por exemplo, "um" texto azul ".).</span><span class="sxs-lookup"><span data-stu-id="3325e-115">The image element should have some intrinsic text associated with it that describes the image, typically in its <xref:System.Windows.Automation.AutomationElement.NameProperty> (for example, "A blue whale.").</span></span> <span data-ttu-id="3325e-116">No entanto, quando um intervalo de texto que abrange o objeto de imagem é obtido, nem a imagem nem esse texto descritivo é retornado no fluxo de texto.</span><span class="sxs-lookup"><span data-stu-id="3325e-116">However, when a text range spanning the image object is obtained, neither the image nor this descriptive text is returned in the text stream.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a><span data-ttu-id="3325e-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3325e-117">Example</span></span>  
 <span data-ttu-id="3325e-118">O exemplo de código a seguir demonstra como obter um intervalo de texto de um objeto inserido [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dentro de um provedor de texto.</span><span class="sxs-lookup"><span data-stu-id="3325e-118">The following code example demonstrates how to obtain a text range from an embedded object within a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] text provider.</span></span> <span data-ttu-id="3325e-119">O intervalo de texto recuperado é um intervalo vazio no qual o ponto de extremidade inicial segue "...</span><span class="sxs-lookup"><span data-stu-id="3325e-119">The text range retrieved is an empty range where the starting endpoint follows "…</span></span> <span data-ttu-id="3325e-120">oceano. (espaço) "e o ponto de extremidade final precede o". "de fechamento que representa o hiperlink inserido (conforme mostrado pela imagem fornecida na introdução).</span><span class="sxs-lookup"><span data-stu-id="3325e-120">ocean.(space)" and the ending endpoint precedes the closing "." representing the embedded hyperlink (as shown by the image provided in the introduction).</span></span> <span data-ttu-id="3325e-121">Embora este seja um intervalo vazio, ele não é considerado um intervalo de degeneração porque tem um Span diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="3325e-121">Even though this is an empty range, it is not considered a degenerate range because it has a non-zero span.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3325e-122"><xref:System.Windows.Automation.TextPattern>pode recuperar um objeto inserido baseado em texto, como um hiperlink; no entanto, <xref:System.Windows.Automation.TextPattern> um secundário precisará ser obtido do objeto incorporado para expor sua funcionalidade completa.</span><span class="sxs-lookup"><span data-stu-id="3325e-122"><xref:System.Windows.Automation.TextPattern> can retrieve a text-based embedded object such as a hyperlink; however, a secondary <xref:System.Windows.Automation.TextPattern> will have to be obtained from the embedded object to expose its full functionality.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a><span data-ttu-id="3325e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3325e-123">See also</span></span>

- [<span data-ttu-id="3325e-124">Visão geral de TextPattern de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="3325e-124">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="3325e-125">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="3325e-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="3325e-126">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="3325e-126">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="3325e-127">Adicionar conteúdo a uma caixa de texto utilizando automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="3325e-127">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="3325e-128">Localizar e destacar texto usando automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="3325e-128">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)

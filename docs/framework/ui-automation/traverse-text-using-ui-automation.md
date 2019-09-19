---
title: Percorrer texto usando automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: b22da8575fdc4360601946c3cba136466a393895
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042559"
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="0705d-102">Percorrer texto usando automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0705d-102">Traverse Text Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="0705d-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="0705d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0705d-104">Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="0705d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0705d-105">Este tópico mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o para percorrer o conteúdo textual de um documento por <xref:System.Windows.Automation.Text.TextUnit> incrementos.</span><span class="sxs-lookup"><span data-stu-id="0705d-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0705d-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0705d-106">Example</span></span>  
 <span data-ttu-id="0705d-107">O exemplo de código a seguir demonstra como atravessar o conteúdo de um provedor de texto de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="0705d-107">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="0705d-108">O <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> método move os <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> pontos <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> de extremidade e de um <xref:System.Windows.Automation.Text.TextPatternRange>.</span><span class="sxs-lookup"><span data-stu-id="0705d-108">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="0705d-109">Normalmente, esse intervalo de texto é um intervalo de degeneramento que representa o ponto de inserção de texto.</span><span class="sxs-lookup"><span data-stu-id="0705d-109">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0705d-110">Como apenas objetos inseridos com base em texto são considerados parte do fluxo de texto, objetos incorporados, como imagens `Move` , não afetam ou seu valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="0705d-110">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="0705d-111">Qualquer método que <xref:System.Windows.Automation.Text.TextUnit> use será adiado para o <xref:System.Windows.Automation.Text.TextUnit> próximo maior suporte se <xref:System.Windows.Automation.Text.TextUnit> o dado não for suportado pelo controle.</span><span class="sxs-lookup"><span data-stu-id="0705d-111">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0705d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0705d-112">See also</span></span>

- [<span data-ttu-id="0705d-113">Visão geral de TextPattern de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0705d-113">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="0705d-114">Adicionar conteúdo a uma caixa de texto utilizando automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0705d-114">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="0705d-115">Localizar e destacar texto usando automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0705d-115">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="0705d-116">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="0705d-116">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="0705d-117">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="0705d-117">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)

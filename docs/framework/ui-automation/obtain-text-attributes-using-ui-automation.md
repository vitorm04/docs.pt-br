---
title: Obter atributos de texto usando automação de interface do usuário
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
ms.openlocfilehash: d4cb9d12e4e2d5a28744e3a238884616a6db8f68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214891"
---
# <a name="obtain-text-attributes-using-ui-automation"></a><span data-ttu-id="ee6e7-102">Obter atributos de texto usando automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="ee6e7-102">Obtain Text Attributes Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="ee6e7-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ee6e7-104">Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ee6e7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ee6e7-105">Este tópico mostra como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ao obter atributos de texto de um intervalo de texto.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to obtain text attributes from a text range.</span></span> <span data-ttu-id="ee6e7-106">Um intervalo de texto pode corresponder ao local atual do cursor (ou a seleção de degeneração) dentro de um documento, uma seleção contígua de texto, uma coleção de seleções de texto não contíguos ou todo o conteúdo textual de um documento.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-106">A text range can correspond to the current location of the caret (or degenerate selection) within a document, a contiguous selection of text, a collection of disjoint text selections, or the entire textual content of a document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee6e7-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ee6e7-107">Example</span></span>  
 <span data-ttu-id="ee6e7-108">O exemplo de código a seguir demonstra como obter o <xref:System.Windows.Automation.TextPattern.FontNameAttribute> de um intervalo de texto.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-108">The following code example demonstrates how to obtain the <xref:System.Windows.Automation.TextPattern.FontNameAttribute> from a text range.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <span data-ttu-id="ee6e7-109">O <xref:System.Windows.Automation.TextPattern> padrão de controle, em tandem com o <xref:System.Windows.Automation.Text.TextPatternRange> classe, dá suporte a atributos de texto básico, propriedades e métodos.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-109">The <xref:System.Windows.Automation.TextPattern> control pattern, in tandem with the <xref:System.Windows.Automation.Text.TextPatternRange> class, supports basic text attributes, properties, and methods.</span></span> <span data-ttu-id="ee6e7-110">Para a funcionalidade específica do controle que não é compatível com <xref:System.Windows.Automation.TextPattern> ou <xref:System.Windows.Automation.Text.TextPatternRange> o <xref:System.Windows.Automation.AutomationElement>, classe fornece métodos para um cliente de automação de interface do usuário acessar o modelo de objeto nativo correspondente.</span><span class="sxs-lookup"><span data-stu-id="ee6e7-110">For control-specific functionality that is not supported by <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange> the <xref:System.Windows.Automation.AutomationElement>, class provides methods for a UI Automation client to access the corresponding native object model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee6e7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee6e7-111">See also</span></span>

- [<span data-ttu-id="ee6e7-112">Visão geral de TextPattern de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="ee6e7-112">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="ee6e7-113">Acrescentar Conteúdo a um Text Box Utilizando Automação de IU</span><span class="sxs-lookup"><span data-stu-id="ee6e7-113">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="ee6e7-114">Encontre e destaque texto usando automação de interface de usuário</span><span class="sxs-lookup"><span data-stu-id="ee6e7-114">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="ee6e7-115">Visão Geral de Padrões de Controle de Automação de Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="ee6e7-115">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="ee6e7-116">Padrões de Controle para Clientes de Automação de IU</span><span class="sxs-lookup"><span data-stu-id="ee6e7-116">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="ee6e7-117">Obter detalhes de atributos de texto misto usando automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="ee6e7-117">Obtain Mixed Text Attribute Details Using UI Automation</span></span>](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)

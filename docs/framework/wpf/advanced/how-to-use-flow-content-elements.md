---
title: Como usar elementos de conteúdo de fluxo
ms.date: 03/30/2017
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
ms.openlocfilehash: 146a785ef4f6da650144ed6fc47633670304bde6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="e6ae7-102">Como usar elementos de conteúdo de fluxo</span><span class="sxs-lookup"><span data-stu-id="e6ae7-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="e6ae7-103">O exemplo a seguir demonstra o uso declarativo de vários elementos de fluxo de conteúdo e atributos associados.</span><span class="sxs-lookup"><span data-stu-id="e6ae7-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="e6ae7-104">Elementos e atributos demonstrados incluem:</span><span class="sxs-lookup"><span data-stu-id="e6ae7-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="e6ae7-105">Elemento <xref:System.Windows.Documents.Bold></span><span class="sxs-lookup"><span data-stu-id="e6ae7-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="e6ae7-106">Atributo <xref:System.Windows.Documents.Block.BreakPageBefore%2A></span><span class="sxs-lookup"><span data-stu-id="e6ae7-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="e6ae7-107">Atributo <xref:System.Windows.Documents.TextElement.FontSize%2A></span><span class="sxs-lookup"><span data-stu-id="e6ae7-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="e6ae7-108">Elemento <xref:System.Windows.Documents.Italic></span><span class="sxs-lookup"><span data-stu-id="e6ae7-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="e6ae7-109">Elemento <xref:System.Windows.Documents.LineBreak></span><span class="sxs-lookup"><span data-stu-id="e6ae7-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="e6ae7-110">Elemento <xref:System.Windows.Documents.List></span><span class="sxs-lookup"><span data-stu-id="e6ae7-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="e6ae7-111">Elemento <xref:System.Windows.Documents.ListItem></span><span class="sxs-lookup"><span data-stu-id="e6ae7-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="e6ae7-112">Elemento <xref:System.Windows.Documents.Paragraph></span><span class="sxs-lookup"><span data-stu-id="e6ae7-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="e6ae7-113">Elemento <xref:System.Windows.Documents.Run></span><span class="sxs-lookup"><span data-stu-id="e6ae7-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="e6ae7-114">Elemento <xref:System.Windows.Documents.Section></span><span class="sxs-lookup"><span data-stu-id="e6ae7-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="e6ae7-115">Elemento <xref:System.Windows.Documents.Span></span><span class="sxs-lookup"><span data-stu-id="e6ae7-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="e6ae7-116"><xref:System.Windows.Documents.Typography.Variants%2A> atributo (sobrescrito e subscrito)</span><span class="sxs-lookup"><span data-stu-id="e6ae7-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="e6ae7-117">Elemento <xref:System.Windows.Documents.Underline></span><span class="sxs-lookup"><span data-stu-id="e6ae7-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6ae7-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6ae7-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]

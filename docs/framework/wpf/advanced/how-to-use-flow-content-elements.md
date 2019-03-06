---
title: 'Como: Usar elementos de conteúdo de fluxo'
ms.date: 03/30/2017
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
ms.openlocfilehash: df591304736adf1725b2b4235149bd426fe15216
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368097"
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="b7ea4-102">Como: Usar elementos de conteúdo de fluxo</span><span class="sxs-lookup"><span data-stu-id="b7ea4-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="b7ea4-103">O exemplo a seguir demonstra o uso declarativo para vários elementos de conteúdo dinâmico e atributos associados.</span><span class="sxs-lookup"><span data-stu-id="b7ea4-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="b7ea4-104">Elementos e atributos demonstrados incluem:</span><span class="sxs-lookup"><span data-stu-id="b7ea4-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="b7ea4-105">Elemento <xref:System.Windows.Documents.Bold></span><span class="sxs-lookup"><span data-stu-id="b7ea4-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="b7ea4-106">Atributo <xref:System.Windows.Documents.Block.BreakPageBefore%2A></span><span class="sxs-lookup"><span data-stu-id="b7ea4-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="b7ea4-107">Atributo <xref:System.Windows.Documents.TextElement.FontSize%2A></span><span class="sxs-lookup"><span data-stu-id="b7ea4-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="b7ea4-108">Elemento <xref:System.Windows.Documents.Italic></span><span class="sxs-lookup"><span data-stu-id="b7ea4-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="b7ea4-109">Elemento <xref:System.Windows.Documents.LineBreak></span><span class="sxs-lookup"><span data-stu-id="b7ea4-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="b7ea4-110">Elemento <xref:System.Windows.Documents.List></span><span class="sxs-lookup"><span data-stu-id="b7ea4-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="b7ea4-111">Elemento <xref:System.Windows.Documents.ListItem></span><span class="sxs-lookup"><span data-stu-id="b7ea4-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="b7ea4-112">Elemento <xref:System.Windows.Documents.Paragraph></span><span class="sxs-lookup"><span data-stu-id="b7ea4-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="b7ea4-113">Elemento <xref:System.Windows.Documents.Run></span><span class="sxs-lookup"><span data-stu-id="b7ea4-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="b7ea4-114">Elemento <xref:System.Windows.Documents.Section></span><span class="sxs-lookup"><span data-stu-id="b7ea4-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="b7ea4-115">Elemento <xref:System.Windows.Documents.Span></span><span class="sxs-lookup"><span data-stu-id="b7ea4-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="b7ea4-116"><xref:System.Windows.Documents.Typography.Variants%2A> atributo (sobrescrito e subscrito)</span><span class="sxs-lookup"><span data-stu-id="b7ea4-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="b7ea4-117">Elemento <xref:System.Windows.Documents.Underline></span><span class="sxs-lookup"><span data-stu-id="b7ea4-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7ea4-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7ea4-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]

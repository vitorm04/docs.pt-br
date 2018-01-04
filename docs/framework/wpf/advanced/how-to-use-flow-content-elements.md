---
title: "Como usar elementos de conteúdo de fluxo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e637e114187d0864afe4211a45c346c1e5a449b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="d5bc1-102">Como usar elementos de conteúdo de fluxo</span><span class="sxs-lookup"><span data-stu-id="d5bc1-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="d5bc1-103">O exemplo a seguir demonstra o uso declarativo de vários elementos de fluxo de conteúdo e atributos associados.</span><span class="sxs-lookup"><span data-stu-id="d5bc1-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="d5bc1-104">Elementos e atributos demonstrados incluem:</span><span class="sxs-lookup"><span data-stu-id="d5bc1-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="d5bc1-105">Elemento <xref:System.Windows.Documents.Bold></span><span class="sxs-lookup"><span data-stu-id="d5bc1-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="d5bc1-106">Atributo <xref:System.Windows.Documents.Block.BreakPageBefore%2A></span><span class="sxs-lookup"><span data-stu-id="d5bc1-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="d5bc1-107">Atributo <xref:System.Windows.Documents.TextElement.FontSize%2A></span><span class="sxs-lookup"><span data-stu-id="d5bc1-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="d5bc1-108">Elemento <xref:System.Windows.Documents.Italic></span><span class="sxs-lookup"><span data-stu-id="d5bc1-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="d5bc1-109">Elemento <xref:System.Windows.Documents.LineBreak></span><span class="sxs-lookup"><span data-stu-id="d5bc1-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="d5bc1-110">Elemento <xref:System.Windows.Documents.List></span><span class="sxs-lookup"><span data-stu-id="d5bc1-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="d5bc1-111">Elemento <xref:System.Windows.Documents.ListItem></span><span class="sxs-lookup"><span data-stu-id="d5bc1-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="d5bc1-112">Elemento <xref:System.Windows.Documents.Paragraph></span><span class="sxs-lookup"><span data-stu-id="d5bc1-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="d5bc1-113">Elemento <xref:System.Windows.Documents.Run></span><span class="sxs-lookup"><span data-stu-id="d5bc1-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="d5bc1-114">Elemento <xref:System.Windows.Documents.Section></span><span class="sxs-lookup"><span data-stu-id="d5bc1-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="d5bc1-115">Elemento <xref:System.Windows.Documents.Span></span><span class="sxs-lookup"><span data-stu-id="d5bc1-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="d5bc1-116"><xref:System.Windows.Documents.Typography.Variants%2A>atributo (sobrescrito e subscrito)</span><span class="sxs-lookup"><span data-stu-id="d5bc1-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="d5bc1-117">Elemento <xref:System.Windows.Documents.Underline></span><span class="sxs-lookup"><span data-stu-id="d5bc1-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5bc1-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5bc1-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]

---
title: Como inserir um elemento em texto de forma programática
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Text Animation sample [WPF]
- elements [WPF], inserting into text
- inserting elements into text [WPF]
- TextPointer objects [WPF]
- text [WPF], inserting elements
ms.assetid: 97bd950a-25ac-4e42-a311-94b6420d4136
ms.openlocfilehash: 8eaf0c6a1e3ad3c64800f8611aba555110aa4c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543280"
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a><span data-ttu-id="3951f-102">Como inserir um elemento em texto de forma programática</span><span class="sxs-lookup"><span data-stu-id="3951f-102">How to: Insert an Element Into Text Programmatically</span></span>
<span data-ttu-id="3951f-103">O exemplo a seguir mostra como usar duas <xref:System.Windows.Documents.TextPointer> objetos para especificar um intervalo dentro do texto para aplicar um <xref:System.Windows.Documents.Span> elemento.</span><span class="sxs-lookup"><span data-stu-id="3951f-103">The following example shows how to use two <xref:System.Windows.Documents.TextPointer> objects to specify a range within text to apply a <xref:System.Windows.Documents.Span> element to.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3951f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3951f-104">Example</span></span>  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 <span data-ttu-id="3951f-105">A ilustração a seguir mostra a aparência de neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="3951f-105">The illustration below shows what this example looks like.</span></span>  
  
 <span data-ttu-id="3951f-106">![Um elemento Span aplicado a um intervalo de texto](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span><span class="sxs-lookup"><span data-stu-id="3951f-106">![A Span element applied to a range of text](../../../../docs/framework/wpf/advanced/media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3951f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3951f-107">See Also</span></span>  
 [<span data-ttu-id="3951f-108">Visão geral do documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="3951f-108">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)

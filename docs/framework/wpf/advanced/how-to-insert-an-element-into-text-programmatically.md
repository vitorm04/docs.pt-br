---
title: 'Como: Inserir um elemento em texto de forma programática'
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
ms.openlocfilehash: ea9850c8490ec37032d4565c6b3375e3116d4313
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169579"
---
# <a name="how-to-insert-an-element-into-text-programmatically"></a><span data-ttu-id="fb48e-102">Como: Inserir um elemento em texto de forma programática</span><span class="sxs-lookup"><span data-stu-id="fb48e-102">How to: Insert an Element Into Text Programmatically</span></span>
<span data-ttu-id="fb48e-103">O exemplo a seguir mostra como usar dois <xref:System.Windows.Documents.TextPointer> objetos para especificar um intervalo dentro do texto para aplicar um <xref:System.Windows.Documents.Span> elemento.</span><span class="sxs-lookup"><span data-stu-id="fb48e-103">The following example shows how to use two <xref:System.Windows.Documents.TextPointer> objects to specify a range within text to apply a <xref:System.Windows.Documents.Span> element to.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb48e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb48e-104">Example</span></span>  
 [!code-csharp[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/CSharp/InsertInlineIntoTextExample.cs#insertinlineintotextexamplewholepage)]
 [!code-vb[FlowMiscSnippets_procedural_snip#InsertInlineIntoTextExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowMiscSnippets_procedural_snip/VisualBasic/InsertInlineIntoTextExample.vb#insertinlineintotextexamplewholepage)]  
  
 <span data-ttu-id="fb48e-105">A ilustração a seguir mostra a aparência neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="fb48e-105">The illustration below shows what this example looks like.</span></span>  
  
 <span data-ttu-id="fb48e-106">![Um elemento Span aplicado a um intervalo de texto](./media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span><span class="sxs-lookup"><span data-stu-id="fb48e-106">![A Span element applied to a range of text](./media/flow-insertelementintotextprogrammatically.png "Flow_InsertElementIntoTextProgrammatically")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb48e-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb48e-107">See also</span></span>

- [<span data-ttu-id="fb48e-108">Visão geral do documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="fb48e-108">Flow Document Overview</span></span>](flow-document-overview.md)

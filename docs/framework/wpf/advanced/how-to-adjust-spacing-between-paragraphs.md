---
title: 'Como: Ajustar o espaçamento entre parágrafos'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367473"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="82854-102">Como: Ajustar o espaçamento entre parágrafos</span><span class="sxs-lookup"><span data-stu-id="82854-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="82854-103">Este exemplo mostra como ajustar ou eliminar o espaçamento entre parágrafos em conteúdo de fluxo.</span><span class="sxs-lookup"><span data-stu-id="82854-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="82854-104">No conteúdo de fluxo, o espaço extra que aparece entre parágrafos é o resultado de margens definidas destes parágrafos; Portanto, o espaçamento entre parágrafos pode ser controlado ajustando as margens daqueles parágrafos.</span><span class="sxs-lookup"><span data-stu-id="82854-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="82854-105">Para eliminar completamente o espaço extra entre dois parágrafos, defina as margens dos parágrafos para **0**.</span><span class="sxs-lookup"><span data-stu-id="82854-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="82854-106">Para obter o espacejamento uniforme entre parágrafos em todo <xref:System.Windows.Documents.FlowDocument>, use estilos para definir um valor de margem uniforme para todos os parágrafos no <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="82854-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="82854-107">É importante observar que as margens de dois parágrafos adjacentes "se recolherão" para a maior das margens, em vez de dobrar.</span><span class="sxs-lookup"><span data-stu-id="82854-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="82854-108">Portanto, se dois parágrafos adjacentes possuírem margens de 20 pixels e 40 pixels respectivamente, o espaço entre os parágrafos resultante será de 40 pixels, o maior dos dois valores de margem.</span><span class="sxs-lookup"><span data-stu-id="82854-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82854-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82854-109">Example</span></span>  
 <span data-ttu-id="82854-110">O exemplo a seguir utiliza estilos para configurar a margem para todos os <xref:System.Windows.Documents.Paragraph> elementos em um <xref:System.Windows.Documents.FlowDocument> à **0**, que elimina efetivamente o espaço extra entre parágrafos no <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="82854-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]

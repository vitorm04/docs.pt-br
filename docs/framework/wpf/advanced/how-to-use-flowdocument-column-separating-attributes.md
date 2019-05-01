---
title: 'Como: Usar atributos de separação da coluna de FlowDocument'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 27491b21da587fa198061ba52d8daed5d3f28de3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032027"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a><span data-ttu-id="4ec1e-102">Como: Usar atributos de separação da coluna de FlowDocument</span><span class="sxs-lookup"><span data-stu-id="4ec1e-102">How to: Use FlowDocument Column-Separating Attributes</span></span>
<span data-ttu-id="4ec1e-103">Este exemplo mostra como usar os recursos de separação da coluna de um <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="4ec1e-103">This example shows how to use the column-separating features of a <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ec1e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ec1e-104">Example</span></span>  
 <span data-ttu-id="4ec1e-105">O exemplo a seguir define uma <xref:System.Windows.Documents.FlowDocument>e define o <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, e <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributos.</span><span class="sxs-lookup"><span data-stu-id="4ec1e-105">The following example defines a <xref:System.Windows.Documents.FlowDocument>, and sets the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes.</span></span>  <span data-ttu-id="4ec1e-106">O <xref:System.Windows.Documents.FlowDocument> contém um único parágrafo do conteúdo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="4ec1e-106">The <xref:System.Windows.Documents.FlowDocument> contains a single paragraph of sample content.</span></span>  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 <span data-ttu-id="4ec1e-107">A figura a seguir mostra os efeitos do <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, e <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributos em um renderizado <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="4ec1e-107">The following figure shows the effects of the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes in a rendered <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 ![Captura de tela que mostra o atributo de coluna de dentro de FlowDocument.](./media/how-to-use-flowdocument-column-separating-attributes/flowdocument-intra-column.png)

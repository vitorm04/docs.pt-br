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
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Como: Usar atributos de separação da coluna de FlowDocument
Este exemplo mostra como usar os recursos de separação da coluna de um <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma <xref:System.Windows.Documents.FlowDocument>e define o <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, e <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributos.  O <xref:System.Windows.Documents.FlowDocument> contém um único parágrafo do conteúdo de exemplo.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 A figura a seguir mostra os efeitos do <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, e <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributos em um renderizado <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Captura de tela que mostra o atributo de coluna de dentro de FlowDocument.](./media/how-to-use-flowdocument-column-separating-attributes/flowdocument-intra-column.png)

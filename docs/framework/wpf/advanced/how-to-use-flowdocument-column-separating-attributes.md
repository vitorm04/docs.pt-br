---
title: "Como usar atributos de separação da coluna de FlowDocument"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 779dd7862ba9a6f0d8656decc3ca0791574033fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Como usar atributos de separação da coluna de FlowDocument
Este exemplo mostra como usar os recursos de separação de coluna de um <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma <xref:System.Windows.Documents.FlowDocument>e define o <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, e <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributos.  O <xref:System.Windows.Documents.FlowDocument> contém um único parágrafo do conteúdo de exemplo.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 A figura a seguir mostra os efeitos da <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, e <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributos em uma renderizado <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Captura de tela: FlowDocument Intra coluna](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")

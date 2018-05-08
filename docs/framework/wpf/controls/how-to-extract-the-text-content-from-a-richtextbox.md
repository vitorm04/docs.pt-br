---
title: Como extrair o conteúdo de texto de um RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
ms.openlocfilehash: 309fe15c76c17a79e11341f3a50c0bf5a7a2cc21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a>Como extrair o conteúdo de texto de um RichTextBox
Este exemplo mostra como extrair o conteúdo de um <xref:System.Windows.Controls.RichTextBox> como texto sem formatação.  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] código descreve um conjunto nomeado <xref:System.Windows.Controls.RichTextBox> controle com conteúdo simples.  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir implementa um método que utiliza um <xref:System.Windows.Controls.RichTextBox> como um argumento e retorna uma cadeia de caracteres que representa o conteúdo de texto sem formatação do <xref:System.Windows.Controls.RichTextBox>.  
  
 O método cria um novo <xref:System.Windows.Documents.TextRange> do conteúdo do <xref:System.Windows.Controls.RichTextBox>, usando o <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> e <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> para indicar o intervalo de conteúdo para extrair.  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> e <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> retornarem propriedades de cada um <xref:System.Windows.Documents.TextPointer>e estão acessíveis no FlowDocument subjacente que representa o conteúdo do <xref:System.Windows.Controls.RichTextBox>.  <xref:System.Windows.Documents.TextRange> Fornece uma propriedade de texto, que retorna as partes de texto sem formatação a <xref:System.Windows.Documents.TextRange> como uma cadeia de caracteres.  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)

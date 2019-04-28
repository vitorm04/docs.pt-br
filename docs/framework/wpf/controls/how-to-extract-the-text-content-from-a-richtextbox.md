---
title: 'Como: Extrair o conteúdo de texto de um RichTextBox'
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
ms.openlocfilehash: 220da59ec893528c99014e9ec95fb185c461b291
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001696"
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a>Como: Extrair o conteúdo de texto de um RichTextBox
Este exemplo mostra como extrair o conteúdo de um <xref:System.Windows.Controls.RichTextBox> como texto sem formatação.  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] código descreve uma nomeada <xref:System.Windows.Controls.RichTextBox> controle com conteúdo simples.  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir implementa um método que usa um <xref:System.Windows.Controls.RichTextBox> como um argumento e retorna uma cadeia de caracteres que representa o conteúdo de texto sem formatação a <xref:System.Windows.Controls.RichTextBox>.  
  
 O método cria uma nova <xref:System.Windows.Documents.TextRange> usando o conteúdo da <xref:System.Windows.Controls.RichTextBox>, usando o <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> e <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> para indicar o intervalo de extrair o conteúdo.  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> e <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> propriedades de cada retornam uma <xref:System.Windows.Documents.TextPointer>e estão acessíveis no FlowDocument subjacente que representa o conteúdo do <xref:System.Windows.Controls.RichTextBox>.  <xref:System.Windows.Documents.TextRange> Fornece uma propriedade de texto, que retorna as partes de texto sem formatação do <xref:System.Windows.Documents.TextRange> como uma cadeia de caracteres.  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de RichTextBox](richtextbox-overview.md)
- [Visão geral de TextBox](textbox-overview.md)

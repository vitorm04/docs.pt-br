---
title: 'Como: Abrir um arquivo solto em um controle RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: 8ffa4c9919788060dc4524e127c181ee8282e6f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768596"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Como: Abrir um arquivo solto em um controle RichTextBox
Na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], o <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, e <xref:System.Windows.Documents.FlowDocument> todos os controles têm funcionalidade interna de arrastar e soltar. A funcionalidade interna permite arrastar e soltar o texto dentro e entre os controles. No entanto, ela não habilita a abertura de um arquivo soltando-o no controle. Esses controles também marcam os eventos do tipo "arrastar e soltar" como manipulados. Como resultado, por padrão, não é possível adicionar seus próprios manipuladores de eventos para fornecer funcionalidade para abrir os arquivos soltos.  
  
 Para adicionar o tratamento adicional de eventos de arrastar e soltar nesses controles, use o <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> método para adicionar seus manipuladores de eventos para os eventos de arrastar e soltar. Defina o parâmetro `handledEventsToo` para `true` para que o manipulador especificado seja invocado para um evento roteados que já tenham sido marcado como manipulados por outro elemento na rota de evento.  
  
> [!TIP]
>  Você pode substituir a funcionalidade interna de arrastar e soltar dos <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, e <xref:System.Windows.Documents.FlowDocument> manipulando as versões prévias dos eventos de arrastar e soltar e marcando os eventos de visualização como manipulados. No entanto, isso desabilitará a funcionalidade interna do tipo "arrastar e soltar", o que não é recomendado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como adicionar manipuladores para o <xref:System.Windows.DragDrop.DragOver> e <xref:System.Windows.DragDrop.Drop> eventos em um <xref:System.Windows.Controls.RichTextBox>. Este exemplo usa o <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> método e define o `handledEventsToo` parâmetro para `true` para que os manipuladores de eventos serão invocados, embora o <xref:System.Windows.Controls.RichTextBox> marcar esses eventos como manipulados. O código nos manipuladores de eventos adiciona funcionalidade para abrir um arquivo de texto que é arrastado para o <xref:System.Windows.Controls.RichTextBox>.  
  
 Para testar este exemplo, arraste um arquivo de texto ou um arquivo do rich text format (RTF) do Windows Explorer para o <xref:System.Windows.Controls.RichTextBox>. O arquivo será aberto no <xref:System.Windows.Controls.RichTextBox>. Se você pressionar a tecla SHIFT antes de soltar o arquivo, ele será aberto como texto sem formatação.  
  
 [!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]

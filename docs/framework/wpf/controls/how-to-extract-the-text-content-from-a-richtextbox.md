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
ms.locfileid: "33553930"
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a><span data-ttu-id="955fe-102">Como extrair o conteúdo de texto de um RichTextBox</span><span class="sxs-lookup"><span data-stu-id="955fe-102">How to: Extract the Text Content from a RichTextBox</span></span>
<span data-ttu-id="955fe-103">Este exemplo mostra como extrair o conteúdo de um <xref:System.Windows.Controls.RichTextBox> como texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="955fe-103">This example shows how to extract the contents of a <xref:System.Windows.Controls.RichTextBox> as plain text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="955fe-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="955fe-104">Example</span></span>  
 <span data-ttu-id="955fe-105">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] código descreve um conjunto nomeado <xref:System.Windows.Controls.RichTextBox> controle com conteúdo simples.</span><span class="sxs-lookup"><span data-stu-id="955fe-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a><span data-ttu-id="955fe-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="955fe-106">Example</span></span>  
 <span data-ttu-id="955fe-107">O código a seguir implementa um método que utiliza um <xref:System.Windows.Controls.RichTextBox> como um argumento e retorna uma cadeia de caracteres que representa o conteúdo de texto sem formatação do <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="955fe-107">The following code implements a method that takes a <xref:System.Windows.Controls.RichTextBox> as an argument, and returns a string representing the plain text contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="955fe-108">O método cria um novo <xref:System.Windows.Documents.TextRange> do conteúdo do <xref:System.Windows.Controls.RichTextBox>, usando o <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> e <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> para indicar o intervalo de conteúdo para extrair.</span><span class="sxs-lookup"><span data-stu-id="955fe-108">The method creates a new <xref:System.Windows.Documents.TextRange> from the contents of the <xref:System.Windows.Controls.RichTextBox>, using the <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> to indicate the range of the contents to extract.</span></span>  <span data-ttu-id="955fe-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> e <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> retornarem propriedades de cada um <xref:System.Windows.Documents.TextPointer>e estão acessíveis no FlowDocument subjacente que representa o conteúdo do <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="955fe-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> properties each return a <xref:System.Windows.Documents.TextPointer>, and are accessible on the underlying FlowDocument that represents the contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  <span data-ttu-id="955fe-110"><xref:System.Windows.Documents.TextRange> Fornece uma propriedade de texto, que retorna as partes de texto sem formatação a <xref:System.Windows.Documents.TextRange> como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="955fe-110"><xref:System.Windows.Documents.TextRange> provides a Text property, which returns the plain text portions of the <xref:System.Windows.Documents.TextRange> as a string.</span></span>  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a><span data-ttu-id="955fe-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="955fe-111">See Also</span></span>  
 [<span data-ttu-id="955fe-112">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="955fe-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="955fe-113">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="955fe-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)

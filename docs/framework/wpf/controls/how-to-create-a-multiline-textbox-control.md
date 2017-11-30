---
title: Como criar um controle TextBox multilinha
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 244eb38ea47bbd7376c2f8c6f5b2609fbd9c4330
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="d0b95-102">Como criar um controle TextBox multilinha</span><span class="sxs-lookup"><span data-stu-id="d0b95-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="d0b95-103">Este exemplo mostra como usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir um <xref:System.Windows.Controls.TextBox> controle expandirá automaticamente para acomodar várias linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="d0b95-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0b95-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0b95-104">Example</span></span>  
 <span data-ttu-id="d0b95-105">Definindo o <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributo **Wrap** fará com que o texto passe para uma nova linha quando a borda do <xref:System.Windows.Controls.TextBox> controle é alcançado, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> controle para incluir espaço para uma nova linha, se é necessário.</span><span class="sxs-lookup"><span data-stu-id="d0b95-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="d0b95-106">Definindo o <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributo **true** faz com que uma nova linha seja inserida quando a tecla é pressionada, outra vez automaticamente expandindo o <xref:System.Windows.Controls.TextBox> para incluir espaço para uma nova linha, se necessário.</span><span class="sxs-lookup"><span data-stu-id="d0b95-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="d0b95-107">O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma barra de rolagem para o <xref:System.Windows.Controls.TextBox>, de modo que o conteúdo do <xref:System.Windows.Controls.TextBox> pode ser rolado por meio de se o <xref:System.Windows.Controls.TextBox> expande além do tamanho do quadro ou janela que inclui-lo.</span><span class="sxs-lookup"><span data-stu-id="d0b95-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="d0b95-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0b95-108">See Also</span></span>  
 <xref:System.Windows.TextWrapping>  
 [<span data-ttu-id="d0b95-109">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="d0b95-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="d0b95-110">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="d0b95-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)

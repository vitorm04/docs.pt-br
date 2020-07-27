---
title: Como criar um controle TextBox multilinha
description: Saiba como usar o XAML para definir um controle TextBox que se expande para acomodar várias linhas de texto em um aplicativo Windows Presentation Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166255"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="9234a-103">Como criar um controle TextBox multilinha</span><span class="sxs-lookup"><span data-stu-id="9234a-103">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="9234a-104">Este exemplo mostra como usar o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir um <xref:System.Windows.Controls.TextBox> controle que será expandido automaticamente para acomodar várias linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="9234a-104">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9234a-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9234a-105">Example</span></span>  
 <span data-ttu-id="9234a-106">A definição do <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributo a ser **encapsulado** fará com que o texto inserido seja quebrado em uma nova linha quando a borda do <xref:System.Windows.Controls.TextBox> controle for atingida, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> controle para incluir espaço para uma nova linha, se necessário.</span><span class="sxs-lookup"><span data-stu-id="9234a-106">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="9234a-107">A configuração do <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributo como **true** faz com que uma nova linha seja inserida quando a tecla de retorno é pressionada, mais uma vez automaticamente expandindo a sala de <xref:System.Windows.Controls.TextBox> inclusão para uma nova linha, se necessário.</span><span class="sxs-lookup"><span data-stu-id="9234a-107">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="9234a-108">O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma barra de rolagem ao <xref:System.Windows.Controls.TextBox> , para que o conteúdo do <xref:System.Windows.Controls.TextBox> possa ser rolado por meio de se <xref:System.Windows.Controls.TextBox> expandir para além do tamanho do quadro ou da janela que o inclui.</span><span class="sxs-lookup"><span data-stu-id="9234a-108">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="9234a-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="9234a-109">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="9234a-110">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="9234a-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="9234a-111">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="9234a-111">RichTextBox Overview</span></span>](richtextbox-overview.md)

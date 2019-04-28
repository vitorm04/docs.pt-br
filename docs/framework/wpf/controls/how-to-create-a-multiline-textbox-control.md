---
title: 'Como: Criar um controle TextBox multilinha'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 29fb4c9498fe163c36e71680242d3ef8cf98c089
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001267"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="67f53-102">Como: Criar um controle TextBox multilinha</span><span class="sxs-lookup"><span data-stu-id="67f53-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="67f53-103">Este exemplo mostra como usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir um <xref:System.Windows.Controls.TextBox> controle expandirá automaticamente para acomodar várias linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="67f53-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67f53-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="67f53-104">Example</span></span>  
 <span data-ttu-id="67f53-105">Definindo o <xref:System.Windows.Controls.TextBox.TextWrapping%2A> de atributo para **encapsular** fará com que o texto inserido quebre para uma nova linha quando a borda da <xref:System.Windows.Controls.TextBox> controle é alcançada, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> controle para incluir espaço para uma nova linha, se necessário.</span><span class="sxs-lookup"><span data-stu-id="67f53-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="67f53-106">Definindo o <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> de atributo para **verdadeira** faz com que uma nova linha seja inserida quando a tecla RETURN é pressionada, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> para incluir espaço para uma nova linha, se necessário.</span><span class="sxs-lookup"><span data-stu-id="67f53-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="67f53-107">O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma barra de rolagem para o <xref:System.Windows.Controls.TextBox>, de modo que o conteúdo da <xref:System.Windows.Controls.TextBox> poderá ser rolado se o <xref:System.Windows.Controls.TextBox> ultrapassar o tamanho do quadro ou janela que o contém.</span><span class="sxs-lookup"><span data-stu-id="67f53-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="67f53-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67f53-108">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="67f53-109">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="67f53-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="67f53-110">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="67f53-110">RichTextBox Overview</span></span>](richtextbox-overview.md)

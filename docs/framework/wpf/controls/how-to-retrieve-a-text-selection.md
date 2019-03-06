---
title: 'Como: Recuperar uma seleção de texto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: fdd0e3974964e141c4b65e1c8851f3c371a4d501
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357606"
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="44f65-102">Como: Recuperar uma seleção de texto</span><span class="sxs-lookup"><span data-stu-id="44f65-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="44f65-103">Este exemplo mostra uma maneira de usar o <xref:System.Windows.Controls.TextBox.SelectedText%2A> propriedade para recuperar o texto que o usuário tiver selecionado em um <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="44f65-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f65-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44f65-104">Example</span></span>  
 <span data-ttu-id="44f65-105">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo mostra a definição de uma <xref:System.Windows.Controls.TextBox> controle que contém algum texto para selecionar, e um <xref:System.Windows.Controls.Button> controle com um especificado <xref:System.Windows.Controls.Button.OnClick%2A> método.</span><span class="sxs-lookup"><span data-stu-id="44f65-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="44f65-106">Neste exemplo, um botão com um tipo de <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos é usado para recuperar a seleção de texto.</span><span class="sxs-lookup"><span data-stu-id="44f65-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="44f65-107">Quando o usuário clica no botão, o <xref:System.Windows.Controls.Button.OnClick%2A> método copia o texto selecionado na caixa de texto em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="44f65-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="44f65-108">As circunstâncias específicas pelas quais a seleção de texto é recuperada (clicando em um botão), bem como a ação tomada com essa seleção (copiar a seleção de texto para uma cadeia de caracteres), podem facilmente ser modificadas para acomodar uma grande variedade de cenários.</span><span class="sxs-lookup"><span data-stu-id="44f65-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="44f65-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44f65-109">Example</span></span>  
 <span data-ttu-id="44f65-110">O seguinte C# exemplo mostra uma <xref:System.Windows.Controls.Button.OnClick%2A> manipulador de eventos para o botão definido na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="44f65-110">The following C# example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="44f65-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44f65-111">See also</span></span>
- [<span data-ttu-id="44f65-112">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="44f65-112">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="44f65-113">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="44f65-113">RichTextBox Overview</span></span>](richtextbox-overview.md)

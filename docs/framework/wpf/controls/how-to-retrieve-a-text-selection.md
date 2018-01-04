---
title: "Como recuperar uma seleção de texto"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32be79811de4b8056449c2c6d6c53eca8cc063f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="5f3fc-102">Como recuperar uma seleção de texto</span><span class="sxs-lookup"><span data-stu-id="5f3fc-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="5f3fc-103">Este exemplo mostra uma maneira de usar o <xref:System.Windows.Controls.TextBox.SelectedText%2A> propriedade para recuperar o texto que o usuário selecionou em uma <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="5f3fc-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f3fc-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f3fc-104">Example</span></span>  
 <span data-ttu-id="5f3fc-105">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo mostra a definição de um <xref:System.Windows.Controls.TextBox> controle que contém algum texto para selecionar, e um <xref:System.Windows.Controls.Button> controle com um especificado <xref:System.Windows.Controls.Button.OnClick%2A> método.</span><span class="sxs-lookup"><span data-stu-id="5f3fc-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="5f3fc-106">Neste exemplo, um botão com um tipo de <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos é usado para recuperar a seleção de texto.</span><span class="sxs-lookup"><span data-stu-id="5f3fc-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="5f3fc-107">Quando o usuário clica no botão, o <xref:System.Windows.Controls.Button.OnClick%2A> método copia qualquer texto selecionado na caixa de texto em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5f3fc-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="5f3fc-108">As circunstâncias específicas pelas quais a seleção de texto é recuperada (clicando em um botão), bem como a ação tomada com essa seleção (copiar a seleção de texto para uma cadeia de caracteres), podem facilmente ser modificadas para acomodar uma grande variedade de cenários.</span><span class="sxs-lookup"><span data-stu-id="5f3fc-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="5f3fc-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f3fc-109">Example</span></span>  
 <span data-ttu-id="5f3fc-110">O seguinte [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] exemplo mostra um <xref:System.Windows.Controls.Button.OnClick%2A> manipulador de eventos para o botão definido no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="5f3fc-110">The following [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="5f3fc-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f3fc-111">See Also</span></span>  
 [<span data-ttu-id="5f3fc-112">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="5f3fc-112">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="5f3fc-113">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="5f3fc-113">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)

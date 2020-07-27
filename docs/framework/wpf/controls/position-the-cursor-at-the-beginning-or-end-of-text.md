---
title: Como posicionar o cursor no início ou no término do texto em um controle TextBox
description: Saiba como posicionar o cursor no início ou no final do conteúdo de texto de um controle de caixa de texto Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: afe8b11d032b5d61fa91cbf324f02cd8415d2ea8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167516"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="6d45e-103">Como posicionar o cursor no início ou no término do texto em um controle TextBox</span><span class="sxs-lookup"><span data-stu-id="6d45e-103">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="6d45e-104">Este exemplo mostra como posicionar o cursor no início ou no final do conteúdo de texto de um <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="6d45e-104">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d45e-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d45e-105">Example</span></span>  
 <span data-ttu-id="6d45e-106">O código a seguir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] descreve um <xref:System.Windows.Controls.TextBox> controle e atribui um nome a ele.</span><span class="sxs-lookup"><span data-stu-id="6d45e-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="6d45e-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d45e-107">Example</span></span>  
 <span data-ttu-id="6d45e-108">Para posicionar o cursor no início do conteúdo de um <xref:System.Windows.Controls.TextBox> controle, chame o <xref:System.Windows.Controls.TextBox.Select%2A> método e especifique a posição inicial da seleção de 0 e um comprimento de seleção de 0.</span><span class="sxs-lookup"><span data-stu-id="6d45e-108">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="6d45e-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d45e-109">Example</span></span>  
 <span data-ttu-id="6d45e-110">Para posicionar o cursor no final do conteúdo de um <xref:System.Windows.Controls.TextBox> controle, chame o <xref:System.Windows.Controls.TextBox.Select%2A> método e especifique a posição inicial da seleção igual ao comprimento do conteúdo do texto e um comprimento de seleção de 0.</span><span class="sxs-lookup"><span data-stu-id="6d45e-110">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="6d45e-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="6d45e-111">See also</span></span>

- [<span data-ttu-id="6d45e-112">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="6d45e-112">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="6d45e-113">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="6d45e-113">RichTextBox Overview</span></span>](richtextbox-overview.md)

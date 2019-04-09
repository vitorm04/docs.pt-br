---
title: 'Como: Posicionar o cursor no início ou no fim do texto em um controle TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: 3d7da5daf09e06938b8366e0f5f98a599cae4571
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186219"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="15f69-102">Como: Posicionar o cursor no início ou no fim do texto em um controle TextBox</span><span class="sxs-lookup"><span data-stu-id="15f69-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="15f69-103">Este exemplo mostra como posicionar o cursor no início ou no final do conteúdo de texto de um <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="15f69-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15f69-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15f69-104">Example</span></span>  
 <span data-ttu-id="15f69-105">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] código descreve um <xref:System.Windows.Controls.TextBox> controlar e atribui a ele um nome.</span><span class="sxs-lookup"><span data-stu-id="15f69-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="15f69-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15f69-106">Example</span></span>  
 <span data-ttu-id="15f69-107">Para posicionar o cursor no início do conteúdo de um <xref:System.Windows.Controls.TextBox> de controle, chame o <xref:System.Windows.Controls.TextBox.Select%2A> método e especifique a seleção de posição de início 0 e o comprimento da seleção de 0.</span><span class="sxs-lookup"><span data-stu-id="15f69-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="15f69-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15f69-108">Example</span></span>  
 <span data-ttu-id="15f69-109">Para posicionar o cursor no final do conteúdo de um <xref:System.Windows.Controls.TextBox> de controle, chame o <xref:System.Windows.Controls.TextBox.Select%2A> método e especificar a posição de início de seleção para o comprimento do conteúdo texto e o comprimento de seleção de 0.</span><span class="sxs-lookup"><span data-stu-id="15f69-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="15f69-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15f69-110">See also</span></span>

- [<span data-ttu-id="15f69-111">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="15f69-111">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="15f69-112">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="15f69-112">RichTextBox Overview</span></span>](richtextbox-overview.md)

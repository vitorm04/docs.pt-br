---
title: "Como posicionar o cursor no início ou no término do texto em um controle TextBox"
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
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df30adf232ad782999d8bdf52b1946f84785f98d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="8fe3d-102">Como posicionar o cursor no início ou no término do texto em um controle TextBox</span><span class="sxs-lookup"><span data-stu-id="8fe3d-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="8fe3d-103">Este exemplo mostra como posicionar o cursor no início ou no final do conteúdo do texto de um <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="8fe3d-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fe3d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8fe3d-104">Example</span></span>  
 <span data-ttu-id="8fe3d-105">O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] código descreve um <xref:System.Windows.Controls.TextBox> controlar e atribui a ela um nome.</span><span class="sxs-lookup"><span data-stu-id="8fe3d-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="8fe3d-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8fe3d-106">Example</span></span>  
 <span data-ttu-id="8fe3d-107">Para posicionar o cursor no início do conteúdo de um <xref:System.Windows.Controls.TextBox> de controle, chame o <xref:System.Windows.Controls.TextBox.Select%2A> método e especifique a seleção de posição de início 0 e o comprimento da seleção de 0.</span><span class="sxs-lookup"><span data-stu-id="8fe3d-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="8fe3d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8fe3d-108">Example</span></span>  
 <span data-ttu-id="8fe3d-109">Para posicionar o cursor no final do conteúdo de um <xref:System.Windows.Controls.TextBox> de controle, chame o <xref:System.Windows.Controls.TextBox.Select%2A> método e especificar a posição de início de seleção para o comprimento do conteúdo texto e um comprimento de seleção de 0.</span><span class="sxs-lookup"><span data-stu-id="8fe3d-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="8fe3d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fe3d-110">See Also</span></span>  
 [<span data-ttu-id="8fe3d-111">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="8fe3d-111">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="8fe3d-112">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8fe3d-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)

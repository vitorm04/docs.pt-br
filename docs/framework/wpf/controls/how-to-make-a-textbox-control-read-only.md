---
title: 'Como: Tornar um controle TextBox somente leitura'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 3784471020210f995c8bb0a377d56a2466d97da1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364518"
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="b5a5d-102">Como: Tornar um controle TextBox somente leitura</span><span class="sxs-lookup"><span data-stu-id="b5a5d-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="b5a5d-103">Este exemplo mostra como configurar um <xref:System.Windows.Controls.TextBox> controle por não permitir a entrada do usuário ou modificação.</span><span class="sxs-lookup"><span data-stu-id="b5a5d-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5a5d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5a5d-104">Example</span></span>  
 <span data-ttu-id="b5a5d-105">Para impedir que usuários modifiquem o conteúdo de um <xref:System.Windows.Controls.TextBox> , defina a <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atributo **verdadeiro**.</span><span class="sxs-lookup"><span data-stu-id="b5a5d-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="b5a5d-106">O <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atributo afeta somente a entrada do usuário, ela não afeta o texto definido na [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] descrição de uma <xref:System.Windows.Controls.TextBox> controle ou definida programaticamente através de texto o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b5a5d-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="b5a5d-107">O valor padrão de <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> está **falso**.</span><span class="sxs-lookup"><span data-stu-id="b5a5d-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a5d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5a5d-108">See also</span></span>
- [<span data-ttu-id="b5a5d-109">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="b5a5d-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="b5a5d-110">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="b5a5d-110">RichTextBox Overview</span></span>](richtextbox-overview.md)

---
title: Como definir o conteúdo de texto de um controle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 9b16f2d99295a28725255361b0be3ef7f4245fd2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459307"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="b236e-102">Como definir o conteúdo de texto de um controle TextBox</span><span class="sxs-lookup"><span data-stu-id="b236e-102">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="b236e-103">Este exemplo mostra como usar a propriedade <xref:System.Windows.Controls.TextBox.Text%2A> para definir o conteúdo de texto inicial de um controle de <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="b236e-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="b236e-104">Embora a versão [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do exemplo possa usar as marcas de `<TextBox.Text>` ao texto do conteúdo de cada botão <xref:System.Windows.Controls.TextBox>, não é necessário porque o <xref:System.Windows.Controls.TextBox> aplica o atributo <xref:System.Windows.Markup.ContentPropertyAttribute> à propriedade <xref:System.Windows.Controls.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="b236e-104">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="b236e-105">Para obter mais informações, consulte [visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b236e-105">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>

## <a name="example"></a><span data-ttu-id="b236e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b236e-106">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="b236e-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b236e-107">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="b236e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b236e-108">See also</span></span>

- [<span data-ttu-id="b236e-109">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="b236e-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="b236e-110">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="b236e-110">RichTextBox Overview</span></span>](richtextbox-overview.md)

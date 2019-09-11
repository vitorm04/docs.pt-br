---
title: 'Como: Definir o conteúdo de texto de um controle TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 2e2bc70b108991fd4e3c138bfac5bff942173e33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856116"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="60e17-102">Como: Definir o conteúdo de texto de um controle TextBox</span><span class="sxs-lookup"><span data-stu-id="60e17-102">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="60e17-103">Este exemplo mostra como usar a <xref:System.Windows.Controls.TextBox.Text%2A> propriedade para definir o conteúdo de texto inicial de um <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="60e17-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="60e17-104">Embora a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] versão do exemplo possa usar as `<TextBox.Text>` marcas em volta do <xref:System.Windows.Controls.TextBox> texto do conteúdo de cada botão, isso não é <xref:System.Windows.Controls.TextBox.Text%2A> necessário porque o <xref:System.Windows.Controls.TextBox> aplica o <xref:System.Windows.Markup.ContentPropertyAttribute> atributo à propriedade .</span><span class="sxs-lookup"><span data-stu-id="60e17-104">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="60e17-105">Para obter mais informações, consulte [visão geral de XAML (WPF)](../advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="60e17-105">For more information, see [XAML Overview (WPF)](../advanced/xaml-overview-wpf.md).</span></span>

## <a name="example"></a><span data-ttu-id="60e17-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60e17-106">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="60e17-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60e17-107">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="60e17-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60e17-108">See also</span></span>

- [<span data-ttu-id="60e17-109">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="60e17-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="60e17-110">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="60e17-110">RichTextBox Overview</span></span>](richtextbox-overview.md)

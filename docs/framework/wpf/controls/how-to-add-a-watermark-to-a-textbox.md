---
title: "Como: Adicionar uma marca-d'água a um TextBox"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: abe276c686d394ded13ec03f08deae65e4098d03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923570"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="0a153-102">Como: Adicionar uma marca-d'água a um TextBox</span><span class="sxs-lookup"><span data-stu-id="0a153-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="0a153-103">O exemplo a seguir mostra como auxiliar a usabilidade de <xref:System.Windows.Controls.TextBox> um exibindo uma imagem de tela <xref:System.Windows.Controls.TextBox> de fundo explicativa dentro do até que o usuário entradas de texto, no ponto em que a imagem é removida.</span><span class="sxs-lookup"><span data-stu-id="0a153-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="0a153-104">Além disso, a imagem de plano de fundo será restaurada novamente se o usuário remover sua entrada.</span><span class="sxs-lookup"><span data-stu-id="0a153-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="0a153-105">Consulte a ilustração abaixo.</span><span class="sxs-lookup"><span data-stu-id="0a153-105">See illustration below.</span></span>  
  
 <span data-ttu-id="0a153-106">![Uma caixa de texto com uma imagem de plano de fundo](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="0a153-106">![A TextBox with a background image](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a153-107">O motivo pelo qual uma imagem de plano de fundo é usada neste exemplo em vez <xref:System.Windows.Controls.TextBox.Text%2A> de simplesmente <xref:System.Windows.Controls.TextBox>manipular a propriedade de, é que uma imagem de plano de fundo não interfere na vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="0a153-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a153-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a153-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0a153-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a153-109">See also</span></span>

- [<span data-ttu-id="0a153-110">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="0a153-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="0a153-111">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0a153-111">RichTextBox Overview</span></span>](richtextbox-overview.md)

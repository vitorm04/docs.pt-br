---
title: Como adicionar uma marca d'água a um TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: 962d6958de0811863393f930d8672769a50e8265
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550053"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="21e6d-102">Como adicionar uma marca d'água a um TextBox</span><span class="sxs-lookup"><span data-stu-id="21e6d-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="21e6d-103">O exemplo a seguir mostra como auxiliar usabilidade de um <xref:System.Windows.Controls.TextBox> ao exibir uma imagem de plano de fundo explicativos dentro do <xref:System.Windows.Controls.TextBox> até que o usuário insere texto, no ponto em que a imagem será removida.</span><span class="sxs-lookup"><span data-stu-id="21e6d-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="21e6d-104">Além disso, a imagem de plano de fundo é restaurada novamente se o usuário remove suas entradas.</span><span class="sxs-lookup"><span data-stu-id="21e6d-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="21e6d-105">Consulte a ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="21e6d-105">See illustration below.</span></span>  
  
 <span data-ttu-id="21e6d-106">![Uma caixa de texto com uma imagem de plano de fundo](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="21e6d-106">![A TextBox with a background image](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21e6d-107">O motivo pelo qual uma imagem de plano de fundo é usada neste exemplo, em vez de simplesmente manipular o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade <xref:System.Windows.Controls.TextBox>, é que uma imagem de plano de fundo não interferirá na associação de dados.</span><span class="sxs-lookup"><span data-stu-id="21e6d-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21e6d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21e6d-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="21e6d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21e6d-109">See Also</span></span>  
 [<span data-ttu-id="21e6d-110">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="21e6d-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="21e6d-111">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="21e6d-111">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)

---
title: 'Como: Criar um botão que tenha uma imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: 5be928ac75ad727feabcde07ac0c6dc76ed130e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910943"
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="fd25d-102">Como: Criar um botão que tenha uma imagem</span><span class="sxs-lookup"><span data-stu-id="fd25d-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="fd25d-103">Este exemplo mostra como incluir uma imagem em um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="fd25d-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd25d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd25d-104">Example</span></span>  
 <span data-ttu-id="fd25d-105">O exemplo a seguir cria dois <xref:System.Windows.Controls.Button> controles.</span><span class="sxs-lookup"><span data-stu-id="fd25d-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="fd25d-106">Um <xref:System.Windows.Controls.Button> contém o texto e o outro contém uma imagem.</span><span class="sxs-lookup"><span data-stu-id="fd25d-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="fd25d-107">A imagem é em uma pasta chamada dados, que é uma subpasta da pasta do projeto de exemplo.</span><span class="sxs-lookup"><span data-stu-id="fd25d-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="fd25d-108">Quando um usuário clica o <xref:System.Windows.Controls.Button> que tem a imagem, o plano de fundo e o texto dos outros <xref:System.Windows.Controls.Button> alterar.</span><span class="sxs-lookup"><span data-stu-id="fd25d-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="fd25d-109">Este exemplo cria <xref:System.Windows.Controls.Button> controla usando marcação, mas usa o código para gravar o <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="fd25d-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="fd25d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd25d-110">See also</span></span>

- [<span data-ttu-id="fd25d-111">Controles</span><span class="sxs-lookup"><span data-stu-id="fd25d-111">Controls</span></span>](index.md)
- [<span data-ttu-id="fd25d-112">Biblioteca de controles</span><span class="sxs-lookup"><span data-stu-id="fd25d-112">Control Library</span></span>](control-library.md)

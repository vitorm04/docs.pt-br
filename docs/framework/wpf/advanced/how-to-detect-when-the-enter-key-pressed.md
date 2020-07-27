---
title: Como detectar quando a tecla Enter é pressionada
description: Detectar quando a tecla Enter é selecionada no teclado em Windows Presentation Foundation. Este exemplo consiste em XAML e um arquivo code-behind.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163180"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="99eeb-104">Como detectar quando a tecla Enter é pressionada</span><span class="sxs-lookup"><span data-stu-id="99eeb-104">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="99eeb-105">Este exemplo mostra como detectar quando a <xref:System.Windows.Input.Key.Enter> tecla é pressionada no teclado.</span><span class="sxs-lookup"><span data-stu-id="99eeb-105">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="99eeb-106">Este exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="99eeb-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99eeb-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99eeb-107">Example</span></span>  
 <span data-ttu-id="99eeb-108">Quando o usuário pressiona a <xref:System.Windows.Input.Key.Enter> tecla no <xref:System.Windows.Controls.TextBox> , a entrada na caixa de texto é exibida em outra área do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="99eeb-108">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="99eeb-109">O XAML a seguir cria a interface do usuário, que consiste em um <xref:System.Windows.Controls.StackPanel> , um <xref:System.Windows.Controls.TextBlock> e um <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="99eeb-109">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="99eeb-110">O code-behind a seguir cria o <xref:System.Windows.UIElement.KeyDown> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="99eeb-110">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="99eeb-111">Se a chave que é pressionada for a <xref:System.Windows.Input.Key.Enter> chave, uma mensagem será exibida no <xref:System.Windows.Controls.TextBlock> .</span><span class="sxs-lookup"><span data-stu-id="99eeb-111">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="99eeb-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="99eeb-112">See also</span></span>

- [<span data-ttu-id="99eeb-113">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="99eeb-113">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="99eeb-114">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="99eeb-114">Routed Events Overview</span></span>](routed-events-overview.md)

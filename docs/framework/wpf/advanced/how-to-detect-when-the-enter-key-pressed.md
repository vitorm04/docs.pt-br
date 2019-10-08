---
title: 'Como: Detectar quando a tecla Enter foi pressionada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004814"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="e22b8-102">Como: Detectar quando a tecla Enter foi pressionada</span><span class="sxs-lookup"><span data-stu-id="e22b8-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="e22b8-103">Este exemplo mostra como detectar quando a chave <xref:System.Windows.Input.Key.Enter> é pressionada no teclado.</span><span class="sxs-lookup"><span data-stu-id="e22b8-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="e22b8-104">Este exemplo consiste em um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="e22b8-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e22b8-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e22b8-105">Example</span></span>  
 <span data-ttu-id="e22b8-106">Quando o usuário pressiona a tecla <xref:System.Windows.Input.Key.Enter> no <xref:System.Windows.Controls.TextBox>, a entrada na caixa de texto é exibida em outra área do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e22b8-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="e22b8-107">O XAML a seguir cria a interface do usuário, que consiste em um <xref:System.Windows.Controls.StackPanel>, um <xref:System.Windows.Controls.TextBlock> e um <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e22b8-107">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="e22b8-108">O seguinte código por trás cria o manipulador de eventos <xref:System.Windows.UIElement.KeyDown>.</span><span class="sxs-lookup"><span data-stu-id="e22b8-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="e22b8-109">Se a chave que é pressionada for a chave <xref:System.Windows.Input.Key.Enter>, uma mensagem será exibida no <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="e22b8-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="e22b8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e22b8-110">See also</span></span>

- [<span data-ttu-id="e22b8-111">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="e22b8-111">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="e22b8-112">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="e22b8-112">Routed Events Overview</span></span>](routed-events-overview.md)

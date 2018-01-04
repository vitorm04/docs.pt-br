---
title: "Como detectar quando a tecla Enter é pressionada"
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
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21bb0dc8a38f8b49a4f5372c9dfc1e17e5114d6a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="a02fc-102">Como detectar quando a tecla Enter é pressionada</span><span class="sxs-lookup"><span data-stu-id="a02fc-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="a02fc-103">Este exemplo mostra como detectar quando o <xref:System.Windows.Input.Key.Enter> tecla é pressionada no teclado.</span><span class="sxs-lookup"><span data-stu-id="a02fc-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="a02fc-104">Este exemplo consiste em um [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de arquivo e um arquivo code-behind.</span><span class="sxs-lookup"><span data-stu-id="a02fc-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a02fc-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a02fc-105">Example</span></span>  
 <span data-ttu-id="a02fc-106">Quando o usuário pressiona o <xref:System.Windows.Input.Key.Enter> chave no <xref:System.Windows.Controls.TextBox>, a entrada na caixa de texto aparecerá em outra área do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a02fc-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="a02fc-107">O seguinte [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] cria a interface do usuário, que consiste em uma <xref:System.Windows.Controls.StackPanel>, um <xref:System.Windows.Controls.TextBlock>e um <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="a02fc-107">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="a02fc-108">O código a seguir cria o <xref:System.Windows.UIElement.KeyDown> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="a02fc-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="a02fc-109">Se a chave que é pressionada for o <xref:System.Windows.Input.Key.Enter> chave, será exibida uma mensagem no <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="a02fc-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="a02fc-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a02fc-110">See Also</span></span>  
 [<span data-ttu-id="a02fc-111">Visão geral da entrada</span><span class="sxs-lookup"><span data-stu-id="a02fc-111">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="a02fc-112">Visão geral de eventos roteados</span><span class="sxs-lookup"><span data-stu-id="a02fc-112">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)

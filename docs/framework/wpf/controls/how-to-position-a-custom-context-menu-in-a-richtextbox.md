---
title: 'Como: Posicionar um menu contextual em um RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
ms.openlocfilehash: 1f6e7255286d065eb26773d524a3147801933406
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727892"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="fe2ba-102">Como: Posicionar um menu contextual em um RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fe2ba-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="fe2ba-103">Este exemplo mostra como posicionar um menu de contexto personalizado para um <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="fe2ba-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="fe2ba-104">Quando você implementa um menu de contexto personalizado para um **RichTextBox**, você é responsável por lidar com o posicionamento do menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="fe2ba-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="fe2ba-105">Por padrão, um menu de contexto personalizado é aberto no centro do **RichTextBox**.</span><span class="sxs-lookup"><span data-stu-id="fe2ba-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe2ba-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe2ba-106">Example</span></span>  
 <span data-ttu-id="fe2ba-107">Para substituir o comportamento de posicionamento padrão, adicione um ouvinte para o <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> eventos.</span><span class="sxs-lookup"><span data-stu-id="fe2ba-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="fe2ba-108">O exemplo a seguir mostra como fazer isso programaticamente.</span><span class="sxs-lookup"><span data-stu-id="fe2ba-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="fe2ba-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe2ba-109">Example</span></span>  
 <span data-ttu-id="fe2ba-110">O exemplo a seguir mostra uma implementação correspondente <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> ouvinte de eventos.</span><span class="sxs-lookup"><span data-stu-id="fe2ba-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="fe2ba-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe2ba-111">See also</span></span>
- [<span data-ttu-id="fe2ba-112">Visão geral de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="fe2ba-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
- [<span data-ttu-id="fe2ba-113">Visão geral de TextBox</span><span class="sxs-lookup"><span data-stu-id="fe2ba-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)

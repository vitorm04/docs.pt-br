---
title: "Como: abrir uma caixa de diálogo"
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
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d318f35f8f009f0f2c77210ca8b6b29bedfb7619
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="2be44-102">Como: abrir uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="2be44-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="2be44-103">Este exemplo mostra como abrir uma caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="2be44-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2be44-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2be44-104">Example</span></span>  
 <span data-ttu-id="2be44-105">Uma caixa de diálogo é uma janela que é aberta instanciando <xref:System.Windows.Window> e chamar o <xref:System.Windows.Window.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="2be44-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="2be44-106"><xref:System.Windows.Window.ShowDialog%2A>Abre uma janela e não retorna até que a caixa de diálogo foi fechada.</span><span class="sxs-lookup"><span data-stu-id="2be44-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="2be44-107">Esse tipo de janela também é conhecido como um *modal* janela e restringe a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="2be44-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="2be44-108">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2be44-108">.NET Framework Security</span></span>  
 <span data-ttu-id="2be44-109">Chamando <xref:System.Windows.Window.ShowDialog%2A> requer a permissão para usar todas as janelas e eventos de entrada do usuário sem restrição.</span><span class="sxs-lookup"><span data-stu-id="2be44-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be44-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2be44-110">See Also</span></span>  
 [<span data-ttu-id="2be44-111">Retornar o resultado de uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="2be44-111">Return a Dialog Box Result</span></span>](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)

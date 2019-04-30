---
title: 'Como: Abrir uma caixa de diálogo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 70ac31285dd22244b4bd6ad0d188d182eb6e6264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947700"
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="59925-102">Como: Abrir uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="59925-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="59925-103">Este exemplo mostra como abrir uma caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="59925-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59925-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59925-104">Example</span></span>  
 <span data-ttu-id="59925-105">Uma caixa de diálogo é uma janela que é aberta instanciando <xref:System.Windows.Window> e chamar o <xref:System.Windows.Window.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="59925-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="59925-106"><xref:System.Windows.Window.ShowDialog%2A> Abre uma janela e não retorna até que a nova caixa de diálogo foi fechada.</span><span class="sxs-lookup"><span data-stu-id="59925-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="59925-107">Esse tipo de janela também é conhecido como um *modal* janela e restringe a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="59925-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="59925-108">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59925-108">.NET Framework Security</span></span>  
 <span data-ttu-id="59925-109">Chamar <xref:System.Windows.Window.ShowDialog%2A> requer a permissão para usar todas as janelas e eventos de entrada do usuário sem restrição.</span><span class="sxs-lookup"><span data-stu-id="59925-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59925-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59925-110">See also</span></span>

- [<span data-ttu-id="59925-111">Retornar o resultado de uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="59925-111">Return a Dialog Box Result</span></span>](how-to-return-a-dialog-box-result.md)

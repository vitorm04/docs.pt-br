---
title: 'Como: Retornar o resultado de uma caixa de diálogo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 5e3670006762bcd09634b29314ecf2d05b1a44da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968241"
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="d6def-102">Como: Retornar o resultado de uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="d6def-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="d6def-103">Este exemplo mostra como recuperar o resultado da caixa de diálogo para uma janela que é aberta <xref:System.Windows.Window.ShowDialog%2A>chamando.</span><span class="sxs-lookup"><span data-stu-id="d6def-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6def-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6def-104">Example</span></span>  
 <span data-ttu-id="d6def-105">Antes que uma caixa de diálogo seja <xref:System.Windows.Window.DialogResult%2A> fechada, sua propriedade deve ser <xref:System.Nullable%601> definida com um <xref:System.Boolean> que indica como o usuário fechou a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d6def-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="d6def-106">Esse valor é retornado pelo <xref:System.Windows.Window.ShowDialog%2A> para permitir que o código do cliente determine como a caixa de diálogo foi fechada e, consequentemente, como processar o resultado.</span><span class="sxs-lookup"><span data-stu-id="d6def-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6def-107"><xref:System.Windows.Window.DialogResult%2A>Só poderá ser definido se uma janela for aberta chamando <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="d6def-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="d6def-108">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d6def-108">.NET Framework Security</span></span>  
 <span data-ttu-id="d6def-109">Chamar <xref:System.Windows.Window.ShowDialog%2A> requer permissão para usar todos os eventos de entrada do usuário e do Windows sem restrição.</span><span class="sxs-lookup"><span data-stu-id="d6def-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>

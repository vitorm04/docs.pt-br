---
title: 'Como: Retornar o resultado de uma caixa de diálogo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: b574a5bbc08d947371837116915c2fc8c13ec81d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357762"
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="e50ec-102">Como: Retornar o resultado de uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="e50ec-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="e50ec-103">Este exemplo mostra como recuperar o resultado da caixa de diálogo para uma janela que é aberta chamando <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="e50ec-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e50ec-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e50ec-104">Example</span></span>  
 <span data-ttu-id="e50ec-105">Antes de uma caixa de diálogo é fechada, seu <xref:System.Windows.Window.DialogResult%2A> propriedade deve ser definida com um <xref:System.Nullable%601> <xref:System.Boolean> que indica como o usuário fechou a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="e50ec-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="e50ec-106">Esse valor é retornado por <xref:System.Windows.Window.ShowDialog%2A> para permitir que o código do cliente determinar como a caixa de diálogo foi fechada e, consequentemente, como processar o resultado.</span><span class="sxs-lookup"><span data-stu-id="e50ec-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e50ec-107"><xref:System.Windows.Window.DialogResult%2A> pode ser definido somente se uma janela foi aberta chamando <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="e50ec-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="e50ec-108">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e50ec-108">.NET Framework Security</span></span>  
 <span data-ttu-id="e50ec-109">Chamar <xref:System.Windows.Window.ShowDialog%2A> requer a permissão para usar todas as janelas e eventos de entrada do usuário sem restrição.</span><span class="sxs-lookup"><span data-stu-id="e50ec-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>

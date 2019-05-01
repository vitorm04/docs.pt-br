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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006701"
---
# <a name="how-to-return-a-dialog-box-result"></a>Como: Retornar o resultado de uma caixa de diálogo
Este exemplo mostra como recuperar o resultado da caixa de diálogo para uma janela que é aberta chamando <xref:System.Windows.Window.ShowDialog%2A>.  
  
## <a name="example"></a>Exemplo  
 Antes de uma caixa de diálogo é fechada, seu <xref:System.Windows.Window.DialogResult%2A> propriedade deve ser definida com um <xref:System.Nullable%601> <xref:System.Boolean> que indica como o usuário fechou a caixa de diálogo. Esse valor é retornado por <xref:System.Windows.Window.ShowDialog%2A> para permitir que o código do cliente determinar como a caixa de diálogo foi fechada e, consequentemente, como processar o resultado.  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A> pode ser definido somente se uma janela foi aberta chamando <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Chamar <xref:System.Windows.Window.ShowDialog%2A> requer a permissão para usar todas as janelas e eventos de entrada do usuário sem restrição.

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
# <a name="how-to-return-a-dialog-box-result"></a>Como: Retornar o resultado de uma caixa de diálogo
Este exemplo mostra como recuperar o resultado da caixa de diálogo para uma janela que é aberta <xref:System.Windows.Window.ShowDialog%2A>chamando.  
  
## <a name="example"></a>Exemplo  
 Antes que uma caixa de diálogo seja <xref:System.Windows.Window.DialogResult%2A> fechada, sua propriedade deve ser <xref:System.Nullable%601> definida com um <xref:System.Boolean> que indica como o usuário fechou a caixa de diálogo. Esse valor é retornado pelo <xref:System.Windows.Window.ShowDialog%2A> para permitir que o código do cliente determine como a caixa de diálogo foi fechada e, consequentemente, como processar o resultado.  
  
> [!NOTE]
> <xref:System.Windows.Window.DialogResult%2A>Só poderá ser definido se uma janela for aberta chamando <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Chamar <xref:System.Windows.Window.ShowDialog%2A> requer permissão para usar todos os eventos de entrada do usuário e do Windows sem restrição.

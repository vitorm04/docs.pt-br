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
ms.workload: dotnet
ms.openlocfilehash: 2e6201b7dbcc57a15583b7d95d6b603ab50e951a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-dialog-box"></a>Como: abrir uma caixa de diálogo
Este exemplo mostra como abrir uma caixa de diálogo.  
  
## <a name="example"></a>Exemplo  
 Uma caixa de diálogo é uma janela que é aberta instanciando <xref:System.Windows.Window> e chamar o <xref:System.Windows.Window.ShowDialog%2A> método. <xref:System.Windows.Window.ShowDialog%2A>Abre uma janela e não retorna até que a caixa de diálogo foi fechada. Esse tipo de janela também é conhecido como um *modal* janela e restringe a entrada do usuário.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Chamando <xref:System.Windows.Window.ShowDialog%2A> requer a permissão para usar todas as janelas e eventos de entrada do usuário sem restrição.  
  
## <a name="see-also"></a>Consulte também  
 [Retornar o resultado de uma caixa de diálogo](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)

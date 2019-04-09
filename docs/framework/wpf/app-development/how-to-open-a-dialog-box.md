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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084958"
---
# <a name="how-to-open-a-dialog-box"></a>Como: Abrir uma caixa de diálogo
Este exemplo mostra como abrir uma caixa de diálogo.  
  
## <a name="example"></a>Exemplo  
 Uma caixa de diálogo é uma janela que é aberta instanciando <xref:System.Windows.Window> e chamar o <xref:System.Windows.Window.ShowDialog%2A> método. <xref:System.Windows.Window.ShowDialog%2A> Abre uma janela e não retorna até que a nova caixa de diálogo foi fechada. Esse tipo de janela também é conhecido como um *modal* janela e restringe a entrada do usuário.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Chamar <xref:System.Windows.Window.ShowDialog%2A> requer a permissão para usar todas as janelas e eventos de entrada do usuário sem restrição.  
  
## <a name="see-also"></a>Consulte também

- [Retornar o resultado de uma caixa de diálogo](how-to-return-a-dialog-box-result.md)

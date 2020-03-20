---
title: 'Como: Exibir caixas de diálogo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
ms.openlocfilehash: 3625080c7c322e297a9de92e4f95a40c0caf3e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181967"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Como exibir caixas de diálogo para o Windows Forms
Você exibe uma caixa de diálogo da mesma forma que exibe qualquer outro formulário em um aplicativo. O formulário de inicialização é carregado automaticamente quando o aplicativo é executado. Para fazer aparecer um segundo formulário ou caixa de diálogo no aplicativo, escreva código para carregá-lo e exibi-lo. Da mesma forma, para fazer o formulário ou caixa de diálogo desaparecer, escreva código para descarregá-lo ou escondê-lo.  
  
### <a name="to-display-a-dialog-box"></a>Para exibir uma caixa de diálogo  
  
1. Navegue até o manipulador de eventos com o qual deseja abrir a caixa de diálogo. Isso pode acontecer quando um comando de menu é selecionado, quando um botão é clicado ou quando qualquer outro evento ocorre.  
  
2. No manipulador de eventos, adicione código para abrir a caixa de diálogo. Neste exemplo, um evento de clique de botão é usado para mostrar a caixa de diálogo:  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```

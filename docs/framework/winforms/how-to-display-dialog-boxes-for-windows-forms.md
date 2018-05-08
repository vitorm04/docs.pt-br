---
title: Como exibir caixas de diálogo para o Windows Forms
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
ms.openlocfilehash: a25fe86c4dde1fed69e192956d77615bf2a70402
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Como exibir caixas de diálogo para o Windows Forms
Você pode exibir uma caixa de diálogo da mesma maneira que você exibe qualquer outro formulário em um aplicativo. O formulário de inicialização carrega automaticamente quando o aplicativo é executado. Para fazer um segundo formulário ou a caixa de diálogo aparecer no aplicativo, escreva código para carregar e exibi-lo. Da mesma forma, para tornar o formulário ou a caixa de diálogo caixa desaparecer, escrever um código para descarregar ou ocultá-lo.  
  
### <a name="to-display-a-dialog-box"></a>Para exibir uma caixa de diálogo  
  
1.  Navegue para o manipulador de eventos com a qual você deseja abrir a caixa de diálogo. Isso pode acontecer quando um comando de menu é selecionado, quando um botão é clicado, ou quando qualquer outro evento ocorre.  
  
2.  No manipulador de eventos, adicione código para abrir a caixa de diálogo. Neste exemplo, um evento de clique do botão é usado para mostrar a caixa de diálogo:  
  
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

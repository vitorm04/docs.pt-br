---
title: 'Como: exibir caixas de diálogo'
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
ms.openlocfilehash: dd04a06eaa0dd7583ef2f72edb4cffa99aaaa60c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739467"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Como exibir caixas de diálogo para o Windows Forms
Você exibe uma caixa de diálogo da mesma maneira que exibe qualquer outro formulário em um aplicativo. O formulário de inicialização é carregado automaticamente quando o aplicativo é executado. Para fazer com que um segundo formulário ou caixa de diálogo apareça no aplicativo, escreva o código para carregá-lo e exibi-lo. Da mesma forma, para que o formulário ou a caixa de diálogo desapareçam, escreva o código para descarregar ou ocultá-lo.  
  
### <a name="to-display-a-dialog-box"></a>Para exibir uma caixa de diálogo  
  
1. Navegue até o manipulador de eventos com o qual você deseja abrir a caixa de diálogo. Isso pode acontecer quando um comando de menu é selecionado, quando um botão é clicado ou quando qualquer outro evento ocorre.  
  
2. No manipulador de eventos, adicione o código para abrir a caixa de diálogo. Neste exemplo, um evento de clique de botão é usado para mostrar a caixa de diálogo:  
  
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

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
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="0b534-102">Como exibir caixas de diálogo para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b534-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="0b534-103">Você exibe uma caixa de diálogo da mesma maneira que exibe qualquer outro formulário em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0b534-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="0b534-104">O formulário de inicialização é carregado automaticamente quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="0b534-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="0b534-105">Para fazer com que um segundo formulário ou caixa de diálogo apareça no aplicativo, escreva o código para carregá-lo e exibi-lo.</span><span class="sxs-lookup"><span data-stu-id="0b534-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="0b534-106">Da mesma forma, para que o formulário ou a caixa de diálogo desapareçam, escreva o código para descarregar ou ocultá-lo.</span><span class="sxs-lookup"><span data-stu-id="0b534-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="0b534-107">Para exibir uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="0b534-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="0b534-108">Navegue até o manipulador de eventos com o qual você deseja abrir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="0b534-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="0b534-109">Isso pode acontecer quando um comando de menu é selecionado, quando um botão é clicado ou quando qualquer outro evento ocorre.</span><span class="sxs-lookup"><span data-stu-id="0b534-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="0b534-110">No manipulador de eventos, adicione o código para abrir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="0b534-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="0b534-111">Neste exemplo, um evento de clique de botão é usado para mostrar a caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="0b534-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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

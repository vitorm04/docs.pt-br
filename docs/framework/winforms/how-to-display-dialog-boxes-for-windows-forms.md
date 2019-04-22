---
title: 'Como: exibir caixas de diálogo para o Windows Forms'
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
ms.openlocfilehash: b99f2273dae88faf86448da6e1d2986a83803abf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773812"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="7d71a-102">Como: exibir caixas de diálogo para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d71a-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="7d71a-103">Você pode exibir uma caixa de diálogo da mesma forma que você exibe qualquer outro formulário em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7d71a-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="7d71a-104">O formulário de inicialização carrega automaticamente quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="7d71a-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="7d71a-105">Para fazer um segundo formulário ou caixa de diálogo aparecer no aplicativo, escreva código para carregar e exibi-lo.</span><span class="sxs-lookup"><span data-stu-id="7d71a-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="7d71a-106">Da mesma forma, para tornar o formulário ou caixa de diálogo caixa desaparecer, escreva o código para descarregar ou ocultá-lo.</span><span class="sxs-lookup"><span data-stu-id="7d71a-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="7d71a-107">Para exibir uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="7d71a-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="7d71a-108">Navegue até o manipulador de eventos com a qual você deseja abrir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="7d71a-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="7d71a-109">Isso pode acontecer quando um comando de menu é selecionado, quando um botão é clicado ou quando qualquer outro evento ocorre.</span><span class="sxs-lookup"><span data-stu-id="7d71a-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="7d71a-110">No manipulador de eventos, adicione código para abrir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="7d71a-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="7d71a-111">Neste exemplo, um evento de clique de botão é usado para mostrar a caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="7d71a-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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

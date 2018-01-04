---
title: "Como exibir caixas de diálogo para o Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46e4d019bbd586c0ed46794f55c65da7bcc657f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="72b5b-102">Como exibir caixas de diálogo para o Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72b5b-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="72b5b-103">Você pode exibir uma caixa de diálogo da mesma maneira que você exibe qualquer outro formulário em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="72b5b-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="72b5b-104">O formulário de inicialização carrega automaticamente quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="72b5b-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="72b5b-105">Para fazer um segundo formulário ou a caixa de diálogo aparecer no aplicativo, escreva código para carregar e exibi-lo.</span><span class="sxs-lookup"><span data-stu-id="72b5b-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="72b5b-106">Da mesma forma, para tornar o formulário ou a caixa de diálogo caixa desaparecer, escrever um código para descarregar ou ocultá-lo.</span><span class="sxs-lookup"><span data-stu-id="72b5b-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="72b5b-107">Para exibir uma caixa de diálogo</span><span class="sxs-lookup"><span data-stu-id="72b5b-107">To display a dialog box</span></span>  
  
1.  <span data-ttu-id="72b5b-108">Navegue para o manipulador de eventos com a qual você deseja abrir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="72b5b-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="72b5b-109">Isso pode acontecer quando um comando de menu é selecionado, quando um botão é clicado, ou quando qualquer outro evento ocorre.</span><span class="sxs-lookup"><span data-stu-id="72b5b-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2.  <span data-ttu-id="72b5b-110">No manipulador de eventos, adicione código para abrir a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="72b5b-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="72b5b-111">Neste exemplo, um evento de clique do botão é usado para mostrar a caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="72b5b-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
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

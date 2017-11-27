---
title: "Como capturar a entrada do usuário de um PrintDialog em tempo de execução"
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
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c942cb5f005177b74dd25a9725b4990553adbb8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a><span data-ttu-id="911f6-102">Como capturar a entrada do usuário de um PrintDialog em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="911f6-102">How to: Capture User Input from a PrintDialog at Run Time</span></span>
<span data-ttu-id="911f6-103">Enquanto você pode definir opções de impressão em tempo de design, às vezes, convém alterar essas opções em tempo de execução, provavelmente devido a escolhas feitas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="911f6-103">While you can set options related to printing at design time, you will sometimes want to change these options at run time, most likely because of choices made by the user.</span></span> <span data-ttu-id="911f6-104">Você pode capturar a entrada do usuário para imprimir um documento usando o <xref:System.Windows.Forms.PrintDialog> e <xref:System.Drawing.Printing.PrintDocument> componentes.</span><span class="sxs-lookup"><span data-stu-id="911f6-104">You can capture user input for printing a document using the <xref:System.Windows.Forms.PrintDialog> and the <xref:System.Drawing.Printing.PrintDocument> components.</span></span>  
  
### <a name="to-change-print-options-programmatically"></a><span data-ttu-id="911f6-105">Para alterar opções de impressão programaticamente</span><span class="sxs-lookup"><span data-stu-id="911f6-105">To change print options programmatically</span></span>  
  
1.  <span data-ttu-id="911f6-106">Adicionar um <xref:System.Windows.Forms.PrintDialog> e um <xref:System.Drawing.Printing.PrintDocument> componente para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="911f6-106">Add a <xref:System.Windows.Forms.PrintDialog> and a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="911f6-107">Definir o <xref:System.Windows.Forms.PrintDialog.Document%2A> propriedade o <xref:System.Windows.Forms.PrintDialog> para o <xref:System.Drawing.Printing.PrintDocument> adicionado ao formulário.</span><span class="sxs-lookup"><span data-stu-id="911f6-107">Set the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> to the <xref:System.Drawing.Printing.PrintDocument> added to the form.</span></span>  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  <span data-ttu-id="911f6-108">Exibição de <xref:System.Windows.Forms.PrintDialog> componente usando o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="911f6-108">Display the <xref:System.Windows.Forms.PrintDialog> component by using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  <span data-ttu-id="911f6-109">Opções de impressão do usuário na caixa de diálogo serão copiadas para o <xref:System.Drawing.Printing.PrinterSettings> propriedade o <xref:System.Drawing.Printing.PrintDocument> componente.</span><span class="sxs-lookup"><span data-stu-id="911f6-109">The user's printing choices from the dialog will be copied to the <xref:System.Drawing.Printing.PrinterSettings> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911f6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="911f6-110">See Also</span></span>  
 [<span data-ttu-id="911f6-111">Como Imprimir um Arquivo de Texto de Várias Páginas nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="911f6-111">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="911f6-112">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="911f6-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)

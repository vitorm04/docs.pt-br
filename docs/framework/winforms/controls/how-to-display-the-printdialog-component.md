---
title: Como exibir o componente PrintDialog
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: d8765187522f8becf24b519434b7c170c1c755b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532181"
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="d9505-102">Como exibir o componente PrintDialog</span><span class="sxs-lookup"><span data-stu-id="d9505-102">How to: Display the PrintDialog Component</span></span>
<span data-ttu-id="d9505-103">O <xref:System.Windows.Forms.PrintDialog> componente é a caixa de diálogo de impressão padrão do Windows que muitos dos seus usuários estarão familiarizados com.</span><span class="sxs-lookup"><span data-stu-id="d9505-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="d9505-104">Como os usuários serão imediatamente confortáveis com ele, seria útil para você usar o <xref:System.Windows.Forms.PrintDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="d9505-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
### <a name="to-display-the-printdialog-component"></a><span data-ttu-id="d9505-105">Para exibir o componente PrintDialog</span><span class="sxs-lookup"><span data-stu-id="d9505-105">To display the PrintDialog component</span></span>  
  
-   <span data-ttu-id="d9505-106">Chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A> método de dentro do código do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d9505-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>  
  
     <span data-ttu-id="d9505-107">Assim que o componente for exibido, os usuários irá interagir com ele, definindo as propriedades do trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="d9505-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="d9505-108">Eles são salvos no <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` classe (e o <xref:System.Drawing.Printing.PageSettings> classe, se o usuário acessa o [componente PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) por meio de <xref:System.Windows.Forms.PrintDialog> componente) associado a esse trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="d9505-108">These are saved in the <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="d9505-109">Em seguida, você pode fazer chamadas para as propriedades que eles definidos para determinar as especificações do trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="d9505-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9505-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9505-110">See Also</span></span>  
 [<span data-ttu-id="d9505-111">Como Criar Trabalhos de Impressão Padrão dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9505-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="d9505-112">Como Capturar a Entrada do Usuário de um PrintDialog em Tempo de Execução</span><span class="sxs-lookup"><span data-stu-id="d9505-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [<span data-ttu-id="d9505-113">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="d9505-113">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="d9505-114">Componente PrintDialog</span><span class="sxs-lookup"><span data-stu-id="d9505-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [<span data-ttu-id="d9505-115">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9505-115">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="d9505-116">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9505-116">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)

---
title: Como exibir o componente PrintDialog
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 198ae75d407bd1837033a1cc186d84ff972fdc2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941564"
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="6c1c3-102">Como exibir o componente PrintDialog</span><span class="sxs-lookup"><span data-stu-id="6c1c3-102">How to display the PrintDialog component</span></span>

<span data-ttu-id="6c1c3-103">O <xref:System.Windows.Forms.PrintDialog> componente é a caixa de diálogo de impressão padrão do Windows que muitos dos seus usuários estarão familiarizados com.</span><span class="sxs-lookup"><span data-stu-id="6c1c3-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="6c1c3-104">Como os usuários serão imediatamente à vontade com ele, seria vantajoso para você usar o <xref:System.Windows.Forms.PrintDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="6c1c3-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>

## <a name="to-display-the-printdialog-component"></a><span data-ttu-id="6c1c3-105">Para exibir o componente PrintDialog</span><span class="sxs-lookup"><span data-stu-id="6c1c3-105">To display the PrintDialog component</span></span>

- <span data-ttu-id="6c1c3-106">Chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A> método de dentro do código do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c1c3-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>

     <span data-ttu-id="6c1c3-107">Quando o componente é exibido, os usuários interagirão com ele, definindo as propriedades do trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="6c1c3-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="6c1c3-108">Eles são salvos na <xref:System.Drawing.Printing.PrinterSettings> classe (e o <xref:System.Drawing.Printing.PageSettings> classe, se o usuário acessa o [componente PageSetupDialog](pagesetupdialog-component-windows-forms.md) por meio do <xref:System.Windows.Forms.PrintDialog> componente) associado a esse trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="6c1c3-108">These are saved in the  <xref:System.Drawing.Printing.PrinterSettings> class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="6c1c3-109">Em seguida, você pode fazer chamadas para as propriedades que eles definidos para determinar as especificações do trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="6c1c3-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c1c3-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c1c3-110">See also</span></span>

- [<span data-ttu-id="6c1c3-111">Como: Criar trabalhos de impressão padrão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c1c3-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="6c1c3-112">Como: Capturar a entrada do usuário de um PrintDialog em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6c1c3-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [<span data-ttu-id="6c1c3-113">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="6c1c3-113">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="6c1c3-114">Componente PrintDialog</span><span class="sxs-lookup"><span data-stu-id="6c1c3-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
- [<span data-ttu-id="6c1c3-115">Suporte à impressão nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c1c3-115">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="6c1c3-116">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c1c3-116">Windows Forms Controls</span></span>](index.md)
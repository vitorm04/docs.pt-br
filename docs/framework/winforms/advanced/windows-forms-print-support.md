---
title: Suporte à impressão no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708126"
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="71188-102">Suporte à impressão no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71188-102">Windows Forms Print Support</span></span>
<span data-ttu-id="71188-103">A impressão nos Windows Forms consiste principalmente em usar o [Componente PrintDocument](../controls/printdocument-component-windows-forms.md) para permitir que o usuário imprima e o [Controle PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md), o [Componente PrintDialog](../controls/printdialog-component-windows-forms.md) e o [Componente PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) para fornecer uma interface gráfica familiar aos usuários acostumados com o sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="71188-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="71188-104">Normalmente, você cria uma nova instância dos <xref:System.Drawing.Printing.PrintDocument> componente, definir as propriedades que descrevem o que imprimir usando o <xref:System.Drawing.Printing.PrinterSettings> e <xref:System.Drawing.Printing.PageSettings> classes e chame o <xref:System.Drawing.Printing.PrintDocument.Print%2A> método para efetivamente imprimir o documento.</span><span class="sxs-lookup"><span data-stu-id="71188-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="71188-105">Durante o curso da impressão de um aplicativo baseado em Windows, o <xref:System.Drawing.Printing.PrintDocument> componente mostrará uma caixa de diálogo de impressão de anulação para alertar os usuários para o fato de que a impressão está ocorrendo e permitir que o trabalho de impressão seja cancelado.</span><span class="sxs-lookup"><span data-stu-id="71188-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71188-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="71188-106">In This Section</span></span>  
 [<span data-ttu-id="71188-107">Como: Criar trabalhos de impressão padrão do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71188-107">How to: Create Standard Windows Forms Print Jobs</span></span>](how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="71188-108">Explica como usar o <xref:System.Drawing.Printing.PrintDocument> componente para imprimir a partir de um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="71188-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="71188-109">Como: Capturar a entrada do usuário de um PrintDialog em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="71188-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="71188-110">Explica como modificar opções de impressão selecionadas programaticamente usando o <xref:System.Windows.Forms.PrintDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="71188-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="71188-111">Como: Escolher as impressoras conectadas ao computador de um usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71188-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="71188-112">Descreve como alterar a impressora para imprimir usando o <xref:System.Windows.Forms.PrintDialog> componente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="71188-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="71188-113">Como: Imprimir elementos gráficos nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71188-113">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="71188-114">Descreve o envio de elementos gráficos para a impressora.</span><span class="sxs-lookup"><span data-stu-id="71188-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="71188-115">Como: Imprimir um arquivo de texto de várias páginas nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71188-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="71188-116">Descreve o envio de texto para a impressora.</span><span class="sxs-lookup"><span data-stu-id="71188-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="71188-117">Como: Trabalhos de impressão de formulários do Windows completa</span><span class="sxs-lookup"><span data-stu-id="71188-117">How to: Complete Windows Forms Print Jobs</span></span>](how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="71188-118">Explica como alertar usuários para a conclusão de um trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="71188-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="71188-119">Como: Imprimir um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="71188-119">How to: Print a Windows Form</span></span>](how-to-print-a-windows-form.md)  
 <span data-ttu-id="71188-120">Mostra como imprimir uma cópia do formulário atual.</span><span class="sxs-lookup"><span data-stu-id="71188-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="71188-121">Como: Imprimir no Windows Forms usando Visualizar impressão</span><span class="sxs-lookup"><span data-stu-id="71188-121">How to: Print in Windows Forms Using Print Preview</span></span>](how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="71188-122">Mostra como usar um <xref:System.Windows.Forms.PrintPreviewDialog> para imprimir um documento.</span><span class="sxs-lookup"><span data-stu-id="71188-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="71188-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="71188-123">Related Sections</span></span>  
 [<span data-ttu-id="71188-124">Componente PrintDocument</span><span class="sxs-lookup"><span data-stu-id="71188-124">PrintDocument Component</span></span>](../controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="71188-125">Explica o uso do <xref:System.Drawing.Printing.PrintDocument> componente.</span><span class="sxs-lookup"><span data-stu-id="71188-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="71188-126">Componente PrintDialog</span><span class="sxs-lookup"><span data-stu-id="71188-126">PrintDialog Component</span></span>](../controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="71188-127">Explica o uso do <xref:System.Windows.Forms.PrintDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="71188-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="71188-128">Controle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="71188-128">PrintPreviewDialog Control</span></span>](../controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="71188-129">Explica o uso do <xref:System.Windows.Forms.PrintPreviewDialog> controle.</span><span class="sxs-lookup"><span data-stu-id="71188-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="71188-130">Componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="71188-130">PageSetupDialog Component</span></span>](../controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="71188-131">Explica o uso do <xref:System.Windows.Forms.PageSetupDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="71188-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="71188-132">Descreve as classes no <xref:System.Drawing.Printing> namespace.</span><span class="sxs-lookup"><span data-stu-id="71188-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>

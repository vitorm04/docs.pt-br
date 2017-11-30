---
title: "Visão geral do componente PageSetupDialog (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 082dbff66c8a0f06635936011f802c99b88e41df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="9134b-102">Visão geral do componente PageSetupDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9134b-102">PageSetupDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="9134b-103">Windows Forms <xref:System.Windows.Forms.PageSetupDialog> componente é uma caixa de diálogo pré-configurado usada para definir os detalhes de página de impressão em aplicativos baseados no Windows.</span><span class="sxs-lookup"><span data-stu-id="9134b-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="9134b-104">Usá-lo em seu aplicativo do Windows como uma solução simples para os usuários para definir as preferências de página em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="9134b-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="9134b-105">Você pode habilitar os usuários definam ajustes de borda e margem, cabeçalhos e rodapés de páginas e orientação retrato ou paisagem.</span><span class="sxs-lookup"><span data-stu-id="9134b-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="9134b-106">Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="9134b-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="9134b-107">Propriedades e métodos de tecla</span><span class="sxs-lookup"><span data-stu-id="9134b-107">Key Properties and Methods</span></span>  
 <span data-ttu-id="9134b-108">Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9134b-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="9134b-109">Este componente tem propriedades que você pode definir relacionados como uma única página (<xref:System.Drawing.Printing.PrintDocument> classe) ou qualquer documento (<xref:System.Drawing.Printing.PageSettings> classe).</span><span class="sxs-lookup"><span data-stu-id="9134b-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="9134b-110">Além disso, o <xref:System.Windows.Forms.PageSetupDialog> componente pode ser usado para determinar as configurações de impressora específica, que são armazenadas na <xref:System.Drawing.Printing.PrinterSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="9134b-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>  
  
 <span data-ttu-id="9134b-111">Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.PageSetupDialog> componente aparece na bandeja de na parte inferior do Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="9134b-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9134b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9134b-112">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="9134b-113">Componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="9134b-113">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)

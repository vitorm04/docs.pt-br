---
title: Visão geral do componente PageSetupDialog
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744331"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="891f1-102">Visão geral do componente PageSetupDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="891f1-102">PageSetupDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="891f1-103">O componente Windows Forms <xref:System.Windows.Forms.PageSetupDialog> é uma caixa de diálogo pré-configurada usada para definir detalhes da página para impressão em aplicativos baseados no Windows.</span><span class="sxs-lookup"><span data-stu-id="891f1-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="891f1-104">Use-o em seu aplicativo baseado no Windows como uma solução simples para que os usuários definam preferências de página no lugar de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="891f1-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="891f1-105">Você pode permitir que os usuários definam ajustes de borda e margem, cabeçalhos e rodapés e orientação retrato ou paisagem.</span><span class="sxs-lookup"><span data-stu-id="891f1-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="891f1-106">Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="891f1-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="891f1-107">Propriedades e métodos de tecla</span><span class="sxs-lookup"><span data-stu-id="891f1-107">Key Properties and Methods</span></span>

<span data-ttu-id="891f1-108">Use o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="891f1-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="891f1-109">Esse componente tem propriedades que podem ser definidas com relação a uma única página (<xref:System.Drawing.Printing.PrintDocument> classe) ou a qualquer documento (<xref:System.Drawing.Printing.PageSettings> classe).</span><span class="sxs-lookup"><span data-stu-id="891f1-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="891f1-110">Além disso, o componente <xref:System.Windows.Forms.PageSetupDialog> pode ser usado para determinar configurações de impressora específicas, que são armazenadas na classe <xref:System.Drawing.Printing.PrinterSettings>.</span><span class="sxs-lookup"><span data-stu-id="891f1-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>

<span data-ttu-id="891f1-111">Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.PageSetupDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="891f1-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="891f1-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="891f1-112">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="891f1-113">Componente PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="891f1-113">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)

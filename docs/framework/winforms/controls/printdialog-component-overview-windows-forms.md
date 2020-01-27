---
title: Visão geral do componente PrintDialog
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728674"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="18af6-102">Visão geral do componente PrintDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="18af6-102">PrintDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="18af6-103">O componente [PrintDialog](printdialog-component-windows-forms.md) dos Windows Forms é uma caixa de diálogo pré-configurada usada para selecionar uma impressora, escolher as páginas a serem impressas e determinar outras configurações relacionadas à impressão em aplicativos baseados no Windows.</span><span class="sxs-lookup"><span data-stu-id="18af6-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="18af6-104">Use-o como uma solução simples para seleção de impressora e de configurações relacionadas à impressão em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="18af6-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="18af6-105">Você pode habilitar os usuários a imprimir muitas partes de seus documentos: imprimir tudo, imprimir um intervalo de páginas selecionadas ou uma seleção.</span><span class="sxs-lookup"><span data-stu-id="18af6-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="18af6-106">Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="18af6-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="18af6-107">O componente <xref:System.Windows.Forms.PrintDialog> herda da classe <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="18af6-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-component"></a><span data-ttu-id="18af6-108">Como trabalhar com o componente</span><span class="sxs-lookup"><span data-stu-id="18af6-108">Working with the Component</span></span>

<span data-ttu-id="18af6-109">Use o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="18af6-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="18af6-110">Esse componente tem propriedades relacionadas a um único trabalho de impressão (<xref:System.Drawing.Printing.PrintDocument> classe) ou às configurações de uma impressora individual (<xref:System.Drawing.Printing.PrinterSettings> classe).</span><span class="sxs-lookup"><span data-stu-id="18af6-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="18af6-111">Um deles, por sua vez, pode ser compartilhado por várias impressoras.</span><span class="sxs-lookup"><span data-stu-id="18af6-111">Either of these, in turn, may be shared by multiple printers.</span></span>

<span data-ttu-id="18af6-112">Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.PrintDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="18af6-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="18af6-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="18af6-113">See also</span></span>

- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="18af6-114">Componente PrintDialog</span><span class="sxs-lookup"><span data-stu-id="18af6-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)

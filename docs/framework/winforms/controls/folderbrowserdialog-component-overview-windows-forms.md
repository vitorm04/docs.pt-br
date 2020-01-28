---
title: Visão geral do componente FolderBrowserDialog
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: 8b017ba08ae4205e930ac00177c89a89fde17d3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745728"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="e72c9-102">Visão geral do componente FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e72c9-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="e72c9-103">O componente Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> é uma caixa de diálogo modal que é usada para procurar e selecionar pastas.</span><span class="sxs-lookup"><span data-stu-id="e72c9-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="e72c9-104">Novas pastas também podem ser criadas de dentro do componente <xref:System.Windows.Forms.FolderBrowserDialog>.</span><span class="sxs-lookup"><span data-stu-id="e72c9-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>

> [!NOTE]
> <span data-ttu-id="e72c9-105">Para selecionar arquivos, em vez de pastas, use o componente [OpenFileDialog](openfiledialog-component-windows-forms.md) .</span><span class="sxs-lookup"><span data-stu-id="e72c9-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>

<span data-ttu-id="e72c9-106">O componente <xref:System.Windows.Forms.FolderBrowserDialog> é exibido em tempo de execução usando o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="e72c9-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="e72c9-107">Defina a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> para determinar a pasta superior e todas as subpastas que aparecerão dentro do modo de exibição de árvore da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="e72c9-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="e72c9-108">Depois que a caixa de diálogo for exibida, você poderá usar a propriedade <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> para obter o caminho da pasta que foi selecionada.</span><span class="sxs-lookup"><span data-stu-id="e72c9-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>

<span data-ttu-id="e72c9-109">Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.FolderBrowserDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e72c9-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="e72c9-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="e72c9-110">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="e72c9-111">Como escolher pastas com o componente FolderBrowserDialog dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e72c9-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="e72c9-112">Componente FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="e72c9-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)

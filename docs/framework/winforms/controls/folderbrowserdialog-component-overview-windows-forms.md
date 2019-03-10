---
title: Visão geral do componente FolderBrowserDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: d08eb456ea2d2d3b805d3df7e0e79b26ea7d415e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708243"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="a5ced-102">Visão geral do componente FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a5ced-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="a5ced-103">Os formulários do Windows <xref:System.Windows.Forms.FolderBrowserDialog> componente é uma caixa de diálogo modal que é usada para procurar e selecionar pastas.</span><span class="sxs-lookup"><span data-stu-id="a5ced-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="a5ced-104">Novas pastas também podem ser criadas de dentro do <xref:System.Windows.Forms.FolderBrowserDialog> componente.</span><span class="sxs-lookup"><span data-stu-id="a5ced-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5ced-105">Para selecionar arquivos, em vez de pastas, use o [OpenFileDialog](openfiledialog-component-windows-forms.md) componente.</span><span class="sxs-lookup"><span data-stu-id="a5ced-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>  
  
 <span data-ttu-id="a5ced-106">O <xref:System.Windows.Forms.FolderBrowserDialog> componente é exibido em tempo de execução usando o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a5ced-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="a5ced-107">Defina o <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> propriedade para determinar a pasta principal e todas as subpastas que aparecerão na exibição de árvore da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a5ced-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="a5ced-108">Depois que a caixa de diálogo tenha sido mostrada, você pode usar o <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> propriedade para obter o caminho da pasta que foi selecionado.</span><span class="sxs-lookup"><span data-stu-id="a5ced-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>  
  
 <span data-ttu-id="a5ced-109">Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.FolderBrowserDialog> componente aparece na bandeja na parte inferior do Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="a5ced-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ced-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5ced-110">See also</span></span>
- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="a5ced-111">Como: Escolher pastas com o componente do Windows Forms FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="a5ced-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="a5ced-112">Componente FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="a5ced-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)

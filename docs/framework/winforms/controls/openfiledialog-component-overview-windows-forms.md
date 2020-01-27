---
title: Visão geral do componente OpenFileDialog
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728443"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="1b080-102">Visão geral do componente OpenFileDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1b080-102">OpenFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="1b080-103">O Windows Forms <xref:System.Windows.Forms.OpenFileDialog> componente é uma caixa de diálogo pré-configurada.</span><span class="sxs-lookup"><span data-stu-id="1b080-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="1b080-104">É a mesma caixa de diálogo **Abrir arquivo** exposta pelo sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="1b080-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="1b080-105">Ele é herdado da classe <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="1b080-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="use-this-component"></a><span data-ttu-id="1b080-106">Usar este componente</span><span class="sxs-lookup"><span data-stu-id="1b080-106">Use this component</span></span>

<span data-ttu-id="1b080-107">Use esse componente em seu aplicativo baseado no Windows como uma solução simples para seleção de arquivos em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="1b080-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="1b080-108">Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="1b080-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="1b080-109">No entanto, lembre-se de que, ao usar o componente <xref:System.Windows.Forms.OpenFileDialog>, você deve escrever sua própria lógica de abertura de arquivo.</span><span class="sxs-lookup"><span data-stu-id="1b080-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>

<span data-ttu-id="1b080-110">Use o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1b080-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="1b080-111">Você pode permitir que os usuários selecionem vários arquivos para serem abertos com a propriedade <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b080-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="1b080-112">Além disso, você pode usar a propriedade <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> para determinar se uma caixa de seleção somente leitura aparece na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="1b080-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="1b080-113">A propriedade <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> indica se a caixa de seleção somente leitura está selecionada.</span><span class="sxs-lookup"><span data-stu-id="1b080-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="1b080-114">Por fim, a propriedade <xref:System.Windows.Forms.FileDialog.Filter%2A> define a cadeia de caracteres de filtro de nome de arquivo atual, que determina as opções que aparecem na caixa "arquivos do tipo" na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="1b080-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>

<span data-ttu-id="1b080-115">Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.OpenFileDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1b080-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b080-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="1b080-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="1b080-117">Componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="1b080-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)

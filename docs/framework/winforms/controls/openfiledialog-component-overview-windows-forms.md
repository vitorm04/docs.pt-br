---
title: Visão geral do componente OpenFileDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: ec275a5923d332d23205c79442fa23bc6e402e3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61804553"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="6ac86-102">Visão geral do componente OpenFileDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6ac86-102">OpenFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="6ac86-103">Os formulários do Windows <xref:System.Windows.Forms.OpenFileDialog> componente é uma caixa de diálogo pré-configurada.</span><span class="sxs-lookup"><span data-stu-id="6ac86-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="6ac86-104">É a mesma caixa de diálogo **Abrir arquivo** exposta pelo sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="6ac86-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="6ac86-105">Ele herda o <xref:System.Windows.Forms.CommonDialog> classe.</span><span class="sxs-lookup"><span data-stu-id="6ac86-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="using-this-component"></a><span data-ttu-id="6ac86-106">Usando este componente</span><span class="sxs-lookup"><span data-stu-id="6ac86-106">Using this Component</span></span>  
 <span data-ttu-id="6ac86-107">Use esse componente em seu aplicativo baseado no Windows como uma solução simples para seleção de arquivos em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="6ac86-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="6ac86-108">Com base nas caixas de diálogo padrão do Windows, crie aplicativos cuja funcionalidade básica é imediatamente familiar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="6ac86-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="6ac86-109">Lembre-se, no entanto, que, quando usar o <xref:System.Windows.Forms.OpenFileDialog> componente, você deve escrever sua própria lógica de abertura de arquivo.</span><span class="sxs-lookup"><span data-stu-id="6ac86-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>  
  
 <span data-ttu-id="6ac86-110">Use o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6ac86-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="6ac86-111">Você pode permitir que usuários selecionem vários arquivos a serem abertos com o <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="6ac86-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="6ac86-112">Além disso, você pode usar o <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> propriedade para determinar se uma caixa de seleção somente leitura é exibido na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="6ac86-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="6ac86-113">O <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> propriedade indica se a caixa de seleção somente leitura está selecionada.</span><span class="sxs-lookup"><span data-stu-id="6ac86-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="6ac86-114">Por fim, o <xref:System.Windows.Forms.FileDialog.Filter%2A> propriedade define a atual arquivo nome filtro cadeia de caracteres, que determina as opções que aparecem na caixa "Arquivos do tipo" na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="6ac86-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>  
  
 <span data-ttu-id="6ac86-115">Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.OpenFileDialog> componente aparece na bandeja na parte inferior do Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="6ac86-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac86-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ac86-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="6ac86-117">Componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="6ac86-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)

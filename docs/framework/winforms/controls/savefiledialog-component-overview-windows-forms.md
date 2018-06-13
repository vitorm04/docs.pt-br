---
title: Visão geral do componente SaveFileDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: be5f70e2e8b0d5143ef387819689ce95564a72d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537441"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="c5b10-102">Visão geral do componente SaveFileDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c5b10-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="c5b10-103">Windows Forms <xref:System.Windows.Forms.SaveFileDialog> componente é uma caixa de diálogo pré-configurado.</span><span class="sxs-lookup"><span data-stu-id="c5b10-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="c5b10-104">É o mesmo que o padrão **salvar arquivo** caixa de diálogo usada pelo Windows.</span><span class="sxs-lookup"><span data-stu-id="c5b10-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="c5b10-105">Ele herda o <xref:System.Windows.Forms.CommonDialog> classe.</span><span class="sxs-lookup"><span data-stu-id="c5b10-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="c5b10-106">Trabalhando com o componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="c5b10-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="c5b10-107">Use-o como uma solução simples para permitir que os usuários salvem arquivos em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="c5b10-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="c5b10-108">Confiando em caixas de diálogo padrão do Windows, a funcionalidade básica de aplicativos que você cria é imediatamente familiar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="c5b10-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="c5b10-109">Lembre-se, no entanto, que, quando usar o <xref:System.Windows.Forms.SaveFileDialog> componente, você deve escrever sua própria lógica de salvamento do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c5b10-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="c5b10-110">Você pode usar o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c5b10-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="c5b10-111">Você pode abrir um arquivo no modo de leitura/gravação usando o <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c5b10-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="c5b10-112">Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.SaveFileDialog> componente aparece na bandeja de na parte inferior do Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="c5b10-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5b10-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5b10-113">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="c5b10-114">Componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="c5b10-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)

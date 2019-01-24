---
title: Visão geral do componente SaveFileDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: ab8eb5409d017c6ea73a44e4e57ccec9cece4824
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631055"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="6ce76-102">Visão geral do componente SaveFileDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6ce76-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="6ce76-103">Os formulários do Windows <xref:System.Windows.Forms.SaveFileDialog> componente é uma caixa de diálogo pré-configurada.</span><span class="sxs-lookup"><span data-stu-id="6ce76-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="6ce76-104">É o mesmo que o padrão **salvar arquivo** caixa de diálogo usada pelo Windows.</span><span class="sxs-lookup"><span data-stu-id="6ce76-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="6ce76-105">Ele herda o <xref:System.Windows.Forms.CommonDialog> classe.</span><span class="sxs-lookup"><span data-stu-id="6ce76-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="6ce76-106">Trabalhando com o componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="6ce76-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="6ce76-107">Usá-lo como uma solução simples para habilitar os usuários salvem arquivos em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="6ce76-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="6ce76-108">Confiando nas caixas de diálogo padrão do Windows, a funcionalidade básica de aplicativos que você criou é imediatamente familiar aos usuários.</span><span class="sxs-lookup"><span data-stu-id="6ce76-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="6ce76-109">Lembre-se, no entanto, que, quando usar o <xref:System.Windows.Forms.SaveFileDialog> componente, você deve escrever sua própria lógica de salvamento do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6ce76-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="6ce76-110">Você pode usar o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método para exibir a caixa de diálogo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6ce76-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="6ce76-111">Você pode abrir um arquivo no modo de leitura/gravação usando o <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6ce76-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="6ce76-112">Quando ele é adicionado a um formulário, o <xref:System.Windows.Forms.SaveFileDialog> componente aparece na bandeja na parte inferior do Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="6ce76-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce76-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ce76-113">See also</span></span>
- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="6ce76-114">Componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="6ce76-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)

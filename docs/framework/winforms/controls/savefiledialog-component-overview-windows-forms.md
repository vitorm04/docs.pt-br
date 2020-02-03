---
title: Visão geral do componente SaveFileDialog
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743106"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="0a05e-102">Visão geral do componente SaveFileDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0a05e-102">SaveFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="0a05e-103">O Windows Forms <xref:System.Windows.Forms.SaveFileDialog> componente é uma caixa de diálogo pré-configurada.</span><span class="sxs-lookup"><span data-stu-id="0a05e-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="0a05e-104">É o mesmo que a caixa de diálogo **salvar arquivo** padrão usada pelo Windows.</span><span class="sxs-lookup"><span data-stu-id="0a05e-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="0a05e-105">Ele é herdado da classe <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="0a05e-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="0a05e-106">Trabalhando com o componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="0a05e-106">Working with the SaveFileDialog Component</span></span>

<span data-ttu-id="0a05e-107">Use-o como uma solução simples para permitir que os usuários salvem arquivos em vez de configurar sua própria caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="0a05e-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="0a05e-108">Ao confiar nas caixas de diálogo padrão do Windows, a funcionalidade básica dos aplicativos que você cria é imediatamente familiar para os usuários.</span><span class="sxs-lookup"><span data-stu-id="0a05e-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="0a05e-109">No entanto, lembre-se de que, ao usar o componente <xref:System.Windows.Forms.SaveFileDialog>, você deve escrever sua própria lógica de salvamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="0a05e-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>

<span data-ttu-id="0a05e-110">Você pode usar o método <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> para exibir a caixa de diálogo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0a05e-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="0a05e-111">Você pode abrir um arquivo no modo de leitura/gravação usando o método <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a05e-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>

<span data-ttu-id="0a05e-112">Quando ele é adicionado a um formulário, o componente <xref:System.Windows.Forms.SaveFileDialog> aparece na bandeja na parte inferior da Designer de Formulários do Windows no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0a05e-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a05e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a05e-113">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="0a05e-114">Componente SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="0a05e-114">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)

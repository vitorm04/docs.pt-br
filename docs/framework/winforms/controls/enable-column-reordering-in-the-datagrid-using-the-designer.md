---
title: Habilitar reordenação de coluna no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: 823c0064b2710ab5dfd0f67edf95374590d4490b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745849"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="3db11-102">Como habilitar a reorganização da coluna no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="3db11-102">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="3db11-103">Ao exibir os dados exibidos em um controle de <xref:System.Windows.Forms.DataGridView> de Windows Forms, os usuários às vezes desejam comparar os valores em colunas específicas.</span><span class="sxs-lookup"><span data-stu-id="3db11-103">When viewing data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, users sometimes want to compare the values in specific columns.</span></span> <span data-ttu-id="3db11-104">Isso pode ser inconveniente se as colunas forem amplamente separadas no controle, especialmente se os usuários precisarem rolar para frente e para trás horizontalmente para ver todas as colunas nas quais estão interessadas.</span><span class="sxs-lookup"><span data-stu-id="3db11-104">This can be inconvenient if the columns are widely separated in the control, especially if users must scroll back and forth horizontally in order to see all the columns they are interested in.</span></span> <span data-ttu-id="3db11-105">Você pode tornar a tarefa de comparar valores de coluna mais fácil, permitindo que os usuários reordenem as colunas.</span><span class="sxs-lookup"><span data-stu-id="3db11-105">You can make the task of comparing column values easier by enabling your users to reorder the columns.</span></span> <span data-ttu-id="3db11-106">Quando você habilita a reordenação de coluna, os usuários podem mover uma coluna para uma nova posição arrastando o cabeçalho da coluna com o mouse.</span><span class="sxs-lookup"><span data-stu-id="3db11-106">When you enable column reordering, users can move a column to a new position by dragging the column header with the mouse.</span></span>

 <span data-ttu-id="3db11-107">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="3db11-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3db11-108">Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3db11-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-enable-column-reordering"></a><span data-ttu-id="3db11-109">Para habilitar a reordenação de coluna</span><span class="sxs-lookup"><span data-stu-id="3db11-109">To enable column reordering</span></span>

- <span data-ttu-id="3db11-110">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e selecione **habilitar reordenação de coluna**.</span><span class="sxs-lookup"><span data-stu-id="3db11-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Enable Column Reordering**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3db11-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3db11-111">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3db11-112">Como congelar colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="3db11-112">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](freeze-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="3db11-113">Como criar um projeto de aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3db11-113">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="3db11-114">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3db11-114">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)

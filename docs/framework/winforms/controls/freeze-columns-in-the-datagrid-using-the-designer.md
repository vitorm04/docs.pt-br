---
title: Como congelar colunas no controle DataGridView dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33606cc30ccc1d63e780d07bcb1757d62b7ebea2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="4d7e1-102">Como congelar colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="4d7e1-102">How to: Freeze Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="4d7e1-103">Quando os usuários exibem os dados exibidos em um Windows Forms <xref:System.Windows.Forms.DataGridView> controle, às vezes precisam para se referir a uma única coluna ou conjunto de colunas com frequência.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-103">When users view data displayed in a Windows Forms <xref:System.Windows.Forms.DataGridView> control, they sometimes need to refer to a single column or set of columns frequently.</span></span> <span data-ttu-id="4d7e1-104">Por exemplo, quando você exibe uma tabela de informações do cliente que contém várias colunas, é útil exibir o nome do cliente em todos os momentos, enquanto permite que outras colunas rolem para fora da região visível.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-104">For example, when you display a table of customer information that contains many columns, it is useful for you to display the customer name at all times while enabling other columns to scroll outside the visible region.</span></span>  
  
 <span data-ttu-id="4d7e1-105">Para obter esse comportamento, você pode congelar colunas no controle.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-105">To achieve this behavior, you can freeze columns in the control.</span></span> <span data-ttu-id="4d7e1-106">Quando você congela uma coluna, todas as colunas à esquerda (ou à direita em scripts de idioma da direita para esquerda) são congeladas também.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-106">When you freeze a column, all the columns to its left (or to its right in right-to-left language scripts) are frozen as well.</span></span> <span data-ttu-id="4d7e1-107">Colunas congeladas permanecerão no local enquanto todas as outras colunas podem rolar.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-107">Frozen columns remain in place while all other columns can scroll.</span></span> <span data-ttu-id="4d7e1-108">Se a reordenação de coluna estiver habilitada, as colunas congeladas serão tratadas como um grupo diferente das colunas não congeladas.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-108">If column reordering is enabled, the frozen columns are treated as a group distinct from the unfrozen columns.</span></span> <span data-ttu-id="4d7e1-109">Os usuários podem reposicionar colunas em um dos grupos, mas não poderão mover uma coluna de um grupo para outro.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-109">Users can reposition columns in either group, but they cannot move a column from one group to the other.</span></span>  
  
 <span data-ttu-id="4d7e1-110">O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="4d7e1-111">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4d7e1-111">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d7e1-112">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4d7e1-113">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4d7e1-114">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="4d7e1-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-freeze-a-column-using-the-designer"></a><span data-ttu-id="4d7e1-115">Para congelar uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="4d7e1-115">To freeze a column using the designer</span></span>  
  
1.  <span data-ttu-id="4d7e1-116">Clique na marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do <xref:System.Windows.Forms.DataGridView> de controle e, em seguida, selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-116">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="4d7e1-117">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-117">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="4d7e1-118">No **propriedades de coluna** grade, defina o <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-118">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d7e1-119">Você também pode congelar uma coluna ao adicioná-la selecionando a caixa de seleção **Congelada** na caixa de diálogo **Adicionar Coluna**.</span><span class="sxs-lookup"><span data-stu-id="4d7e1-119">You can also freeze a column when adding it by selecting the **Frozen** box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7e1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d7e1-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4d7e1-121">Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="4d7e1-121">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="4d7e1-122">Como habilitar a reorganização de colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="4d7e1-122">How to: Enable Column Reordering in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="4d7e1-123">Como: exibir texto da direita para esquerda no Windows Forms para globalização</span><span class="sxs-lookup"><span data-stu-id="4d7e1-123">How to: Display Right-to-Left Text in Windows Forms for Globalization</span></span>](http://msdn.microsoft.com/library/f0663385-2354-4c65-8676-706422283b14)  
 [<span data-ttu-id="4d7e1-124">Como: criar um projeto de aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="4d7e1-124">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="4d7e1-125">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4d7e1-125">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)

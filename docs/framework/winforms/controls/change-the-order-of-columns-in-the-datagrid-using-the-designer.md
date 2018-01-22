---
title: Como alterar a ordem de colunas no controle DataGridView dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42167c1391ef0820568fa120125bd973f567f0de
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="9c1c7-102">Como alterar a ordem de colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="9c1c7-102">How to: Change the Order of Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="9c1c7-103">Quando você associa um Windows Forms <xref:System.Windows.Forms.DataGridView> controle a uma fonte de dados, a ordem de exibição das colunas geradas automaticamente é determinada pela fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="9c1c7-103">When you bind a Windows Forms <xref:System.Windows.Forms.DataGridView> control to a data source, the display order of the automatically generated columns is dictated by the data source.</span></span> <span data-ttu-id="9c1c7-104">Se essa ordem não for a que preferir, você poderá alterar a ordem das colunas usando o designer.</span><span class="sxs-lookup"><span data-stu-id="9c1c7-104">If this order is not what you prefer, you can change the order of the columns using the designer.</span></span> <span data-ttu-id="9c1c7-105">Talvez deseje adicionar colunas não associadas ao controle e alterar a ordem de exibição.</span><span class="sxs-lookup"><span data-stu-id="9c1c7-105">You may also want to add unbound columns to the control and change their display order.</span></span> <span data-ttu-id="9c1c7-106">Para obter informações sobre como alterar a ordem das colunas programaticamente, consulte [Como alterar a ordem de colunas no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9c1c7-106">For information about how to change the column order programmatically, see [How to: Change the Order of Columns in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="9c1c7-107">O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="9c1c7-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9c1c7-108">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9c1c7-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c1c7-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="9c1c7-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9c1c7-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="9c1c7-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9c1c7-111">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="9c1c7-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span></span>  
  
### <a name="to-change-the-column-order-using-the-designer"></a><span data-ttu-id="9c1c7-112">Para alterar a ordem das colunas usando o designer</span><span class="sxs-lookup"><span data-stu-id="9c1c7-112">To change the column order using the designer</span></span>  
  
1.  <span data-ttu-id="9c1c7-113">Clique na marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do <xref:System.Windows.Forms.DataGridView> de controle e, em seguida, selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="9c1c7-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="9c1c7-114">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="9c1c7-114">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="9c1c7-115">Clique na seta para cima ou para baixo à direita da lista **Colunas selecionadas** até que a coluna selecionada esteja na posição desejada.</span><span class="sxs-lookup"><span data-stu-id="9c1c7-115">Click the up or down arrow to the right of the **Selected Columns** list until the selected column is in the position you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1c7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c1c7-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="9c1c7-117">Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="9c1c7-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [<span data-ttu-id="9c1c7-118">Como: criar um projeto de aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="9c1c7-118">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="9c1c7-119">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c1c7-119">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)

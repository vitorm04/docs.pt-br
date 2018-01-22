---
title: Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdd208d589c6b38088074f6d94045651df7049e8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="c7d23-102">Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="c7d23-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="c7d23-103">Dados tabulares geralmente são apresentados em um formato contábil no qual linhas alternativas têm cores de tela de fundo diferente.</span><span class="sxs-lookup"><span data-stu-id="c7d23-103">Tabular data is often presented in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="c7d23-104">Esse formato facilita para os usuários saber quais células estão em cada linha, especialmente com tabelas largas com muitas colunas.</span><span class="sxs-lookup"><span data-stu-id="c7d23-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="c7d23-105">Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar informações de estilo completo de linhas alternadas.</span><span class="sxs-lookup"><span data-stu-id="c7d23-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="c7d23-106">Você pode usar as características de estilo como fonte e cor de primeiro plano, além da cor da tela de fundo, para diferenciar as linhas alternadas.</span><span class="sxs-lookup"><span data-stu-id="c7d23-106">You can use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span> <span data-ttu-id="c7d23-107">Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="c7d23-107">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="c7d23-108">O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="c7d23-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="c7d23-109">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c7d23-109">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7d23-110">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="c7d23-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c7d23-111">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="c7d23-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c7d23-112">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c7d23-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="define-styles-for-alternating-rows"></a><span data-ttu-id="c7d23-113">Defina estilos para linhas alternadas</span><span class="sxs-lookup"><span data-stu-id="c7d23-113">Define styles for alternating rows</span></span>  
  
1.  <span data-ttu-id="c7d23-114">Selecione o <xref:System.Windows.Forms.DataGridView> controle no designer.</span><span class="sxs-lookup"><span data-stu-id="c7d23-114">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>  
  
2.  <span data-ttu-id="c7d23-115">No **propriedades** janela, clique no botão de reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c7d23-115">In the **Properties** window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> property.</span></span>  
  
3.  <span data-ttu-id="c7d23-116">Na caixa de diálogo **Construtor CellStyle**, defina o estilo configurando as propriedades e use o painel **Visualização** para confirmar suas escolhas.</span><span class="sxs-lookup"><span data-stu-id="c7d23-116">In the **CellStyle Builder** dialog box, define the style by setting the properties, and use the **Preview** pane to confirm your choices.</span></span> <span data-ttu-id="c7d23-117">Os estilos que você especifica são usados para todas as outras linhas exibidas no controle, começando com a segunda.</span><span class="sxs-lookup"><span data-stu-id="c7d23-117">The styles you specify are used for every other row displayed in the control, starting with the second one.</span></span>  
  
4.  <span data-ttu-id="c7d23-118">Para definir estilos para as linhas restantes, repita as etapas 2 e 3 usando a <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c7d23-118">To define styles for the remaining rows, repeat steps 2 and 3 using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c7d23-119">Células são exibidas usando estilos herdados de várias propriedades.</span><span class="sxs-lookup"><span data-stu-id="c7d23-119">Cells are displayed using styles inherited from multiple properties.</span></span> <span data-ttu-id="c7d23-120">Para obter mais informações sobre herança de estilo, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="c7d23-120">For more information about style inheritance, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d23-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7d23-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="c7d23-122">Estilos de célula no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7d23-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="c7d23-123">Formatação e estilos básicos no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7d23-123">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="c7d23-124">Usando o Designer com o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7d23-124">Using the Designer with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="c7d23-125">Como: criar um projeto de aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="c7d23-125">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="c7d23-126">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7d23-126">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)

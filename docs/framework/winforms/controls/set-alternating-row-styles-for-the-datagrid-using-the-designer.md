---
title: 'Como: Definir estilos de linhas alternados para o controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 1be746d4cce36344e034692a0e2e8e6a9e9320d5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040433"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="8d1f0-102">Como: Definir estilos de linhas alternados para o controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="8d1f0-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="8d1f0-103">Dados tabulares geralmente são apresentados em um formato contábil no qual linhas alternativas têm cores de tela de fundo diferente.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-103">Tabular data is often presented in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="8d1f0-104">Esse formato facilita para os usuários saber quais células estão em cada linha, especialmente com tabelas largas com muitas colunas.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>

<span data-ttu-id="8d1f0-105">Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar informações de estilo completas para alternar linhas.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="8d1f0-106">Você pode usar as características de estilo como fonte e cor de primeiro plano, além da cor da tela de fundo, para diferenciar as linhas alternadas.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-106">You can use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span> <span data-ttu-id="8d1f0-107">Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8d1f0-107">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="8d1f0-108">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8d1f0-109">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8d1f0-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>


### <a name="define-styles-for-alternating-rows"></a><span data-ttu-id="8d1f0-110">Defina estilos para linhas alternadas</span><span class="sxs-lookup"><span data-stu-id="8d1f0-110">Define styles for alternating rows</span></span>

1. <span data-ttu-id="8d1f0-111">Selecione o <xref:System.Windows.Forms.DataGridView> controle no designer.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-111">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>

2. <span data-ttu-id="8d1f0-112">Na janela **Propriedades** , clique no botão de reticências![(o botão de reticências (...) na janela Propriedades do Visual](./media/visual-studio-ellipsis-button.png)Studio.) ao <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> lado da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-112">In the **Properties** window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> property.</span></span>

3. <span data-ttu-id="8d1f0-113">Na caixa de diálogo **Construtor CellStyle**, defina o estilo configurando as propriedades e use o painel **Visualização** para confirmar suas escolhas.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-113">In the **CellStyle Builder** dialog box, define the style by setting the properties, and use the **Preview** pane to confirm your choices.</span></span> <span data-ttu-id="8d1f0-114">Os estilos que você especifica são usados para todas as outras linhas exibidas no controle, começando com a segunda.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-114">The styles you specify are used for every other row displayed in the control, starting with the second one.</span></span>

4. <span data-ttu-id="8d1f0-115">Para definir estilos para as linhas restantes, repita as etapas 2 e 3 usando <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-115">To define styles for the remaining rows, repeat steps 2 and 3 using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8d1f0-116">Células são exibidas usando estilos herdados de várias propriedades.</span><span class="sxs-lookup"><span data-stu-id="8d1f0-116">Cells are displayed using styles inherited from multiple properties.</span></span> <span data-ttu-id="8d1f0-117">Para obter mais informações sobre herança de estilo, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8d1f0-117">For more information about style inheritance, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d1f0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d1f0-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="8d1f0-119">Estilos de célula no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d1f0-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8d1f0-120">Formatação e estilos básicos no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d1f0-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8d1f0-121">Usando o Designer com o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d1f0-121">Using the Designer with the Windows Forms DataGridView Control</span></span>](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8d1f0-122">Como: Criar um projeto de aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d1f0-122">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="8d1f0-123">Como: Adicionar controles a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d1f0-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)

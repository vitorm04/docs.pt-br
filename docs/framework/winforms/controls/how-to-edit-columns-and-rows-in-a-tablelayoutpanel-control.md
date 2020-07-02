---
title: Como editar colunas e linhas em um controle TableLayoutPanel
description: Saiba como usar a caixa de diálogo estilos de coluna e linha para editar as linhas e colunas de seus controles de Windows Forms.
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619345"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="02c77-103">Como editar colunas e linhas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="02c77-103">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="02c77-104">Você pode usar o editor de coleção do <xref:System.Windows.Forms.TableLayoutPanel> controle, chamado de **coluna e** caixa de diálogo estilos de linha, para editar as linhas e colunas de seus controles.</span><span class="sxs-lookup"><span data-stu-id="02c77-104">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="02c77-105">Se você quiser que um controle ocupe várias linhas ou colunas, defina as propriedades `RowSpan` e `ColumnSpan` do controle.</span><span class="sxs-lookup"><span data-stu-id="02c77-105">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="02c77-106">Para obter mais informações, consulte [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="02c77-106">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="02c77-107">Se você quiser alinhar um controle dentro de uma célula ou se desejar que um controle seja ampliado dentro de uma célula, use a <xref:System.Windows.Forms.Control.Anchor%2A> Propriedade do controle.</span><span class="sxs-lookup"><span data-stu-id="02c77-107">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="02c77-108">Para obter mais informações, consulte [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="02c77-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="02c77-109">Editar linhas e colunas</span><span class="sxs-lookup"><span data-stu-id="02c77-109">To edit rows and columns</span></span>

1. <span data-ttu-id="02c77-110">Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="02c77-110">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="02c77-111">Clique no <xref:System.Windows.Forms.TableLayoutPanel> glifo ações do designer do controle ( ![ seta preta pequena ](./media/designer-actions-glyph.gif) ) e selecione **Editar linhas e colunas** para abrir a caixa de diálogo estilos de **coluna e linha** .</span><span class="sxs-lookup"><span data-stu-id="02c77-111">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="02c77-112">Você também pode clicar com o botão direito do mouse no <xref:System.Windows.Forms.TableLayoutPanel> controle e selecionar **Editar linhas e colunas** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="02c77-112">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="02c77-113">Para adicionar ou remover colunas, selecione **Colunas** da caixa de listagem suspensa **Tipo de membro**.</span><span class="sxs-lookup"><span data-stu-id="02c77-113">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="02c77-114">Para adicionar ou remover linhas, selecione **Linhas** da caixa de listagem suspensa **Tipo de membro**.</span><span class="sxs-lookup"><span data-stu-id="02c77-114">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="02c77-115">Clique no botão **Adicionar** para adicionar uma linha ou coluna ao final da linha **Membro**.</span><span class="sxs-lookup"><span data-stu-id="02c77-115">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="02c77-116">Clique no botão **Inserir** para adicionar uma linha ou coluna antes do item atualmente selecionado na lista.</span><span class="sxs-lookup"><span data-stu-id="02c77-116">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="02c77-117">Se você estiver adicionando uma linha ou coluna, selecione o **Tipo de tamanho** para a nova linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="02c77-117">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="02c77-118">Para obter mais informações, consulte <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="02c77-118">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="02c77-119">Para remover uma linha ou coluna, clique no botão **Remover** para excluir o item selecionado no momento na lista **Membro**.</span><span class="sxs-lookup"><span data-stu-id="02c77-119">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="02c77-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02c77-120">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="02c77-121">Controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="02c77-121">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)

---
title: 'Como: Editar colunas e linhas em um controle TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: 99ff3286592da0a097835b8f35d687475ca54fb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040288"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="7b720-102">Como: Editar colunas e linhas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7b720-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="7b720-103">Você pode usar o editor de coleção do <xref:System.Windows.Forms.TableLayoutPanel> controle, chamado de **coluna e** caixa de diálogo estilos de linha, para editar as linhas e colunas de seus controles.</span><span class="sxs-lookup"><span data-stu-id="7b720-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="7b720-104">Se você quiser que um controle ocupe várias linhas ou colunas, defina as propriedades `RowSpan` e `ColumnSpan` do controle.</span><span class="sxs-lookup"><span data-stu-id="7b720-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="7b720-105">Para obter mais informações, confira [Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="7b720-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="7b720-106">Se você quiser alinhar um controle dentro de uma célula ou se desejar que um controle seja ampliado dentro de uma célula, use a <xref:System.Windows.Forms.Control.Anchor%2A> Propriedade do controle.</span><span class="sxs-lookup"><span data-stu-id="7b720-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="7b720-107">Para obter mais informações, confira [Passo a passo: Organizando controles em Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="7b720-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="7b720-108">Editar linhas e colunas</span><span class="sxs-lookup"><span data-stu-id="7b720-108">To edit rows and columns</span></span>

1. <span data-ttu-id="7b720-109">Arraste um <xref:System.Windows.Forms.TableLayoutPanel> controle da **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="7b720-109">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="7b720-110">Clique no <xref:System.Windows.Forms.TableLayoutPanel> glifo de marca inteligente do controle![(glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e selecione **Editar linhas e colunas** para abrir a caixa de diálogo **estilos de coluna e linha** .</span><span class="sxs-lookup"><span data-stu-id="7b720-110">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="7b720-111">Você também pode clicar com o <xref:System.Windows.Forms.TableLayoutPanel> botão direito do mouse no controle e selecionar **Editar linhas e colunas** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="7b720-111">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="7b720-112">Para adicionar ou remover colunas, selecione **Colunas** da caixa de listagem suspensa **Tipo de membro**.</span><span class="sxs-lookup"><span data-stu-id="7b720-112">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="7b720-113">Para adicionar ou remover linhas, selecione **Linhas** da caixa de listagem suspensa **Tipo de membro**.</span><span class="sxs-lookup"><span data-stu-id="7b720-113">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="7b720-114">Clique no botão **Adicionar** para adicionar uma linha ou coluna ao final da linha **Membro**.</span><span class="sxs-lookup"><span data-stu-id="7b720-114">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="7b720-115">Clique no botão **Inserir** para adicionar uma linha ou coluna antes do item atualmente selecionado na lista.</span><span class="sxs-lookup"><span data-stu-id="7b720-115">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="7b720-116">Se você estiver adicionando uma linha ou coluna, selecione o **Tipo de tamanho** para a nova linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="7b720-116">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="7b720-117">Para obter mais informações, consulte <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="7b720-117">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="7b720-118">Para remover uma linha ou coluna, clique no botão **Remover** para excluir o item selecionado no momento na lista **Membro**.</span><span class="sxs-lookup"><span data-stu-id="7b720-118">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b720-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b720-119">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="7b720-120">Controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7b720-120">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)

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
ms.openlocfilehash: 2149cac7fb15052c2602ef20a6684696730aae1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941512"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="a28d9-102">Como: Editar colunas e linhas em um controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a28d9-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="a28d9-103">Você pode usar o editor de coleção do <xref:System.Windows.Forms.TableLayoutPanel> controle, chamado de **estilos de linha e coluna** caixa de diálogo para editar as linhas e colunas dos controles.</span><span class="sxs-lookup"><span data-stu-id="a28d9-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a28d9-104">Se você quiser que um controle ocupe várias linhas ou colunas, defina as propriedades `RowSpan` e `ColumnSpan` do controle.</span><span class="sxs-lookup"><span data-stu-id="a28d9-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="a28d9-105">Para obter mais informações, confira [Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="a28d9-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="a28d9-106">Se você deseja alinhar um controle dentro de uma célula, ou se você quiser um controle se alongue por uma célula, use o controle <xref:System.Windows.Forms.Control.Anchor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a28d9-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="a28d9-107">Para obter mais informações, confira [Passo a passo: Organizando controles nos Windows Forms utilizando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span><span class="sxs-lookup"><span data-stu-id="a28d9-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="a28d9-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="a28d9-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a28d9-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="a28d9-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a28d9-110">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="a28d9-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="a28d9-111">Editar linhas e colunas</span><span class="sxs-lookup"><span data-stu-id="a28d9-111">To edit rows and columns</span></span>  
  
1. <span data-ttu-id="a28d9-112">Arraste uma <xref:System.Windows.Forms.TableLayoutPanel> controlar do **caixa de ferramentas** para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="a28d9-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2. <span data-ttu-id="a28d9-113">Clique o <xref:System.Windows.Forms.TableLayoutPanel> glifo de smart tag do controle (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e selecione **Editar linhas e colunas** para abrir o  **Estilos de linha e coluna** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a28d9-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="a28d9-114">Você pode também clique com botão direito do <xref:System.Windows.Forms.TableLayoutPanel> controle e selecione **Editar linhas e colunas** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="a28d9-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3. <span data-ttu-id="a28d9-115">Para adicionar ou remover colunas, selecione **Colunas** da caixa de listagem suspensa **Tipo de membro**.</span><span class="sxs-lookup"><span data-stu-id="a28d9-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4. <span data-ttu-id="a28d9-116">Para adicionar ou remover linhas, selecione **Linhas** da caixa de listagem suspensa **Tipo de membro**.</span><span class="sxs-lookup"><span data-stu-id="a28d9-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5. <span data-ttu-id="a28d9-117">Clique no botão **Adicionar** para adicionar uma linha ou coluna ao final da linha **Membro**.</span><span class="sxs-lookup"><span data-stu-id="a28d9-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6. <span data-ttu-id="a28d9-118">Clique no botão **Inserir** para adicionar uma linha ou coluna antes do item atualmente selecionado na lista.</span><span class="sxs-lookup"><span data-stu-id="a28d9-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7. <span data-ttu-id="a28d9-119">Se você estiver adicionando uma linha ou coluna, selecione o **Tipo de tamanho** para a nova linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="a28d9-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="a28d9-120">Para obter mais informações, consulte <xref:System.Windows.Forms.SizeType>.</span><span class="sxs-lookup"><span data-stu-id="a28d9-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8. <span data-ttu-id="a28d9-121">Para remover uma linha ou coluna, clique no botão **Remover** para excluir o item selecionado no momento na lista **Membro**.</span><span class="sxs-lookup"><span data-stu-id="a28d9-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a28d9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a28d9-122">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="a28d9-123">Controle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a28d9-123">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)

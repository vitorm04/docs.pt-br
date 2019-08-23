---
title: 'Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 7a3029192ab0da4a954dfd7d3d258a00b154924e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957110"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="3d5b5-102">Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="3d5b5-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="3d5b5-103">O controle <xref:System.Windows.Forms.DataGridView> de Windows Forms deve conter colunas para exibir dados.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="3d5b5-104">Para preencher o controle manualmente é preciso adicionar as colunas.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="3d5b5-105">De forma alternativa, é possível associar o controle a uma fonte de dados, que gera e preenche as colunas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="3d5b5-106">Se a fonte de dados contém mais colunas do que se deseja exibir, remova as colunas indesejadas.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>

 <span data-ttu-id="3d5b5-107">Os procedimentos a seguir exigem um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3d5b5-108">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3d5b5-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="3d5b5-109">Para adicionar uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="3d5b5-109">To add a column using the designer</span></span>

1. <span data-ttu-id="3d5b5-110">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e selecione **adicionar coluna**.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>

2. <span data-ttu-id="3d5b5-111">Na caixa de diálogo **Adicionar Coluna**, escolha a opção **Coluna de Associação de Dados** e selecione uma coluna da fonte de dados, ou escolha a opção **Coluna Não Associada** e defina a coluna usando os campos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-111">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>

3. <span data-ttu-id="3d5b5-112">Clique no botão **Adicionar** para adicionar a coluna, fazendo com que ela apareça no designer se as colunas existentes não preencherem ainda o controle da área de exibição.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-112">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3d5b5-113">É possível modificar propriedades da coluna na caixa de diálogo **Editar Colunas**, que pode ser acessada na marca inteligente do controle.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-113">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>

## <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="3d5b5-114">Para remover uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="3d5b5-114">To remove a column using the designer</span></span>

1. <span data-ttu-id="3d5b5-115">Escolha **Editar Colunas** na marca inteligente do controle.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-115">Choose **Edit Columns** from the control's smart tag.</span></span>

2. <span data-ttu-id="3d5b5-116">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-116">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="3d5b5-117">Clique no botão **Remover** para excluir a coluna, fazendo com que ela desapareça do designer.</span><span class="sxs-lookup"><span data-stu-id="3d5b5-117">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d5b5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d5b5-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="3d5b5-119">Como: Criar um projeto de aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d5b5-119">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="3d5b5-120">Como: Adicionar controles a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d5b5-120">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)

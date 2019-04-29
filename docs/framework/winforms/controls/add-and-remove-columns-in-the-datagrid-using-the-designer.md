---
title: 'Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 80ede9b7bc5bf667e03dc0a745fbc0b5f6c2663a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640464"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="ecba7-102">Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="ecba7-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="ecba7-103">Os formulários do Windows <xref:System.Windows.Forms.DataGridView> controle deve conter colunas para exibir dados.</span><span class="sxs-lookup"><span data-stu-id="ecba7-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="ecba7-104">Para preencher o controle manualmente é preciso adicionar as colunas.</span><span class="sxs-lookup"><span data-stu-id="ecba7-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="ecba7-105">De forma alternativa, é possível associar o controle a uma fonte de dados, que gera e preenche as colunas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ecba7-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="ecba7-106">Se a fonte de dados contém mais colunas do que se deseja exibir, remova as colunas indesejadas.</span><span class="sxs-lookup"><span data-stu-id="ecba7-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="ecba7-107">Os procedimentos a seguir exigem uma **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="ecba7-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="ecba7-108">Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ecba7-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecba7-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="ecba7-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ecba7-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="ecba7-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ecba7-111">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ecba7-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="ecba7-112">Para adicionar uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="ecba7-112">To add a column using the designer</span></span>  
  
1. <span data-ttu-id="ecba7-113">Clique no glifo de marca inteligente (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito dos <xref:System.Windows.Forms.DataGridView> controle e, em seguida, selecione **adicionar coluna**.</span><span class="sxs-lookup"><span data-stu-id="ecba7-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2. <span data-ttu-id="ecba7-114">Na caixa de diálogo **Adicionar Coluna**, escolha a opção **Coluna de Associação de Dados** e selecione uma coluna da fonte de dados, ou escolha a opção **Coluna Não Associada** e defina a coluna usando os campos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="ecba7-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3. <span data-ttu-id="ecba7-115">Clique no botão **Adicionar** para adicionar a coluna, fazendo com que ela apareça no designer se as colunas existentes não preencherem ainda o controle da área de exibição.</span><span class="sxs-lookup"><span data-stu-id="ecba7-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ecba7-116">É possível modificar propriedades da coluna na caixa de diálogo **Editar Colunas**, que pode ser acessada na marca inteligente do controle.</span><span class="sxs-lookup"><span data-stu-id="ecba7-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="ecba7-117">Para remover uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="ecba7-117">To remove a column using the designer</span></span>  
  
1. <span data-ttu-id="ecba7-118">Escolha **Editar Colunas** na marca inteligente do controle.</span><span class="sxs-lookup"><span data-stu-id="ecba7-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2. <span data-ttu-id="ecba7-119">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="ecba7-119">Select a column from the **Selected Columns** list.</span></span>  
  
3. <span data-ttu-id="ecba7-120">Clique no botão **Remover** para excluir a coluna, fazendo com que ela desapareça do designer.</span><span class="sxs-lookup"><span data-stu-id="ecba7-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecba7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecba7-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="ecba7-122">Como: Criar um projeto de aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ecba7-122">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="ecba7-123">Como: Adicionar controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ecba7-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)

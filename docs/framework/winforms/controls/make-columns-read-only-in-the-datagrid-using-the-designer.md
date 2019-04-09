---
title: 'Como: Deixar as colunas somente leitura no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 8639c1e6f4382c1f91ed2c777b1b0ff29c5a60a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113510"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="19b36-102">Como: Deixar as colunas somente leitura no controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="19b36-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="19b36-103">Por padrão, os usuários podem modificar o texto e dados numéricos exibidos nos formulários de Windows <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="19b36-103">By default, users can modify text and numerical data displayed in the Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="19b36-104">Se quiser exibir os dados que não são destinados para modificação, você deverá tornar somente leitura as colunas que contêm os dados.</span><span class="sxs-lookup"><span data-stu-id="19b36-104">If you want to display data that is not meant for modification, you must make the columns that contain the data read-only.</span></span> <span data-ttu-id="19b36-105">Para obter informações sobre como fazer o controle totalmente somente leitura, consulte [como: Evitar a adição de linha e exclusão no Windows Forms usando o Designer de controle de DataGridView](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="19b36-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
 <span data-ttu-id="19b36-106">O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="19b36-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="19b36-107">Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="19b36-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19b36-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="19b36-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="19b36-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="19b36-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="19b36-110">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="19b36-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-make-a-column-read-only-by-using-the-designer"></a><span data-ttu-id="19b36-111">Para tornar a coluna somente leitura usando o designer</span><span class="sxs-lookup"><span data-stu-id="19b36-111">To make a column read-only by using the designer</span></span>  
  
1.  <span data-ttu-id="19b36-112">Clique no glifo de marca inteligente (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito dos <xref:System.Windows.Forms.DataGridView> controle e, em seguida, selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="19b36-112">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>  
  
2.  <span data-ttu-id="19b36-113">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="19b36-113">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="19b36-114">No **propriedades da coluna** grade, defina o <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="19b36-114">In the **Column Properties** grid, set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="19b36-115">Você também pode tornar uma coluna somente leitura ao adicioná-la marcando a caixa de seleção **Somente Leitura** na caixa de diálogo **Adicionar Coluna**.</span><span class="sxs-lookup"><span data-stu-id="19b36-115">You can also make a column read-only when you add it by selecting the **Read Only** check box in the **Add Column** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b36-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19b36-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="19b36-117">Como: Adicionar e remover colunas no controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="19b36-117">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="19b36-118">Como: Evitar a adição e a exclusão de linha no controle DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="19b36-118">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer</span></span>](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="19b36-119">Como: Criar um projeto de aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19b36-119">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="19b36-120">Como: Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19b36-120">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)

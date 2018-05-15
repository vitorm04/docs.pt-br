---
title: Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: f98d0e530f502655b9a48819d266a604581d22de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="e6534-102">Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="e6534-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="e6534-103">Windows Forms <xref:System.Windows.Forms.DataGridView> controle deve conter colunas para exibir os dados.</span><span class="sxs-lookup"><span data-stu-id="e6534-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="e6534-104">Para preencher o controle manualmente é preciso adicionar as colunas.</span><span class="sxs-lookup"><span data-stu-id="e6534-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="e6534-105">De forma alternativa, é possível associar o controle a uma fonte de dados, que gera e preenche as colunas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e6534-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="e6534-106">Se a fonte de dados contém mais colunas do que se deseja exibir, remova as colunas indesejadas.</span><span class="sxs-lookup"><span data-stu-id="e6534-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="e6534-107">Os procedimentos a seguir exigem uma **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="e6534-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e6534-108">Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e6534-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6534-109">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="e6534-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e6534-110">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="e6534-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e6534-111">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e6534-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="e6534-112">Para adicionar uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="e6534-112">To add a column using the designer</span></span>  
  
1.  <span data-ttu-id="e6534-113">Clique na marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do <xref:System.Windows.Forms.DataGridView> de controle e, em seguida, selecione **adicionar coluna**.</span><span class="sxs-lookup"><span data-stu-id="e6534-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2.  <span data-ttu-id="e6534-114">Na caixa de diálogo **Adicionar Coluna**, escolha a opção **Coluna de Associação de Dados** e selecione uma coluna da fonte de dados, ou escolha a opção **Coluna Não Associada** e defina a coluna usando os campos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="e6534-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3.  <span data-ttu-id="e6534-115">Clique no botão **Adicionar** para adicionar a coluna, fazendo com que ela apareça no designer se as colunas existentes não preencherem ainda o controle da área de exibição.</span><span class="sxs-lookup"><span data-stu-id="e6534-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e6534-116">É possível modificar propriedades da coluna na caixa de diálogo **Editar Colunas**, que pode ser acessada na marca inteligente do controle.</span><span class="sxs-lookup"><span data-stu-id="e6534-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="e6534-117">Para remover uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="e6534-117">To remove a column using the designer</span></span>  
  
1.  <span data-ttu-id="e6534-118">Escolha **Editar Colunas** na marca inteligente do controle.</span><span class="sxs-lookup"><span data-stu-id="e6534-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2.  <span data-ttu-id="e6534-119">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="e6534-119">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="e6534-120">Clique no botão **Remover** para excluir a coluna, fazendo com que ela desapareça do designer.</span><span class="sxs-lookup"><span data-stu-id="e6534-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6534-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6534-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="e6534-122">Como: criar um projeto de aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="e6534-122">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="e6534-123">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6534-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)

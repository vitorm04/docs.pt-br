---
title: 'Como: Alterar o tipo de uma coluna DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: f40ab6fe000f9104b10d5841f52eadf102a91a6b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040475"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="994fe-102">Como: Alterar o tipo de uma coluna DataGridView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="994fe-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="994fe-103">Às vezes, você vai querer alterar o tipo de uma coluna que já foi adicionada a um controle <xref:System.Windows.Forms.DataGridView> de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="994fe-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="994fe-104">Por exemplo, talvez deseje modificar os tipos de algumas das colunas que são geradas automaticamente quando você associa o controle a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="994fe-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="994fe-105">Isso é útil quando a tabela exibida contém colunas com chaves estrangeiras para linhas em uma tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="994fe-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="994fe-106">Nesse caso, talvez você queira substituir as colunas da caixa de texto que exibem essas chaves estrangeiras com colunas de caixa de combinação que exibem os valores mais significativos da tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="994fe-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>

 <span data-ttu-id="994fe-107">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="994fe-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="994fe-108">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="994fe-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="994fe-109">Para alterar o tipo de uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="994fe-109">To change the type of a column using the designer</span></span>

1. <span data-ttu-id="994fe-110">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="994fe-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="994fe-111">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="994fe-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="994fe-112">Na grade **Propriedades da coluna** grade, defina a propriedade `ColumnType` como o novo tipo de coluna.</span><span class="sxs-lookup"><span data-stu-id="994fe-112">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="994fe-113">A propriedade `ColumnType` é uma propriedade somente em tempo de design que indica a classe que representa o tipo de coluna.</span><span class="sxs-lookup"><span data-stu-id="994fe-113">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="994fe-114">Não é uma propriedade real definida em uma classe de coluna.</span><span class="sxs-lookup"><span data-stu-id="994fe-114">It is not an actual property defined in a column class.</span></span>

## <a name="see-also"></a><span data-ttu-id="994fe-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="994fe-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="994fe-116">Como: Criar um projeto de aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="994fe-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="994fe-117">Como: Adicionar controles a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="994fe-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)

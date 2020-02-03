---
title: Alterar o tipo de uma coluna DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 976f257d38dc7be5c904e63da47c61486bd3301c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737138"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a><span data-ttu-id="d7b9b-102">Como alterar o tipo de uma coluna DataGridView dos Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="d7b9b-102">How to: Change the Type of a Windows Forms DataGridView Column Using the Designer</span></span>
<span data-ttu-id="d7b9b-103">Às vezes, você vai querer alterar o tipo de uma coluna que já foi adicionada a um controle de <xref:System.Windows.Forms.DataGridView> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-103">Sometimes you will want to change the type of a column that has already been added to a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d7b9b-104">Por exemplo, talvez deseje modificar os tipos de algumas das colunas que são geradas automaticamente quando você associa o controle a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-104">For example, you may want to modify the types of some of the columns that are generated automatically when you bind the control to a data source.</span></span> <span data-ttu-id="d7b9b-105">Isso é útil quando a tabela exibida contém colunas com chaves estrangeiras para linhas em uma tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-105">This is useful when the table you display has columns containing foreign keys to rows in a related table.</span></span> <span data-ttu-id="d7b9b-106">Nesse caso, talvez você queira substituir as colunas da caixa de texto que exibem essas chaves estrangeiras com colunas de caixa de combinação que exibem os valores mais significativos da tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-106">In this case, you may want to replace the text box columns that display these foreign keys with combo box columns that display more meaningful values from the related table.</span></span>

 <span data-ttu-id="d7b9b-107">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d7b9b-108">Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d7b9b-108">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-change-the-type-of-a-column-using-the-designer"></a><span data-ttu-id="d7b9b-109">Para alterar o tipo de uma coluna usando o designer</span><span class="sxs-lookup"><span data-stu-id="d7b9b-109">To change the type of a column using the designer</span></span>

1. <span data-ttu-id="d7b9b-110">Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e selecione **Editar colunas**.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-110">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Edit Columns**.</span></span>

2. <span data-ttu-id="d7b9b-111">Selecione uma coluna na lista **Colunas Selecionadas**.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-111">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="d7b9b-112">Na grade **Propriedades da coluna** grade, defina a propriedade `ColumnType` como o novo tipo de coluna.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-112">In the **Column Properties** grid, set the `ColumnType` property to the new column type.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d7b9b-113">A propriedade `ColumnType` é uma propriedade somente em tempo de design que indica a classe que representa o tipo de coluna.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-113">The `ColumnType` property is a design-time-only property that indicates the class representing the column type.</span></span> <span data-ttu-id="d7b9b-114">Não é uma propriedade real definida em uma classe de coluna.</span><span class="sxs-lookup"><span data-stu-id="d7b9b-114">It is not an actual property defined in a column class.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7b9b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7b9b-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="d7b9b-116">Como criar um projeto de aplicativo Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7b9b-116">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="d7b9b-117">Como Adicionar Controles ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7b9b-117">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)

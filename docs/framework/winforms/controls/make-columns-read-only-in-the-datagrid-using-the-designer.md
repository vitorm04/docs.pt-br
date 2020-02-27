---
title: Tornar as colunas somente leitura no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 2dd3f8bfcad39ca3d530c79a6e6a8170585f7adf
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627949"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como deixar as colunas somente leitura no controle DataGridView dos Windows Forms usando o designer
Por padrão, os usuários podem modificar texto e dados numéricos exibidos no controle de <xref:System.Windows.Forms.DataGridView> de Windows Forms. Se quiser exibir os dados que não são destinados para modificação, você deverá tornar somente leitura as colunas que contêm os dados. Para obter informações sobre como tornar o controle totalmente somente leitura, veja [Como evitar a adição e a exclusão de linha no controle no DataGridView dos Windows Forms usando o Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>Para tornar a coluna somente leitura usando o designer

1. Clique no glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e, em seguida, selecione **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Na grade **Propriedades da coluna** , defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> como `true`.

    > [!NOTE]
    > Você também pode tornar uma coluna somente leitura ao adicioná-la marcando a caixa de seleção **Somente Leitura** na caixa de diálogo **Adicionar Coluna**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Como evitar a adição e a exclusão de linha no controle DataGridView dos Windows Forms usando o designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)

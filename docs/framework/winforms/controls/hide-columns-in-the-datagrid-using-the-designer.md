---
title: Ocultar colunas no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: c5344e10a69d86b1733f5462f9c2df0f0e71b8d5
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628833"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como ocultar colunas no controle DataGridView dos Windows Forms usando o designer
Às vezes, você desejará exibir apenas algumas das colunas que estão disponíveis em um controle de <xref:System.Windows.Forms.DataGridView> Windows Forms. Por exemplo, talvez você queira mostrar uma coluna de salário de funcionários para usuários com credenciais de gerenciamento enquanto a oculta de outros usuários. Como alternativa, talvez você queira associar o controle a uma fonte de dados que contém várias colunas, sendo que você deseja exibir apenas algumas delas. Nesse caso, você normalmente removerá as colunas que não está interessado em exibir em vez de ocultá-las. Para saber mais, veja [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-hide-a-column-using-the-designer"></a>Para ocultar uma coluna usando o designer

1. Clique no glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e, em seguida, selecione **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Na grade **Propriedades da coluna** , defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> como `false`.

    > [!NOTE]
    > Você também pode ocultar uma coluna ao adicioná-la desmarcando a caixa de seleção **Visível** na caixa de diálogo **Adicionar Coluna**.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)

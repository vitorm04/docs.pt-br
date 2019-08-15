---
title: 'Como: Deixar as colunas somente leitura no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 6bdd561c863a461f43a5a7aac025fead1f971bb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039817"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Deixar as colunas somente leitura no controle DataGridView do Windows Forms usando o designer
Por padrão, os usuários podem modificar texto e dados numéricos exibidos no controle <xref:System.Windows.Forms.DataGridView> de Windows Forms. Se quiser exibir os dados que não são destinados para modificação, você deverá tornar somente leitura as colunas que contêm os dados. Para obter informações sobre como tornar o controle totalmente somente leitura, consulte [como: Impedir adição e exclusão de linhas no controle Windows Forms DataGridView usando o designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>Para tornar a coluna somente leitura usando o designer

1. Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e selecione **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Na grade **Propriedades da coluna** , defina a <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> Propriedade como `true`.

    > [!NOTE]
    >  Você também pode tornar uma coluna somente leitura ao adicioná-la marcando a caixa de seleção **Somente Leitura** na caixa de diálogo **Adicionar Coluna**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Como: Adicionar e remover colunas no controle Windows Forms DataGridView usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Como: Impedir adição e exclusão de linha no controle Windows Forms DataGridView usando o designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md)

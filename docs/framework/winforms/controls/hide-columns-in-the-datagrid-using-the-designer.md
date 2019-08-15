---
title: 'Como: Ocultar colunas no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: d502a89913e108254848151e9058ac6ae83a9638
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039769"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Ocultar colunas no controle DataGridView do Windows Forms usando o designer
Às vezes, você desejará exibir apenas algumas das colunas que estão disponíveis em um <xref:System.Windows.Forms.DataGridView> controle de Windows Forms. Por exemplo, talvez você queira mostrar uma coluna de salário de funcionários para usuários com credenciais de gerenciamento enquanto a oculta de outros usuários. Como alternativa, talvez você queira associar o controle a uma fonte de dados que contém várias colunas, sendo que você deseja exibir apenas algumas delas. Nesse caso, você normalmente removerá as colunas que não está interessado em exibir em vez de ocultá-las. Para obter mais informações, confira [Como: Adicione e remova colunas no controle Windows Forms DataGridView usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-hide-a-column-using-the-designer"></a>Para ocultar uma coluna usando o designer

1. Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e selecione **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Na grade **Propriedades da coluna** , defina a <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> Propriedade como `false`.

    > [!NOTE]
    >  Você também pode ocultar uma coluna ao adicioná-la desmarcando a caixa de seleção **Visível** na caixa de diálogo **Adicionar Coluna**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Como: Adicionar e remover colunas no controle Windows Forms DataGridView usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md)

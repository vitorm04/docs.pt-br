---
title: Adicionar e remover colunas no controle DataGridView usando o designer
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 8843b1d30f3e5f31a060e27b41b0105e6584f155
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628599"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer
O controle de <xref:System.Windows.Forms.DataGridView> de Windows Forms deve conter colunas para exibir dados. Para preencher o controle manualmente é preciso adicionar as colunas. De forma alternativa, é possível associar o controle a uma fonte de dados, que gera e preenche as colunas automaticamente. Se a fonte de dados contém mais colunas do que se deseja exibir, remova as colunas indesejadas.

 Os procedimentos a seguir exigem um projeto de **aplicativo do Windows** com um formulário que contém um controle de <xref:System.Windows.Forms.DataGridView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-add-a-column-using-the-designer"></a>Para adicionar uma coluna usando o designer

1. Clique no glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e, em seguida, selecione **adicionar coluna**.

2. Na caixa de diálogo **Adicionar Coluna**, escolha a opção **Coluna de Associação de Dados** e selecione uma coluna da fonte de dados, ou escolha a opção **Coluna Não Associada** e defina a coluna usando os campos fornecidos.

3. Clique no botão **Adicionar** para adicionar a coluna, fazendo com que ela apareça no designer se as colunas existentes não preencherem ainda o controle da área de exibição.

    > [!NOTE]
    > É possível modificar propriedades da coluna na caixa de diálogo **Editar Colunas**, que pode ser acessada na marca inteligente do controle.

## <a name="to-remove-a-column-using-the-designer"></a>Para remover uma coluna usando o designer

1. Escolha **Editar Colunas** na marca inteligente do controle.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Clique no botão **Remover** para excluir a coluna, fazendo com que ela desapareça do designer.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.DataGridView>
- [Como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)

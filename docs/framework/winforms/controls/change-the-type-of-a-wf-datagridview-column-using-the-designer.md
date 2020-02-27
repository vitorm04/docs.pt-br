---
title: Alterar o tipo de uma coluna DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 470f350a4791a3db39d08ab7992d86eb7b2e270a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628612"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Como alterar o tipo de uma coluna DataGridView dos Windows Forms usando o designer
Às vezes, você vai querer alterar o tipo de uma coluna que já foi adicionada a um controle de <xref:System.Windows.Forms.DataGridView> Windows Forms. Por exemplo, talvez deseje modificar os tipos de algumas das colunas que são geradas automaticamente quando você associa o controle a uma fonte de dados. Isso é útil quando a tabela exibida contém colunas com chaves estrangeiras para linhas em uma tabela relacionada. Nesse caso, talvez você queira substituir as colunas da caixa de texto que exibem essas chaves estrangeiras com colunas de caixa de combinação que exibem os valores mais significativos da tabela relacionada.

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Para alterar o tipo de uma coluna usando o designer

1. Clique no glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e, em seguida, selecione **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Na grade **Propriedades da coluna** grade, defina a propriedade `ColumnType` como o novo tipo de coluna.

    > [!NOTE]
    > A propriedade `ColumnType` é uma propriedade somente em tempo de design que indica a classe que representa o tipo de coluna. Não é uma propriedade real definida em uma classe de coluna.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)

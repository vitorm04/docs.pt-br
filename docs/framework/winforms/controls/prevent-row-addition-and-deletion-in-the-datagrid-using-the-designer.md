---
title: Impedir adição e exclusão de linha no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: cca497aeaedd0c9f988241092eed707ecc259859
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628885"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como evitar a adição e a exclusão de linha no controle DataGridView dos Windows Forms usando o designer
Às vezes, você desejará impedir que os usuários insiram novas linhas de dados ou exclua linhas existentes no controle de <xref:System.Windows.Forms.DataGridView>. Novas linhas são inseridas na linha especial para novos registros na parte inferior do controle. Quando você desabilitar a adição de linha, a linha para novos registros não será exibida. Em seguida, você pode deixar o controle totalmente somente leitura desabilitando a exclusão de linha e a edição de célula.

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-prevent-row-addition-and-deletion"></a>Para evitar a exclusão e adição de linha

- Clique no glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e desmarque as caixas de seleção **habilitar adição** e **Habilitar exclusão** .

    > [!NOTE]
    > Para tornar o controle somente leitura inteiramente, desmarque também a caixa de seleção **Habilitar Edição**.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)

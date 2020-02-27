---
title: Alterar a ordem das colunas no controle DataGridView usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 7540203fb1c0465caeb045275734d1a7c6f25ee8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628742"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como alterar a ordem de colunas no controle DataGridView dos Windows Forms usando o designer

Quando você associa um Windows Forms <xref:System.Windows.Forms.DataGridView> controle a uma fonte de dados, a ordem de exibição das colunas geradas automaticamente é determinada pela fonte de dados. Se essa ordem não for a que preferir, você poderá alterar a ordem das colunas usando o designer. Talvez deseje adicionar colunas não associadas ao controle e alterar a ordem de exibição. Para obter informações sobre como alterar a ordem das colunas programaticamente, consulte [Como alterar a ordem de colunas no controle DataGridView dos Windows Forms](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um formulário que contém um controle <xref:System.Windows.Forms.DataGridView>. Para obter informações sobre como configurar esse projeto, consulte [como: criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-change-the-column-order-using-the-designer"></a>Para alterar a ordem das colunas usando o designer

1. Clique no glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) no canto superior direito do controle de <xref:System.Windows.Forms.DataGridView> e, em seguida, selecione **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Clique na seta para cima ou para baixo à direita da lista **Colunas selecionadas** até que a coluna selecionada esteja na posição desejada.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.DataGridView>
- [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Como criar um projeto de aplicativo Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como Adicionar Controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)

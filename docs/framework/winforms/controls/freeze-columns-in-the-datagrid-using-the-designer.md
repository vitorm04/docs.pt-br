---
title: 'Como: Congelar colunas no controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: 7ebdf7a1598ac3cd61005ae607e5bfbe7cb49059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933710"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Congelar colunas no controle DataGridView do Windows Forms usando o designer
Quando os usuários exibem dados exibidos em <xref:System.Windows.Forms.DataGridView> um controle de Windows Forms, às vezes eles precisam se referir a uma única coluna ou conjunto de colunas com frequência. Por exemplo, quando você exibe uma tabela de informações do cliente que contém várias colunas, é útil exibir o nome do cliente em todos os momentos, enquanto permite que outras colunas rolem para fora da região visível.

 Para obter esse comportamento, você pode congelar colunas no controle. Quando você congela uma coluna, todas as colunas à esquerda (ou à direita em scripts de idioma da direita para esquerda) são congeladas também. Colunas congeladas permanecerão no local enquanto todas as outras colunas podem rolar. Se a reordenação de coluna estiver habilitada, as colunas congeladas serão tratadas como um grupo diferente das colunas não congeladas. Os usuários podem reposicionar colunas em um dos grupos, mas não poderão mover uma coluna de um grupo para outro.

 O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-freeze-a-column-using-the-designer"></a>Para congelar uma coluna usando o designer

1. Clique no glifo de marca inteligente (![glifo de marca inteligente](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no <xref:System.Windows.Forms.DataGridView> canto superior direito do controle e selecione **Editar colunas**.

2. Selecione uma coluna na lista **Colunas Selecionadas**.

3. Na grade **Propriedades da coluna** , defina a <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Propriedade como `true`.

    > [!NOTE]
    > Você também pode congelar uma coluna ao adicioná-la selecionando a caixa de seleção **Congelada** na caixa de diálogo **Adicionar Coluna**.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [Como: Adicionar e remover colunas no controle Windows Forms DataGridView usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Como: Habilitar reordenação de coluna no controle Windows Forms DataGridView usando o designer](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [Como: Exibir texto da direita para a esquerda em Windows Forms para globalização](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md)

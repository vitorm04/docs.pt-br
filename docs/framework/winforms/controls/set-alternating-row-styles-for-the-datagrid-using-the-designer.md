---
title: 'Como: Definir estilos de linhas alternados para o controle DataGridView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: a24b4e6af98d2637ecae2352aaa881adcd1c1a45
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666842"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Definir estilos de linhas alternados para o controle DataGridView do Windows Forms usando o designer

Dados tabulares geralmente são apresentados em um formato contábil no qual linhas alternativas têm cores de tela de fundo diferente. Esse formato facilita para os usuários saber quais células estão em cada linha, especialmente com tabelas largas com muitas colunas.

Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar informações de estilo completas para alternar linhas. Você pode usar as características de estilo como fonte e cor de primeiro plano, além da cor da tela de fundo, para diferenciar as linhas alternadas. Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.DataGridView> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="define-styles-for-alternating-rows"></a>Defina estilos para linhas alternadas

1. Selecione o <xref:System.Windows.Forms.DataGridView> controle no designer.

2. Na janela **Propriedades** , clique no botão de reticências![(o botão de reticências (...) na janela Propriedades do Visual](./media/visual-studio-ellipsis-button.png)Studio.) ao <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> lado da propriedade.

3. Na caixa de diálogo **Construtor CellStyle**, defina o estilo configurando as propriedades e use o painel **Visualização** para confirmar suas escolhas. Os estilos que você especifica são usados para todas as outras linhas exibidas no controle, começando com a segunda.

4. Para definir estilos para as linhas restantes, repita as etapas 2 e 3 usando <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> a propriedade.

    > [!NOTE]
    > Células são exibidas usando estilos herdados de várias propriedades. Para obter mais informações sobre herança de estilo, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formatação e estilos básicos no controle DataGridView do Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Usando o Designer com o controle DataGridView dos Windows Forms](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles a Windows Forms](how-to-add-controls-to-windows-forms.md)

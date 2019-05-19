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
ms.openlocfilehash: 0e5714663a0873cb275d2909028a7d791be76fcf
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882221"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Como: Definir estilos de linhas alternados para o controle DataGridView do Windows Forms usando o designer
Dados tabulares geralmente são apresentados em um formato contábil no qual linhas alternativas têm cores de tela de fundo diferente. Esse formato facilita para os usuários saber quais células estão em cada linha, especialmente com tabelas largas com muitas colunas.  
  
 Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar informações de estilo completas para linhas alternadas. Você pode usar as características de estilo como fonte e cor de primeiro plano, além da cor da tela de fundo, para diferenciar as linhas alternadas. Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="define-styles-for-alternating-rows"></a>Defina estilos para linhas alternadas  
  
1. Selecione o <xref:System.Windows.Forms.DataGridView> controle no designer.  
  
2.  No **propriedades** janela, clique no botão de reticências (![botão do botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado de <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> propriedade.  
  
3. Na caixa de diálogo **Construtor CellStyle**, defina o estilo configurando as propriedades e use o painel **Visualização** para confirmar suas escolhas. Os estilos que você especifica são usados para todas as outras linhas exibidas no controle, começando com a segunda.  
  
4. Para definir estilos para as linhas restantes, repita as etapas 2 e 3 usando o <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> propriedade.  
  
    > [!NOTE]
    >  Células são exibidas usando estilos herdados de várias propriedades. Para obter mais informações sobre herança de estilo, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Formatação e estilos básicos no controle DataGridView do Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Usando o Designer com o controle DataGridView dos Windows Forms](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md)

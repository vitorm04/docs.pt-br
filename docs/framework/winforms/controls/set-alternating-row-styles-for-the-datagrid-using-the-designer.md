---
title: Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 0291f653b74acc0441d572bcff2fd5bd2c67e76c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Como definir estilos de linha alternada para o controle DataGridView dos Windows Forms usando o designer
Dados tabulares geralmente são apresentados em um formato contábil no qual linhas alternativas têm cores de tela de fundo diferente. Esse formato facilita para os usuários saber quais células estão em cada linha, especialmente com tabelas largas com muitas colunas.  
  
 Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar informações de estilo completo de linhas alternadas. Você pode usar as características de estilo como fonte e cor de primeiro plano, além da cor da tela de fundo, para diferenciar as linhas alternadas. Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="define-styles-for-alternating-rows"></a>Defina estilos para linhas alternadas  
  
1.  Selecione o <xref:System.Windows.Forms.DataGridView> controle no designer.  
  
2.  No **propriedades** janela, clique no botão de reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> propriedade.  
  
3.  Na caixa de diálogo **Construtor CellStyle**, defina o estilo configurando as propriedades e use o painel **Visualização** para confirmar suas escolhas. Os estilos que você especifica são usados para todas as outras linhas exibidas no controle, começando com a segunda.  
  
4.  Para definir estilos para as linhas restantes, repita as etapas 2 e 3 usando a <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> propriedade.  
  
    > [!NOTE]
    >  Células são exibidas usando estilos herdados de várias propriedades. Para obter mais informações sobre herança de estilo, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 [Estilos de célula no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Formatação e estilos básicos no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Usando o Designer com o controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)  
 [Como: criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)

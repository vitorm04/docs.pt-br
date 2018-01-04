---
title: Como definir estilos de fonte e cor no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 577a8237c79f90ae717b75e8d6633bfbdba82f58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a>Como definir estilos de fonte e cor no controle DataGridView dos Windows Forms
Você pode especificar a aparência visual de células dentro de uma <xref:System.Windows.Forms.DataGridView> controle definindo propriedades da <xref:System.Windows.Forms.DataGridViewCellStyle> classe. Você pode recuperar as instâncias dessa classe de várias propriedades do <xref:System.Windows.Forms.DataGridView> classe e suas classes complementar ou você pode instanciar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos de atribuição para essas propriedades.  
  
 Os procedimentos a seguir demonstram personalização básica da aparência de célula usando o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriedade. Todas as células no controle herdam os estilos especificados por essa propriedade, a menos que eles sejam substituídos no nível da célula, linha ou coluna. Para obter um exemplo de herança de estilo, consulte [Como definir estilos de célula padrão para o controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Para obter informações sobre usos adicionais do <xref:System.Windows.Forms.DataGridViewCellStyle> de classe, consulte os tópicos listados na seção Consulte também.  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  Consulte também [Como definir estilos de célula padrão e formatos de dados para o controle DataGridView dos Windows Forms usando o designer](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a>Para especificar a fonte usada pelas células DataGridView  
  
-   Definir o <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle>. O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para definir a fonte de todo o controle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a>Para especificar as cores de primeiro plano e de tela de fundo das células DataGridView  
  
-   Definir o <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> propriedades de um <xref:System.Windows.Forms.DataGridViewCellStyle>. O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para definir esses estilos para todo o controle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a>Para especificar as cores de primeiro plano e de tela de fundo das células DataGridView selecionadas  
  
-   Definir o <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> propriedades de um <xref:System.Windows.Forms.DataGridViewCellStyle>. O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para definir esses estilos para todo o controle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1`.  
  
-   Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, e <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.  
  
## <a name="robust-programming"></a>Programação robusta  
 Para obter escalabilidade máxima, você deve compartilhar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos em várias linhas, colunas ou células que usam os mesmos estilos, em vez de definir as propriedades de estilo para cada elemento separadamente. Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Formatação e estilos básicos no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Estilos de célula no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)

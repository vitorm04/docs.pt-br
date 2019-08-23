---
title: 'Como: Definir estilos de linha alternados para o controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: d113c45469f6a78c94b9489bd82f9e55b5b96bba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962270"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Como: Definir estilos de linha alternados para o controle DataGridView do Windows Forms
Dados tabulares geralmente são apresentados aos usuários em um formato contábil no qual linhas alternativas têm cores de tela de fundo diferente. Esse formato facilita para os usuários saber quais células estão em cada linha, especialmente com tabelas largas com muitas colunas.  
  
 Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar informações de estilo completas para alternar linhas. Isso permite usar as características de estilo como cor e fonte de primeiro plano, além da cor da tela de fundo, para diferenciar as linhas alternadas.  
  
 Há suporte para esta tarefa no Visual Studio.  Consulte [também como: Defina os estilos de linha alternados para o controle Windows Forms DataGridView](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)usando o designer.  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Para definir estilos de linha alternada de forma programática  
  
- Defina <xref:System.Windows.Forms.DataGridViewCellStyle> as propriedades dos objetos retornados <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> pelas propriedades e <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> do <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > Os estilos especificados usando as <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> propriedades <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> e substituem os estilos especificados na coluna e <xref:System.Windows.Forms.DataGridView> no nível, mas são substituídos pelos estilos definidos no nível de linha e célula individuais. Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Referências aos <xref:System?displayProperty=nameWithType>assemblies, <xref:System.Drawing?displayProperty=nameWithType>e. <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="robust-programming"></a>Programação robusta  
 Para obter a escalabilidade máxima, <xref:System.Windows.Forms.DataGridViewCellStyle> você deve compartilhar objetos em várias linhas, colunas ou células que usam os mesmos estilos, em vez de definir as propriedades de estilo para cada elemento separadamente. Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Formatação e estilos básicos no controle DataGridView do Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Como: Definir estilos de fonte e cor no controle Windows Forms DataGridView](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)

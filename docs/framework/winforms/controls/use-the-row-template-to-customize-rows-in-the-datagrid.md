---
title: Como usar o modelo da linha para personalizar linhas no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 2bde9b3f6934833804866e29c18f3636c65ba069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Como usar o modelo da linha para personalizar linhas no controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle usa o modelo de linha como base para todas as linhas que ele adiciona o controle por meio de associação de dados ou quando você chamar o <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> método sem especificar uma linha existente para usar.  
  
 O modelo de linha proporciona maior controle sobre a aparência e comportamento de linhas que o <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> propriedade fornece. Com o modelo de linha, você pode definir qualquer <xref:System.Windows.Forms.DataGridViewRow> propriedades, incluindo <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Há algumas situações em que você deve usar o modelo de linha para obter um efeito específico. Por exemplo, informações de altura de linha não podem ser armazenadas em um <xref:System.Windows.Forms.DataGridViewCellStyle>, portanto, você deve usar um modelo de linha para alterar a altura padrão usada por todas as linhas. O modelo de linha também é útil quando você cria suas próprias classes derivadas de <xref:System.Windows.Forms.DataGridViewRow> e você deseja que seu tipo personalizado usado quando novas linhas são adicionadas ao controle.  
  
> [!NOTE]
>  O modelo de linha é usado somente quando linhas são adicionadas. Você não pode alterar as linhas existentes alterando o modelo de linha.  
  
### <a name="to-use-the-row-template"></a>Para usar o modelo de linha  
  
-   Definir propriedades no objeto recuperado do <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> propriedade.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, e <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>  
 [Formatação e estilos básicos no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Estilos de célula no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)

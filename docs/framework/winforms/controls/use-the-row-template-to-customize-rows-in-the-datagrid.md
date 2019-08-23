---
title: 'Como: Usar o modelo da linha para personalizar linhas no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 0dba318e6aa35761f4e9471fdb13b65644747b57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966501"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Como: Usar o modelo da linha para personalizar linhas no controle DataGridView do Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle usa o modelo de linha como uma base para todas as linhas que ele adiciona ao controle por meio da vinculação de dados ou quando <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> você chama o método sem especificar uma linha existente a ser usada.  
  
 O modelo de linha proporciona maior controle sobre a aparência e o comportamento de linhas que <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> a propriedade fornece. Com o modelo de linha, você pode definir <xref:System.Windows.Forms.DataGridViewRow> qualquer propriedade, <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>incluindo.  
  
 Há algumas situações em que você deve usar o modelo de linha para obter um efeito específico. Por exemplo, as informações de altura de linha não podem <xref:System.Windows.Forms.DataGridViewCellStyle>ser armazenadas em um, portanto, você deve usar um modelo de linha para alterar a altura padrão usada por todas as linhas. O modelo de linha também é útil quando você cria suas próprias classes derivadas <xref:System.Windows.Forms.DataGridViewRow> de e deseja que seu tipo personalizado seja usado quando novas linhas são adicionadas ao controle.  
  
> [!NOTE]
> O modelo de linha é usado somente quando linhas são adicionadas. Você não pode alterar as linhas existentes alterando o modelo de linha.  
  
### <a name="to-use-the-row-template"></a>Para usar o modelo de linha  
  
- Defina as propriedades no objeto recuperado da <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> propriedade.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Referências aos <xref:System?displayProperty=nameWithType>assemblies, <xref:System.Drawing?displayProperty=nameWithType>e. <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Formatação e estilos básicos no controle DataGridView do Windows Forms](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Estilos de célula no controle DataGridView do Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)

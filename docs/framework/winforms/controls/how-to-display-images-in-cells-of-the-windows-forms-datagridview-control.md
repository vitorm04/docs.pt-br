---
title: Exibir imagens em células do controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740278"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Como exibir imagens em células do controle DataGridView dos Windows Forms
Uma imagem ou um gráfico é um dos valores que você pode exibir em uma linha de dados. Frequentemente, esses elementos gráficos assumem a forma de foto do funcionário ou um logotipo da empresa.  
  
 Incorporar imagens é simples quando você exibe dados dentro do controle de <xref:System.Windows.Forms.DataGridView>. O controle de <xref:System.Windows.Forms.DataGridView> manipula nativamente qualquer formato de imagem com suporte da classe <xref:System.Drawing.Image>, bem como o formato de imagem OLE usado por alguns bancos de dados.  
  
 Se a fonte de dados do controle de <xref:System.Windows.Forms.DataGridView> tiver uma coluna de imagens, ela será exibida automaticamente pelo controle de <xref:System.Windows.Forms.DataGridView>.  
  
 O exemplo de código a seguir demonstra como extrair um ícone de um recurso inserido e convertê-lo em um bitmap para exibição em cada célula de uma coluna de imagens. Para obter outro exemplo que substitui os valores de célula textual por imagens correspondentes, consulte [Como personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Um recurso de ícone incorporado denominado `tree.ico`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>e <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- [Recursos básicos de coluna, linha e célula no controle DataGridView dos Windows Forms](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Como personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)

---
title: Como exibir imagens em células do controle DataGridView dos Windows Forms
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
ms.openlocfilehash: 62a29b9ade4953a1775c2a71b62e4881065f51a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531187"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Como exibir imagens em células do controle DataGridView dos Windows Forms
Uma imagem ou um gráfico é um dos valores que você pode exibir em uma linha de dados. Frequentemente, esses elementos gráficos assumem a forma de foto do funcionário ou um logotipo da empresa.  
  
 A incorporação de imagens é simple quando você exibe dados dentro de <xref:System.Windows.Forms.DataGridView> controle. O <xref:System.Windows.Forms.DataGridView> controle nativamente trata qualquer formato de imagem com suporte a <xref:System.Drawing.Image> classe, bem como a OLE de formato usado por alguns bancos de dados de imagem.  
  
 Se o <xref:System.Windows.Forms.DataGridView> fonte de dados do controle tem uma coluna de imagens, eles serão exibidos automaticamente pelo <xref:System.Windows.Forms.DataGridView> controle.  
  
 O exemplo de código a seguir demonstra como extrair um ícone de um recurso inserido e convertê-lo em um bitmap para exibição em cada célula de uma coluna de imagens. Para obter outro exemplo que substitui os valores de célula textual por imagens correspondentes, consulte [Como personalizar a formatação de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Um recurso de ícone incorporado denominado `tree.ico`.  
  
-   Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, e <xref:System.Drawing?displayProperty=nameWithType> assemblies.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 [Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Como personalizar a formatação de dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)

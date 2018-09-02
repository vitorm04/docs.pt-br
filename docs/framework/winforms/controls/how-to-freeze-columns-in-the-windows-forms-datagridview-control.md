---
title: Como congelar colunas no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: df8ac7e7db74d4e8df8872b5ec7f8f2ec774b3c8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407292"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Como congelar colunas no controle DataGridView dos Windows Forms
Quando os usuários exibem os dados exibidos em um Windows Forms <xref:System.Windows.Forms.DataGridView> controle, às vezes elas precisam para se referir a uma única coluna ou conjunto de colunas com frequência. Por exemplo, ao exibir uma tabela de informações do cliente que contém várias colunas, é útil exibir o nome do cliente em todos os momentos enquanto permite outras colunas rolem para fora da região visível.  
  
 Para obter esse comportamento, você pode congelar colunas no controle. Quando você congela uma coluna, todas as colunas à esquerda (ou à direita em scripts de idioma da direita para esquerda) são congeladas também. Colunas congeladas permanecerão no local enquanto todas as outras colunas podem rolar.  
  
> [!NOTE]
>  Se a reordenação de coluna estiver habilitada, as colunas congeladas serão tratadas como um grupo diferente das colunas não congeladas. Os usuários podem reposicionar colunas em um dos grupos, mas não poderão mover uma coluna de um grupo para outro.  
  
 O <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> propriedade de uma coluna determina se a coluna está sempre visível dentro da grade.  
  
 Há suporte para esta tarefa no Visual Studio.  Consulte também [como: Congelar colunas no Windows Forms DataGridView controle usando o Designer](https://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).  
  
### <a name="to-freeze-a-column-programmatically"></a>Para congelar uma coluna de forma programática  
  
-   Defina a propriedade <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> como `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna denominada `AddToCartButton`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Como habilitar a reorganização de coluna no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)

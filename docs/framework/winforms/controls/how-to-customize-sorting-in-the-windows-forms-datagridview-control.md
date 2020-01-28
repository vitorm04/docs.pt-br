---
title: Personalizar a classificação em um controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 20f581b2df6fd172a0a1998aed60c56b0306f2eb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743186"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Como personalizar a classificação no controle DataGridView dos Windows Forms
O controle de <xref:System.Windows.Forms.DataGridView> fornece classificação automática, mas, dependendo de suas necessidades, talvez seja necessário personalizar as operações de classificação. Por exemplo, é possível usar a classificação programática para criar uma interface do usuário (UI) alternativa. Como alternativa, você pode manipular o evento <xref:System.Windows.Forms.DataGridView.SortCompare> ou chamar a sobrecarga `Sort(IComparer)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A> para maior flexibilidade de classificação, como classificar várias colunas.  
  
 Os exemplos de código a seguir demonstram essas três abordagens da classificação personalizada. Para mais informações, consulte [Modos de classificação da coluna no controle DataGridView do Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Classificação programática  
 O exemplo de código a seguir demonstra uma classificação programática usando as propriedades <xref:System.Windows.Forms.DataGridView.SortOrder%2A> e <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> para determinar a direção da classificação e a propriedade <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> para definir manualmente o glifo de classificação. A sobrecarga de `Sort(DataGridViewColumn,ListSortDirection)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A> é usada para classificar dados somente em uma única coluna.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Classificação personalizada usando o evento SortCompare  
 O exemplo de código a seguir demonstra a classificação personalizada usando um manipulador de eventos <xref:System.Windows.Forms.DataGridView.SortCompare>. A <xref:System.Windows.Forms.DataGridViewColumn> selecionada é classificada e, se houver valores duplicados na coluna, a coluna de ID será usada para determinar a ordem final.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Classificação personalizada usando a interface IComparer  
 O exemplo de código a seguir demonstra a classificação personalizada usando a sobrecarga de `Sort(IComparer)` do método <xref:System.Windows.Forms.DataGridView.Sort%2A>, que usa uma implementação da interface <xref:System.Collections.IComparer> para executar uma classificação de várias colunas.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Esses exemplos precisam de:  
  
- Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- [Classificando dados no controle DataGridView dos Windows Forms](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Modos de classificação da coluna no controle DataGridView dos Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Como definir os modos de classificação para colunas no controle DataGridView do Windows Forms](set-the-sort-modes-for-columns-wf-datagridview-control.md)

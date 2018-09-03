---
title: Como personalizar a classificação no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 34a92af246e1145e8d0d1d6874b2d64d7dee7846
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482563"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Como personalizar a classificação no controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle proporciona classificação automática mas, dependendo das suas necessidades, talvez você precise personalizar as operações de classificação. Por exemplo, é possível usar a classificação programática para criar uma interface do usuário (UI) alternativa. Como alternativa, você pode lidar com o <xref:System.Windows.Forms.DataGridView.SortCompare> chamada ou evento a `Sort(IComparer)` sobrecarga da <xref:System.Windows.Forms.DataGridView.Sort%2A> método para maior flexibilidade de classificação, como classificar várias colunas.  
  
 Os exemplos de código a seguir demonstram essas três abordagens da classificação personalizada. Para mais informações, consulte [Modos de classificação da coluna no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Classificação programática  
 O exemplo de código a seguir demonstra uma classificação programática usando o <xref:System.Windows.Forms.DataGridView.SortOrder%2A> e <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> propriedades para determinar a direção da classificação e o <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> propriedade para definir manualmente o glifo de classificação. O `Sort(DataGridViewColumn,ListSortDirection)` sobrecarga da <xref:System.Windows.Forms.DataGridView.Sort%2A> método é usado para classificar dados somente em uma única coluna.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Classificação personalizada usando o evento SortCompare  
 O exemplo de código a seguir demonstra classificação personalizada usando um <xref:System.Windows.Forms.DataGridView.SortCompare> manipulador de eventos. Selecionado <xref:System.Windows.Forms.DataGridViewColumn> é classificada e, se houver valores duplicados na coluna, a coluna de ID é usada para determinar a classificação final.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Classificação personalizada usando a interface IComparer  
 O exemplo de código a seguir demonstra classificação personalizada usando o `Sort(IComparer)` sobrecarga da <xref:System.Windows.Forms.DataGridView.Sort%2A> método, que usa uma implementação da <xref:System.Collections.IComparer> interface para executar uma classificação de várias colunas.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esses exemplos precisam de:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como compilar esses exemplos da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 [Classificando dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Modos de classificação da coluna no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Como definir os modos de classificação para colunas no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)

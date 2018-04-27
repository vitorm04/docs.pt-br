---
title: Como personalizar a classificação no controle DataGridView dos Windows Forms
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f945cd82deeec5ff281ff067cf6be93d00c6810
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Como personalizar a classificação no controle DataGridView dos Windows Forms
O <xref:System.Windows.Forms.DataGridView> controle fornece classificação automática, mas, dependendo de suas necessidades, talvez seja necessário personalizar as operações de classificação. Por exemplo, é possível usar a classificação programática para criar uma interface do usuário (UI) alternativa. Como alternativa, você pode manipular o <xref:System.Windows.Forms.DataGridView.SortCompare> chamada ou evento de `Sort(IComparer)` de sobrecarga do <xref:System.Windows.Forms.DataGridView.Sort%2A> método maior flexibilidade de classificação, como classificar várias colunas.  
  
 Os exemplos de código a seguir demonstram essas três abordagens da classificação personalizada. Para mais informações, consulte [Modos de classificação da coluna no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Classificação programática  
 O exemplo de código a seguir demonstra uma classificação de programação usando o <xref:System.Windows.Forms.DataGridView.SortOrder%2A> e <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> propriedades para determinar a direção da classificação e o <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> propriedade para definir manualmente o glifo de classificação. O `Sort(DataGridViewColumn,ListSortDirection)` de sobrecarga do <xref:System.Windows.Forms.DataGridView.Sort%2A> método é usado para classificar dados somente em uma única coluna.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Classificação personalizada usando o evento SortCompare  
 O exemplo de código a seguir demonstra a classificação personalizada usando um <xref:System.Windows.Forms.DataGridView.SortCompare> manipulador de eventos. Selecionado <xref:System.Windows.Forms.DataGridViewColumn> está classificada e, se houver valores duplicados na coluna, a coluna ID é usada para determinar a ordem final.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Classificação personalizada usando a interface IComparer  
 O exemplo de código a seguir demonstra a classificação personalizada usando o `Sort(IComparer)` de sobrecarga do <xref:System.Windows.Forms.DataGridView.Sort%2A> método, que usa uma implementação do <xref:System.Collections.IComparer> para executar uma classificação de várias colunas.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esses exemplos precisam de:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar esses exemplos de linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 [Classificando dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Modos de classificação da coluna no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Como definir os modos de classificação para colunas no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)

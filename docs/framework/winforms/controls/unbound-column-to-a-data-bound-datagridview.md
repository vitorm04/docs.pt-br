---
title: Adicionar uma coluna desassociada a um controle DataGridView associado a dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 807bbc121f33c35d70068571e76637c078ecb3da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747070"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Como adicionar uma coluna não associada a um controle DataGridView dos Windows Forms associado a dados
Os dados exibidos no controle de <xref:System.Windows.Forms.DataGridView> normalmente serão provenientes de uma fonte de dados de algum tipo, mas talvez você queira exibir uma coluna de dados que não venha da fonte de dados. Esse tipo de coluna é chamado de coluna não associada. Colunas não associadas podem assumir várias formas. Frequentemente, elas são usadas para fornecer acesso aos detalhes de uma linha de dados.  
  
 O exemplo de código a seguir demonstra como criar uma coluna não associada dos botões de **Detalhes** para exibir uma tabela filho relacionada a uma linha específica em uma tabela pai quando você implementa um cenário mestre/de detalhes. Para responder a cliques de botão, implemente um manipulador de eventos <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> que exibe um formulário que contém a tabela filho.  
  
 Há suporte para esta tarefa no Visual Studio.  Consulte também [como: Adicionar e remover colunas no controle Windows Forms DataGridView usando o designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
- Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- [Exibindo dados no controle DataGridView dos Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Modos de exibição de dados no controle DataGridView dos Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)

---
title: Como adicionar uma coluna não associada a um controle DataGridView dos Windows Forms associado a dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 39c637fe30ed852f7d6e9fa7a1dbbfa72af9e4b4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466063"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Como adicionar uma coluna não associada a um controle DataGridView dos Windows Forms associado a dados
Os dados exibidos no <xref:System.Windows.Forms.DataGridView> controle normalmente serão provenientes de uma fonte de dados de algum tipo, mas você talvez queira exibir uma coluna de dados que não vêm da fonte de dados. Esse tipo de coluna é chamado de coluna não associada. Colunas não associadas podem assumir várias formas. Frequentemente, elas são usadas para fornecer acesso aos detalhes de uma linha de dados.  
  
 O exemplo de código a seguir demonstra como criar uma coluna não associada dos botões de **Detalhes** para exibir uma tabela filho relacionada a uma linha específica em uma tabela pai quando você implementa um cenário mestre/de detalhes. Para responder a cliques de botão, implemente um <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> manipulador de eventos que exibe um formulário que contém a tabela filho.  
  
 Há suporte para esta tarefa no Visual Studio.  Consulte também [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](https://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.  
  
-   Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 [Exibindo dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Modos de exibição dos dados no controle DataGridView do Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)

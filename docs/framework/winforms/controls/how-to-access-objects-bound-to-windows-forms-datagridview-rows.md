---
title: acessar objetos vinculados a linhas DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743170"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Como acessar objetos associados a linhas DataGridView dos Windows Forms
Às vezes, é útil exibir uma tabela de informações armazenadas em uma coleção de objetos de negócios. Quando você associa um controle de <xref:System.Windows.Forms.DataGridView> a essa coleção, cada propriedade pública é exibida em sua própria coluna, a menos que a propriedade tenha sido marcada como não navegável com um <xref:System.ComponentModel.BrowsableAttribute>. Por exemplo, uma coleção de objetos `Customer` teria colunas como **Nome** e **Endereço**.  
  
 Se esses objetos contiverem informações adicionais e o código que você deseja acessar, será possível alcançá-lo por meio de objetos de linha. No exemplo de código a seguir, os usuários podem selecionar várias linhas e clicar em um botão para enviar uma fatura para cada um dos clientes correspondentes.  
  
### <a name="to-access-row-bound-objects"></a>Para acessar objetos associados a linhas  
  
- Use a propriedade <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo de código completo inclui uma implementação simples de `Customer` e associa o <xref:System.Windows.Forms.DataGridView> a um <xref:System.Collections.ArrayList> contendo alguns objetos `Customer`. O manipulador de eventos <xref:System.Windows.Forms.Control.Click> da <xref:System.Windows.Forms.Button?displayProperty=nameWithType> deve acessar os objetos `Customer` por meio das linhas, porque a coleção Customer não está acessível fora do manipulador de eventos <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies Sistema e System.Windows.Forms.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Como associar objetos a controles DataGridView do Windows Forms](how-to-bind-objects-to-windows-forms-datagridview-controls.md)

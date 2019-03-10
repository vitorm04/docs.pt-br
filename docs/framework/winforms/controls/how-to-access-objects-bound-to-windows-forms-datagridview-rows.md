---
title: 'Como: Acessar objetos associados ao Windows Forms DataGridView linhas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 5c66bc961d92a2ece1aea4986d0c23181c971b3e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720339"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Como: Acessar objetos associados ao Windows Forms DataGridView linhas
Às vezes, é útil exibir uma tabela de informações armazenadas em uma coleção de objetos de negócios. Quando você associa um <xref:System.Windows.Forms.DataGridView> controle a uma coleção assim, cada propriedade pública é exibido em sua própria coluna, a menos que a propriedade foi marcado como não pesquisável com um <xref:System.ComponentModel.BrowsableAttribute>. Por exemplo, uma coleção de objetos `Customer` teria colunas como **Nome** e **Endereço**.  
  
 Se esses objetos contiverem informações adicionais e o código que você deseja acessar, será possível alcançá-lo por meio de objetos de linha. No exemplo de código a seguir, os usuários podem selecionar várias linhas e clicar em um botão para enviar uma fatura para cada um dos clientes correspondentes.  
  
### <a name="to-access-row-bound-objects"></a>Para acessar objetos associados a linhas  
  
-   Use a propriedade <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo inclui um simples `Customer` implementação e associa o <xref:System.Windows.Forms.DataGridView> para um <xref:System.Collections.ArrayList> que contém alguns `Customer` objetos. O <xref:System.Windows.Forms.Control.Click> manipulador de eventos do <xref:System.Windows.Forms.Button?displayProperty=nameWithType> deve acessar o `Customer` objetos por meio de linhas, porque a coleção do cliente não é acessível de fora a <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> manipulador de eventos.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies Sistema e System.Windows.Forms.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [Exibindo dados no controle DataGridView do Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Como: Associar objetos a controles DataGridView dos Windows Forms](how-to-bind-objects-to-windows-forms-datagridview-controls.md)

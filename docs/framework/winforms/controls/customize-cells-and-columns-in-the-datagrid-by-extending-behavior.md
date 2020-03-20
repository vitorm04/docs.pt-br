---
title: Personalize células e colunas no controle datagridview estendendo seu comportamento e aparência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: e111f0bce812fc0851fabd1fde0fc2a6d44dd25f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182386"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência
O <xref:System.Windows.Forms.DataGridView> controle fornece uma série de maneiras de personalizar sua aparência e comportamento usando propriedades, eventos e classes complementares. Ocasionalmente, você pode ter requisitos para as suas células que ultrapassem o que esses recursos podem fornecer. Você pode criar <xref:System.Windows.Forms.DataGridViewCell> sua própria classe personalizada para fornecer funcionalidade estendida.  
  
 Você cria <xref:System.Windows.Forms.DataGridViewCell> uma classe personalizada, <xref:System.Windows.Forms.DataGridViewCell> derivando da classe base ou de uma de suas classes derivadas. Embora você possa exibir qualquer tipo de célula em qualquer tipo <xref:System.Windows.Forms.DataGridViewColumn> de coluna, você normalmente também criará uma classe personalizada especializada para exibir seu tipo de célula. As classes <xref:System.Windows.Forms.DataGridViewColumn> de coluna derivam de um de seus tipos derivados.  
  
 No exemplo de código a seguir, você criará uma classe de célula personalizada chamada `DataGridViewRolloverCell` que detecta quando o mouse entra e sai dos limites da célula. Enquanto o mouse está dentro dos limites da célula, um retângulo de inserção é desenhado. Este novo tipo <xref:System.Windows.Forms.DataGridViewTextBoxCell> deriva e se comporta em todos os outros aspectos como sua classe base. A classe de coluna correspondente chama-se `DataGridViewRolloverColumn`.  
  
 Para usar essas classes, crie <xref:System.Windows.Forms.DataGridView> um formulário contendo `DataGridViewRolloverColumn` um controle, adicione um ou mais objetos à <xref:System.Windows.Forms.DataGridView.Columns%2A> coleção e preencha o controle com linhas contendo valores.  
  
> [!NOTE]
> Este exemplo não funcionará corretamente se você adicionar linhas vazias. Linhas vazias são criadas, por exemplo, quando você adiciona <xref:System.Windows.Forms.DataGridView.RowCount%2A> linhas ao controle definindo a propriedade. Isso ocorre porque as linhas adicionadas neste caso são compartilhadas automaticamente, o que significa que objetos `DataGridViewRolloverCell` não são instanciados até você clicar em células individuais, fazendo, assim, com que as linhas associadas tornem-se não compartilhadas.  
  
 Uma vez que esse tipo de personalização de célula requer linhas não compartilhadas, ele não é adequado para uso com grandes conjuntos de dados. Para obter mais informações sobre compartilhamento de linha, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Quando você <xref:System.Windows.Forms.DataGridViewCell> deriva <xref:System.Windows.Forms.DataGridViewColumn> rouca ou e adiciona novas propriedades à `Clone` classe derivada, certifique-se de substituir o método para copiar as novas propriedades durante as operações de clonagem. Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Para personalizar células e colunas no controle DataGridView  
  
1. Deriva uma nova classe `DataGridViewRolloverCell`celular, <xref:System.Windows.Forms.DataGridViewTextBoxCell> chamada , do tipo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Anular o <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> método `DataGridViewRolloverCell` da classe. Em uma substituição, primeiro chame a implementação da classe base, que lida com a funcionalidade de caixa de texto hospedada. Em seguida, use <xref:System.Windows.Forms.Control.PointToClient%2A> o método do controle para transformar a <xref:System.Windows.Forms.DataGridView> posição do cursor (em coordenadas de tela) para as coordenadas da área do cliente. Se as coordenadas do mouse estiverem dentro dos limites da célula, desenhe o retângulo em baixo-relevo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Anular os <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> métodos da `DataGridViewRolloverCell` classe para forçar as células a se repintarem quando o ponteiro do mouse entra ou as deixa.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Deriva ruma nova `DataGridViewRolloverCellColumn`classe, <xref:System.Windows.Forms.DataGridViewColumn> chamada , do tipo. Na construtora, atribua `DataGridViewRolloverCell` um novo <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> objeto à sua propriedade.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo inclui um pequeno formulário de teste que demonstra o comportamento do tipo de célula personalizado.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Windows.Forms e System.Drawing.  

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Personalizando o controle DataGridView dos Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Arquitetura de controle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)

---
title: 'Como: Personalizar células e colunas no controle DataGridView do Windows Forms estendendo o comportamento e a aparência'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: 0976a0e07aead1bbaf951c6db8266c5de1a31cd8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929698"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Como: Personalizar células e colunas no controle DataGridView do Windows Forms estendendo o comportamento e a aparência
O <xref:System.Windows.Forms.DataGridView> controle fornece várias maneiras de personalizar sua aparência e comportamento usando propriedades, eventos e classes complementares. Ocasionalmente, você pode ter requisitos para as suas células que ultrapassem o que esses recursos podem fornecer. Você pode criar sua própria classe <xref:System.Windows.Forms.DataGridViewCell> personalizada para fornecer funcionalidade estendida.  
  
 Você cria uma classe <xref:System.Windows.Forms.DataGridViewCell> personalizada derivando <xref:System.Windows.Forms.DataGridViewCell> da classe base ou de uma de suas classes derivadas. Embora seja possível exibir qualquer tipo de célula em qualquer tipo de coluna, normalmente você também criará uma classe <xref:System.Windows.Forms.DataGridViewColumn> personalizada especializada para exibir o tipo de célula. Classes de coluna derivam de <xref:System.Windows.Forms.DataGridViewColumn> ou um de seus tipos derivados.  
  
 No exemplo de código a seguir, você criará uma classe de célula personalizada chamada `DataGridViewRolloverCell` que detecta quando o mouse entra e sai dos limites da célula. Enquanto o mouse está dentro dos limites da célula, um retângulo de inserção é desenhado. Esse novo tipo deriva de <xref:System.Windows.Forms.DataGridViewTextBoxCell> e se comporta em todos os outros aspectos como sua classe base. A classe de coluna correspondente chama-se `DataGridViewRolloverColumn`.  
  
 Para usar essas classes, crie um formulário contendo um <xref:System.Windows.Forms.DataGridView> controle, adicione um ou mais `DataGridViewRolloverColumn` objetos à <xref:System.Windows.Forms.DataGridView.Columns%2A> coleção e preencha o controle com linhas contendo valores.  
  
> [!NOTE]
> Este exemplo não funcionará corretamente se você adicionar linhas vazias. Linhas vazias são criadas, por exemplo, quando você adiciona linhas ao controle definindo a <xref:System.Windows.Forms.DataGridView.RowCount%2A> propriedade. Isso ocorre porque as linhas adicionadas neste caso são compartilhadas automaticamente, o que significa que objetos `DataGridViewRolloverCell` não são instanciados até você clicar em células individuais, fazendo, assim, com que as linhas associadas tornem-se não compartilhadas.  
  
 Uma vez que esse tipo de personalização de célula requer linhas não compartilhadas, ele não é adequado para uso com grandes conjuntos de dados. Para obter mais informações sobre compartilhamento de linha, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Quando você deriva de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> e adiciona novas propriedades à classe derivada, certifique-se de substituir o `Clone` método para copiar as novas propriedades durante as operações de clonagem. Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Para personalizar células e colunas no controle DataGridView  
  
1. Derive uma nova classe `DataGridViewRolloverCell` <xref:System.Windows.Forms.DataGridViewTextBoxCell> de célula, chamada, do tipo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Substitua o <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> método `DataGridViewRolloverCell` na classe. Em uma substituição, primeiro chame a implementação da classe base, que lida com a funcionalidade de caixa de texto hospedada. Em seguida, use o <xref:System.Windows.Forms.Control.PointToClient%2A> método do controle para transformar a posição do cursor (em coordenadas da <xref:System.Windows.Forms.DataGridView> tela) nas coordenadas da área do cliente. Se as coordenadas do mouse estiverem dentro dos limites da célula, desenhe o retângulo em baixo-relevo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Substitua os <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> métodos <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> e na `DataGridViewRolloverCell` classe para forçar as células a se redesenharem quando o ponteiro do mouse entrar ou deixá-las.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Derive uma nova classe, `DataGridViewRolloverCellColumn`chamada, <xref:System.Windows.Forms.DataGridViewColumn> do tipo. No construtor, atribua um novo `DataGridViewRolloverCell` objeto à sua <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> propriedade.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo inclui um pequeno formulário de teste que demonstra o comportamento do tipo de célula personalizado.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Windows.Forms e System.Drawing.  
 
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Personalizando o controle DataGridView dos Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Arquitetura de controle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)

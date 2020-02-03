---
title: Personalizar células e colunas no controle DataGridView estendendo seu comportamento e aparência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: be01e085d4fa74c0c49f0a0494183482875c6a09
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744067"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência
O controle de <xref:System.Windows.Forms.DataGridView> fornece várias maneiras de personalizar sua aparência e comportamento usando propriedades, eventos e classes complementares. Ocasionalmente, você pode ter requisitos para as suas células que ultrapassem o que esses recursos podem fornecer. Você pode criar sua própria classe de <xref:System.Windows.Forms.DataGridViewCell> personalizada para fornecer funcionalidade estendida.  
  
 Você cria uma classe de <xref:System.Windows.Forms.DataGridViewCell> personalizada derivando da classe base <xref:System.Windows.Forms.DataGridViewCell> ou de uma de suas classes derivadas. Embora seja possível exibir qualquer tipo de célula em qualquer tipo de coluna, normalmente você também criará uma classe de <xref:System.Windows.Forms.DataGridViewColumn> personalizada especializada para exibir o tipo de célula. Classes de coluna derivam de <xref:System.Windows.Forms.DataGridViewColumn> ou um de seus tipos derivados.  
  
 No exemplo de código a seguir, você criará uma classe de célula personalizada chamada `DataGridViewRolloverCell` que detecta quando o mouse entra e sai dos limites da célula. Enquanto o mouse está dentro dos limites da célula, um retângulo de inserção é desenhado. Esse novo tipo deriva de <xref:System.Windows.Forms.DataGridViewTextBoxCell> e se comporta em todos os outros aspectos como sua classe base. A classe de coluna correspondente chama-se `DataGridViewRolloverColumn`.  
  
 Para usar essas classes, crie um formulário que contenha um controle <xref:System.Windows.Forms.DataGridView>, adicione um ou mais objetos `DataGridViewRolloverColumn` à coleção de <xref:System.Windows.Forms.DataGridView.Columns%2A> e preencha o controle com linhas que contenham valores.  
  
> [!NOTE]
> Este exemplo não funcionará corretamente se você adicionar linhas vazias. Linhas vazias são criadas, por exemplo, quando você adiciona linhas ao controle, definindo a propriedade <xref:System.Windows.Forms.DataGridView.RowCount%2A>. Isso ocorre porque as linhas adicionadas neste caso são compartilhadas automaticamente, o que significa que objetos `DataGridViewRolloverCell` não são instanciados até você clicar em células individuais, fazendo, assim, com que as linhas associadas tornem-se não compartilhadas.  
  
 Uma vez que esse tipo de personalização de célula requer linhas não compartilhadas, ele não é adequado para uso com grandes conjuntos de dados. Para obter mais informações sobre compartilhamento de linha, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Quando você deriva de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> e adiciona novas propriedades à classe derivada, certifique-se de substituir o método `Clone` para copiar as novas propriedades durante as operações de clonagem. Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Para personalizar células e colunas no controle DataGridView  
  
1. Derive uma nova classe de célula, chamada `DataGridViewRolloverCell`, do tipo <xref:System.Windows.Forms.DataGridViewTextBoxCell>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Substitua o método <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> na classe `DataGridViewRolloverCell`. Em uma substituição, primeiro chame a implementação da classe base, que lida com a funcionalidade de caixa de texto hospedada. Em seguida, use o método <xref:System.Windows.Forms.Control.PointToClient%2A> do controle para transformar a posição do cursor (em coordenadas da tela) para as coordenadas da área do cliente <xref:System.Windows.Forms.DataGridView>. Se as coordenadas do mouse estiverem dentro dos limites da célula, desenhe o retângulo em baixo-relevo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Substitua os métodos <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> e <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> na classe `DataGridViewRolloverCell` para forçar as células a se redesenharem quando o ponteiro do mouse entrar ou deixá-las.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Derive uma nova classe, chamada `DataGridViewRolloverCellColumn`, do tipo <xref:System.Windows.Forms.DataGridViewColumn>. No construtor, atribua um novo objeto `DataGridViewRolloverCell` à sua propriedade <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo de código completo inclui um pequeno formulário de teste que demonstra o comportamento do tipo de célula personalizado.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Windows.Forms e System.Drawing.  
 
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Personalizando o controle DataGridView do Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Arquitetura de controle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Tipos de coluna no controle DataGridView do Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)

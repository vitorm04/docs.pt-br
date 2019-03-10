---
title: 'Como: Personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e aparência'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: 7ea684fd0a3f23005e70594bf1870851a3708a8c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721262"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Como: Personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e aparência
O <xref:System.Windows.Forms.DataGridView> controle fornece várias maneiras de personalizar sua aparência e comportamento usando propriedades, eventos e classe complementares. Ocasionalmente, você pode ter requisitos para as suas células que ultrapassem o que esses recursos podem fornecer. Você pode criar seu próprio <xref:System.Windows.Forms.DataGridViewCell> classe para fornecer funcionalidade estendida.  
  
 Criar um personalizado <xref:System.Windows.Forms.DataGridViewCell> classe derivando de <xref:System.Windows.Forms.DataGridViewCell> classe base ou uma de suas classes derivadas. Embora você possa exibir qualquer tipo de célula em qualquer tipo de coluna, você normalmente também criará um personalizado <xref:System.Windows.Forms.DataGridViewColumn> classe especializada para exibir seu tipo de célula. Classes de coluna derivam de <xref:System.Windows.Forms.DataGridViewColumn> ou um de seus tipos derivados.  
  
 No exemplo de código a seguir, você criará uma classe de célula personalizada chamada `DataGridViewRolloverCell` que detecta quando o mouse entra e sai dos limites da célula. Enquanto o mouse está dentro dos limites da célula, um retângulo de inserção é desenhado. Esse novo tipo deriva de <xref:System.Windows.Forms.DataGridViewTextBoxCell> e se comporta em todos os outros aspectos como sua classe base. A classe de coluna correspondente chama-se `DataGridViewRolloverColumn`.  
  
 Para usar essas classes, crie um formulário que contém um <xref:System.Windows.Forms.DataGridView> de controle, adicione um ou mais `DataGridViewRolloverColumn` objetos para o <xref:System.Windows.Forms.DataGridView.Columns%2A> coleção e preencher o controle com linhas contendo valores.  
  
> [!NOTE]
>  Este exemplo não funcionará corretamente se você adicionar linhas vazias. Linhas vazias são criadas, por exemplo, quando você adiciona linhas ao controle configurando a <xref:System.Windows.Forms.DataGridView.RowCount%2A> propriedade. Isso ocorre porque as linhas adicionadas neste caso são compartilhadas automaticamente, o que significa que objetos `DataGridViewRolloverCell` não são instanciados até você clicar em células individuais, fazendo, assim, com que as linhas associadas tornem-se não compartilhadas.  
  
 Uma vez que esse tipo de personalização de célula requer linhas não compartilhadas, ele não é adequado para uso com grandes conjuntos de dados. Para obter mais informações sobre compartilhamento de linha, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
>  Quando você deriva <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> e adicionar novas propriedades à classe derivada, certifique-se de substituir o `Clone` método para copiar as novas propriedades durante operações de clonagem. Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Para personalizar células e colunas no controle DataGridView  
  
1.  Derivar uma nova classe de célula, chamada `DataGridViewRolloverCell`, da <xref:System.Windows.Forms.DataGridViewTextBoxCell> tipo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2.  Substituir a <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> método no `DataGridViewRolloverCell` classe. Em uma substituição, primeiro chame a implementação da classe base, que lida com a funcionalidade de caixa de texto hospedada. Em seguida, use o controle <xref:System.Windows.Forms.Control.PointToClient%2A> método para transformar a posição do cursor (nas coordenadas de tela) para o <xref:System.Windows.Forms.DataGridView> coordenadas da área de cliente. Se as coordenadas do mouse estiverem dentro dos limites da célula, desenhe o retângulo em baixo-relevo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3.  Substituir a <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> e <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> métodos no `DataGridViewRolloverCell` classe para forçar as células a repintarem a próprias quando o ponteiro do mouse entra ou sair delas.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4.  Derivar uma nova classe chamada `DataGridViewRolloverCellColumn`, da <xref:System.Windows.Forms.DataGridViewColumn> tipo. No construtor, atribuir um novo `DataGridViewRolloverCell` o objeto para a sua <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> propriedade.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo inclui um pequeno formulário de teste que demonstra o comportamento do tipo de célula personalizado.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Windows.Forms e System.Drawing.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Personalizando o controle DataGridView dos Windows Forms](customizing-the-windows-forms-datagridview-control.md)
- [Arquitetura de controle DataGridView](datagridview-control-architecture-windows-forms.md)
- [Tipos de coluna no controle DataGridView dos Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)

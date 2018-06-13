---
title: Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: 0a5d2dd5ac72d5199d143c6173e28457e1a80f6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529127"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência
O <xref:System.Windows.Forms.DataGridView> controle fornece várias maneiras para personalizar sua aparência e comportamento usando propriedades, eventos e complementar classes. Ocasionalmente, você pode ter requisitos para as suas células que ultrapassem o que esses recursos podem fornecer. Você pode criar seu próprios personalizada <xref:System.Windows.Forms.DataGridViewCell> classe para fornecer funcionalidade estendida.  
  
 Criar um personalizado <xref:System.Windows.Forms.DataGridViewCell> classe derivando de <xref:System.Windows.Forms.DataGridViewCell> classe base ou uma de suas classes derivadas. Embora você possa exibir qualquer tipo de célula em qualquer tipo de coluna, você normalmente também criará um personalizado <xref:System.Windows.Forms.DataGridViewColumn> classe especializada para exibir o tipo de célula. Coluna derivam de <xref:System.Windows.Forms.DataGridViewColumn> ou um de seus tipos derivados.  
  
 No exemplo de código a seguir, você criará uma classe de célula personalizada chamada `DataGridViewRolloverCell` que detecta quando o mouse entra e sai dos limites da célula. Enquanto o mouse está dentro dos limites da célula, um retângulo de inserção é desenhado. Esse novo tipo derivado de <xref:System.Windows.Forms.DataGridViewTextBoxCell> e se comporta em todos os outros aspectos como sua classe base. A classe de coluna correspondente chama-se `DataGridViewRolloverColumn`.  
  
 Para usar essas classes, crie um formulário que contém um <xref:System.Windows.Forms.DataGridView> controle, adicione um ou mais `DataGridViewRolloverColumn` objetos para o <xref:System.Windows.Forms.DataGridView.Columns%2A> coleção e preencher o controle com linhas que contêm valores.  
  
> [!NOTE]
>  Este exemplo não funcionará corretamente se você adicionar linhas vazias. Linhas vazias são criadas, por exemplo, quando você adiciona linhas ao controle definindo o <xref:System.Windows.Forms.DataGridView.RowCount%2A> propriedade. Isso ocorre porque as linhas adicionadas neste caso são compartilhadas automaticamente, o que significa que objetos `DataGridViewRolloverCell` não são instanciados até você clicar em células individuais, fazendo, assim, com que as linhas associadas tornem-se não compartilhadas.  
  
 Uma vez que esse tipo de personalização de célula requer linhas não compartilhadas, ele não é adequado para uso com grandes conjuntos de dados. Para obter mais informações sobre compartilhamento de linha, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
>  Quando você deriva de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> e adicionar novas propriedades para a classe derivada, certifique-se de substituir o `Clone` método para copiar as novas propriedades durante operações de clonagem. Você também deve chamar o método `Clone` da classe base para que as propriedades da classe base sejam copiadas para a nova célula ou coluna.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Para personalizar células e colunas no controle DataGridView  
  
1.  Derive uma nova classe de célula, chamada `DataGridViewRolloverCell`, do <xref:System.Windows.Forms.DataGridViewTextBoxCell> tipo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2.  Substituir o <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> método o `DataGridViewRolloverCell` classe. Em uma substituição, primeiro chame a implementação da classe base, que lida com a funcionalidade de caixa de texto hospedada. Em seguida, use o controle <xref:System.Windows.Forms.Control.PointToClient%2A> método para transformar a posição do cursor (em coordenadas de tela) para o <xref:System.Windows.Forms.DataGridView> coordenadas da área do cliente. Se as coordenadas do mouse estiverem dentro dos limites da célula, desenhe o retângulo em baixo-relevo.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3.  Substituir o <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> e <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> métodos de `DataGridViewRolloverCell` classe forçar células para redesenhar a mesmos quando o ponteiro do mouse entra ou sai-los.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4.  Derivar uma nova classe chamada `DataGridViewRolloverCellColumn`, do <xref:System.Windows.Forms.DataGridViewColumn> tipo. No construtor, atribuir um novo `DataGridViewRolloverCell` o objeto para a sua <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> propriedade.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código completo inclui um pequeno formulário de teste que demonstra o comportamento do tipo de célula personalizado.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Windows.Forms e System.Drawing.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [Personalizando o controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Arquitetura de controle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Tipos de coluna no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)

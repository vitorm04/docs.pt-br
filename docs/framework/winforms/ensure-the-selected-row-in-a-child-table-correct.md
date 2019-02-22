---
title: 'Como: Verifique se que a linha selecionada em uma tabela filho permaneça na posição correta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
ms.openlocfilehash: 2ecac036bf081959b8ce2ba0afe8fdeed9ed9099
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664231"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a>Como: Verifique se que a linha selecionada em uma tabela filho permaneça na posição correta
Muitas vezes, ao trabalhar com a vinculação de dados nos Windows Forms, você exibirá dados no que é chamado de modo de exibição pai/filho ou detalhes/mestre. Isso se refere a um cenário de associação de dados em que os dados da mesma fonte são exibidos em dois controles. Alterar a seleção em um controle faz com que os dados exibidos no segundo controle mudem. Por exemplo, o primeiro controle pode conter uma lista de clientes e o segundo, uma lista de pedidos relacionada ao cliente selecionado no primeiro controle.  
  
 Iniciando com o .NET Framework versão 2.0, quando você exibe dados no modo de exibição pai/filho, pode ser necessário executar etapas adicionais para que a linha selecionada atualmente na tabela filho não seja redefinida para a primeira linha da tabela. Para fazer isso, será preciso armazenar em cache a posição da tabela filho e redefini-la após a alteração da tabela pai. Normalmente, a redefinição do filho ocorre na primeira vez que um campo em uma linha da tabela pai muda.  
  
### <a name="to-cache-the-current-child-position"></a>Para armazenar em cache a posição filho atual  
  
1.  Declare uma variável de inteiro para armazenar a posição de lista filho e uma variável booliana para indicar se a posição filho deve ser armazenada em cache.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  Lidar com o <xref:System.Windows.Forms.CurrencyManager.ListChanged> evento para a associação <xref:System.Windows.Forms.CurrencyManager> e verifique se há um <xref:System.ComponentModel.ListChangedType> de <xref:System.ComponentModel.ListChangedType.Reset>.  
  
3.  Verifique a posição atual do <xref:System.Windows.Forms.CurrencyManager>. Se for maior que a primeira entrada na lista (normalmente 0), salve-a em uma variável.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  Lidar com a lista de pai <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> evento para o Gerenciador de moeda pai. No manipulador, defina o valor booliano para indicar que este não é um cenário de cache. Se o <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> ocorre, a alteração para o pai é uma alteração de posição de lista e não uma alteração de valor do item.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a>Para redefinir a posição filho  
  
1.  Lidar com o <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> eventos para o filho da associação <xref:System.Windows.Forms.CurrencyManager>.  
  
2.  Redefina a posição da tabela filho para a posição em cache salva no procedimento anterior.  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como salvar a posição atual no <xref:System.Windows.Forms.CurrencyManager>para uma tabela filho e redefinir a posição após a conclusão de uma edição na tabela pai. Este exemplo contém dois <xref:System.Windows.Forms.DataGridView> controles associados a duas tabelas em um <xref:System.Data.DataSet> usando um <xref:System.Windows.Forms.BindingSource> componente. É estabelecido um relacionamento entre as duas tabelas e o relacionamento é adicionado para o <xref:System.Data.DataSet>. A posição na tabela filho inicialmente é definida como a terceira linha para fins de demonstração.  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 Para testar o exemplo de código, execute as etapas a seguir:  
  
1.  Execute o exemplo.  
  
2.  Marque a caixa de seleção **Armazenar em cache e redefinir posição**.  
  
3.  Clique no botão **Limpar campo pai** para provocar uma alteração em um campo da tabela pai. Observe que a linha selecionada na tabela filho não muda.  
  
4.  Feche e execute o exemplo novamente. Você precisa fazer isso porque o comportamento de reinicialização ocorre apenas na primeira alteração da linha pai.  
  
5.  Desmarque a caixa de seleção **Armazenar em cache e redefinir posição**.  
  
6.  Clique no botão **Limpar campo pai**. Observe que a linha selecionada na tabela filho muda para a primeira linha.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referência aos assemblies System, System.Data, System.Drawing, System.Windows.Forms e System.XML.  
  
 Para obter informações sobre como criar este exemplo da linha de comando do Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [construção de linha de comando com csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também
- [Como: Certifique-se de vários controles associados à mesma fonte de dados permaneçam sincronizados](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)
- [Componente BindingSource](../../../docs/framework/winforms/controls/bindingsource-component.md)
- [Vinculação de dados e os Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)

---
title: Como navegar por dados no Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
ms.openlocfilehash: 9572c1234c07c77d5df0c9cd58499faafe460e4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Como navegar por dados no Windows Forms
Em um aplicativo do Windows, a maneira mais fácil de navegar por meio de registros em uma fonte de dados é associar um <xref:System.Windows.Forms.BindingSource> componente para a fonte de dados e controles de associação para o <xref:System.Windows.Forms.BindingSource>. Você pode usar o método de navegação internos no <xref:System.Windows.Forms.BindingSource> tais um <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> e <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Usar esses métodos ajustará o <xref:System.Windows.Forms.BindingSource.Position%2A> e <xref:System.Windows.Forms.BindingSource.Current%2A> propriedades do <xref:System.Windows.Forms.BindingSource> adequadamente. Você também pode localizar um item e defina-o como o item atual, definindo o <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Incrementar a posição em uma fonte de dados  
  
1.  Definir o <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade o <xref:System.Windows.Forms.BindingSource> para seus dados associados para a posição do registro para ir para. O exemplo a seguir ilustra o uso de <xref:System.Windows.Forms.BindingSource.MoveNext%2A> método do <xref:System.Windows.Forms.BindingSource> para incrementar o <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade quando o `nextButton` é clicado. O <xref:System.Windows.Forms.BindingSource> está associado a `Customers` tabela de um conjunto de dados `Northwind`.  
  
    > [!NOTE]
    >  Definindo o <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade para um valor para o primeiro ou último registro acima não resultar em um erro, como o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] não permitirá que você defina a posição para um valor fora dos limites da lista. Se, no aplicativo, for importante saber se você passou do primeiro ou do último registro, inclua a lógica para testar se a contagem de elementos de dados será excedida.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Verificar se você passou do final ou do início  
  
1.  Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.BindingSource.PositionChanged>. No manipulador, é possível testar se o valor da posição proposta excedeu a contagem de elementos de dados real.  
  
     O exemplo a seguir ilustra como testar se o último elemento de dados foi alcançado. No exemplo, se você estiver no último elemento, o botão **Próximo** do formulário estará desabilitado.  
  
    > [!NOTE]
    >  Lembre-se de que é necessário alterar a lista em que você está navegando no código, reabilite o botão **Próximo**, para que os usuários possam pesquisar a totalidade da nova lista. Além disso, lembre-se que as opções acima <xref:System.Windows.Forms.BindingSource.PositionChanged> evento específicas <xref:System.Windows.Forms.BindingSource> você estiver trabalhando com precisa ser associado com seu método de manipulação de eventos. A seguir está um exemplo de um método para tratar o <xref:System.Windows.Forms.BindingSource.PositionChanged> evento:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Localizar um item e defini-lo como o item atual  
  
1.  Localize o registro que deseja definir como o item atual. Você pode fazer isso usando o <xref:System.Windows.Forms.BindingSource.Find%2A> método o <xref:System.Windows.Forms.BindingSource>, se sua fonte de dados implementa <xref:System.ComponentModel.IBindingList>. Alguns exemplos de dados de fontes que implementam <xref:System.ComponentModel.IBindingList> são <xref:System.ComponentModel.BindingList%601> e <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Fontes de dados com suporte nos Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Notificação de alteração na vinculação de dados dos Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Vinculação de dados e os Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Associação de dados do Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)

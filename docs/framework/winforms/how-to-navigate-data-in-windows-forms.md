---
title: 'Como: navegar dados'
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
ms.openlocfilehash: 2dd900b652b0ff21ea0eb0dbc5463b22c869ec7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739392"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Como navegar por dados no Windows Forms
Em um aplicativo do Windows, a maneira mais fácil de navegar pelos registros em uma fonte de dados é associar um componente <xref:System.Windows.Forms.BindingSource> à fonte de dados e, em seguida, associar os controles à <xref:System.Windows.Forms.BindingSource>. Você pode usar o método de navegação interno no <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> e <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. O uso desses métodos ajustará as propriedades <xref:System.Windows.Forms.BindingSource.Position%2A> e <xref:System.Windows.Forms.BindingSource.Current%2A> do <xref:System.Windows.Forms.BindingSource> adequadamente. Você também pode encontrar um item e defini-lo como o item atual definindo a propriedade <xref:System.Windows.Forms.BindingSource.Position%2A>.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Incrementar a posição em uma fonte de dados  
  
1. Defina a propriedade <xref:System.Windows.Forms.BindingSource.Position%2A> do <xref:System.Windows.Forms.BindingSource> para os dados associados à posição do registro para a qual ir. O exemplo a seguir ilustra o uso do método <xref:System.Windows.Forms.BindingSource.MoveNext%2A> da <xref:System.Windows.Forms.BindingSource> para incrementar a propriedade <xref:System.Windows.Forms.BindingSource.Position%2A> quando o `nextButton` é clicado. O <xref:System.Windows.Forms.BindingSource> está associado à tabela de `Customers` de um conjunto de `Northwind`de um DataSet.  
  
    > [!NOTE]
    > Definir a propriedade <xref:System.Windows.Forms.BindingSource.Position%2A> como um valor além do primeiro ou último registro não resulta em um erro, pois o .NET Framework não permitirá que você defina a posição como um valor fora dos limites da lista. Se, no aplicativo, for importante saber se você passou do primeiro ou do último registro, inclua a lógica para testar se a contagem de elementos de dados será excedida.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Verificar se você passou do final ou do início  
  
1. Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.BindingSource.PositionChanged>. No manipulador, é possível testar se o valor da posição proposta excedeu a contagem de elementos de dados real.  
  
     O exemplo a seguir ilustra como testar se o último elemento de dados foi alcançado. No exemplo, se você estiver no último elemento, o botão **Próximo** do formulário estará desabilitado.  
  
    > [!NOTE]
    > Lembre-se de que é necessário alterar a lista em que você está navegando no código, reabilite o botão **Próximo**, para que os usuários possam pesquisar a totalidade da nova lista. Além disso, lembre-se de que o evento de <xref:System.Windows.Forms.BindingSource.PositionChanged> acima para o <xref:System.Windows.Forms.BindingSource> específico com o qual você está trabalhando precisa estar associado ao seu método de manipulação de eventos. Veja a seguir um exemplo de um método para manipular o evento de <xref:System.Windows.Forms.BindingSource.PositionChanged>:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Localizar um item e defini-lo como o item atual  
  
1. Localize o registro que deseja definir como o item atual. Você pode fazer isso usando o método <xref:System.Windows.Forms.BindingSource.Find%2A> da <xref:System.Windows.Forms.BindingSource>, se sua fonte de dados implementar <xref:System.ComponentModel.IBindingList>. Alguns exemplos de fontes de dados que implementam <xref:System.ComponentModel.IBindingList> são <xref:System.ComponentModel.BindingList%601> e <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Fontes de dados com suporte nos Windows Forms](data-sources-supported-by-windows-forms.md)
- [Notificação de alteração na vinculação de dados dos Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Associação de dados e o Windows Forms](data-binding-and-windows-forms.md)
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)

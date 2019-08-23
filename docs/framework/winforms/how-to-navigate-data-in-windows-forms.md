---
title: 'Como: navegar por dados nos Windows Forms'
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
ms.openlocfilehash: eb973497f51592b5d34c22e62da77612aec23c35
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964270"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Como: navegar por dados nos Windows Forms
Em um aplicativo do Windows, a maneira mais fácil de navegar pelos registros em uma fonte de dados é associar <xref:System.Windows.Forms.BindingSource> um componente à fonte de dados e, em seguida, <xref:System.Windows.Forms.BindingSource>associar controles ao. Em seguida, você pode usar o método de navegação interno no <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> <xref:System.Windows.Forms.BindingSource.MoveNext%2A> <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, e <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. O uso desses métodos ajustará <xref:System.Windows.Forms.BindingSource.Position%2A> as <xref:System.Windows.Forms.BindingSource.Current%2A> Propriedades e do <xref:System.Windows.Forms.BindingSource> de forma apropriada. Você também pode encontrar um item e defini-lo como o item atual definindo a <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Incrementar a posição em uma fonte de dados  
  
1. Defina a <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade <xref:System.Windows.Forms.BindingSource> do para os dados associados à posição do registro para a qual ir. O exemplo a seguir ilustra o <xref:System.Windows.Forms.BindingSource.MoveNext%2A> uso do método <xref:System.Windows.Forms.BindingSource> do para incrementar a <xref:System.Windows.Forms.BindingSource.Position%2A> propriedade `nextButton` quando o é clicado. O <xref:System.Windows.Forms.BindingSource> é associado `Customers` à tabela de um DataSet `Northwind`.  
  
    > [!NOTE]
    > Definir a <xref:System.Windows.Forms.BindingSource.Position%2A> Propriedade com um valor além do primeiro ou do último registro não resulta em um erro, pois o .NET Framework não permitirá que você defina a posição como um valor fora dos limites da lista. Se, no aplicativo, for importante saber se você passou do primeiro ou do último registro, inclua a lógica para testar se a contagem de elementos de dados será excedida.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Verificar se você passou do final ou do início  
  
1. Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.BindingSource.PositionChanged>. No manipulador, é possível testar se o valor da posição proposta excedeu a contagem de elementos de dados real.  
  
     O exemplo a seguir ilustra como testar se o último elemento de dados foi alcançado. No exemplo, se você estiver no último elemento, o botão **Próximo** do formulário estará desabilitado.  
  
    > [!NOTE]
    > Lembre-se de que é necessário alterar a lista em que você está navegando no código, reabilite o botão **Próximo**, para que os usuários possam pesquisar a totalidade da nova lista. Além disso, lembre-se de <xref:System.Windows.Forms.BindingSource.PositionChanged> que o evento acima <xref:System.Windows.Forms.BindingSource> para o específico com o qual você está trabalhando precisa estar associado ao seu método de manipulação de eventos. Veja a seguir um exemplo de um método para manipular o <xref:System.Windows.Forms.BindingSource.PositionChanged> evento:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Localizar um item e defini-lo como o item atual  
  
1. Localize o registro que deseja definir como o item atual. Você pode fazer isso usando o <xref:System.Windows.Forms.BindingSource.Find%2A> método <xref:System.Windows.Forms.BindingSource>do, se a fonte de dados for <xref:System.ComponentModel.IBindingList>implementada. Alguns exemplos de fontes de dados que <xref:System.ComponentModel.IBindingList> implementam <xref:System.Data.DataView>são <xref:System.ComponentModel.BindingList%601> e.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Fontes de dados com suporte nos Windows Forms](data-sources-supported-by-windows-forms.md)
- [Notificação de alteração na vinculação de dados dos Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Vinculação de dados e os Windows Forms](data-binding-and-windows-forms.md)
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)

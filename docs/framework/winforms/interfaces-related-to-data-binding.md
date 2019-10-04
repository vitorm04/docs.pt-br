---
title: Interfaces relacionadas à associação de dados
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], data-binding interfaces
- INotifyPropertyChanged interface
- IBindingListView interface
- IList interface [Windows Forms], Windows Forms data binding
- IBindingList interface [Windows Forms], Windows Forms data binding
- interfaces [Windows Forms], Windows Forms data binding
- IEditableObject interface [Windows Forms], Windows Forms data binding
- data binding [Windows Forms], interfaces
- IDataErrorInfo interface [Windows Forms], Windows Forms data binding
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
ms.openlocfilehash: 4e40f7ec1922cdf43e6a0b8f5734acaaeefbc514
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834585"
---
# <a name="interfaces-related-to-data-binding"></a>Interfaces relacionadas à associação de dados

Com o ADO.NET, você pode criar várias estruturas de dados diferentes para atender às necessidades de associação do seu aplicativo e aos dados com os quais você está trabalhando. Talvez você queira criar suas próprias classes que forneçam ou consumam dados nos Windows Forms. Esses objetos podem oferecer vários níveis de funcionalidade e complexidade, desde a vinculação de dados básica até o fornecimento de suporte em tempo de design, verificação de erros, notificação de alterações ou até mesmo suporte para uma reversão estruturada das alterações feitas nos próprios dados.

## <a name="consumers-of-data-binding-interfaces"></a>Consumidores de interfaces de associação de dados

As seções a seguir descrevem dois grupos de objetos de interface. O primeiro grupo lista as interfaces que são implementadas nas fontes de dados por autores de fonte de dados. Essas interfaces são projetadas para serem consumidas pelos consumidores de fonte de dados, que são, na maioria dos casos, controles ou componentes dos Windows Forms. O segundo grupo lista as interfaces projetadas para serem usadas por autores de componente. Os autores de componente usam essas interfaces quando estão criando um componente que dá suporte à vinculação de dados a ser consumida pelo mecanismo de vinculação de dados dos Windows Forms. Você pode implementar essas interfaces nas classes associadas ao seu formulário para habilitar a vinculação de dados. Cada caso apresenta uma classe que implementa uma interface que habilita a interação com os dados. As ferramentas de experiência de design de dados de desenvolvimento rápido de aplicativos (RAD) do Visual Studio já aproveitam essa funcionalidade.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Interfaces para implementação por autores de fonte de dados

As seguintes interfaces são projetadas para serem consumidas por controles dos Windows Forms:

- interface <xref:System.Collections.IList>

  Uma classe que implementa a interface <xref:System.Collections.IList> poderia ser uma <xref:System.Array>, <xref:System.Collections.ArrayList> ou <xref:System.Collections.CollectionBase>. Essas são listas indexadas de itens do tipo <xref:System.Object>. Essas listas devem conter tipos homogêneos, porque o primeiro item do índice determina o tipo. <xref:System.Collections.IList> estaria disponível para associação somente em tempo de execução.

  > [!NOTE]
  > Se você quiser criar uma lista de objetos comerciais para associação com Windows Forms, considere usar o <xref:System.ComponentModel.BindingList%601>. O <xref:System.ComponentModel.BindingList%601> é uma classe extensível que implementa as interfaces primárias necessárias para a associação de dados de Windows Forms bidirecional.

- interface <xref:System.ComponentModel.IBindingList>

  Uma classe que implementa a interface <xref:System.ComponentModel.IBindingList> fornece um nível muito mais alto de funcionalidade de vinculação de dados. Essa implementação oferece recursos básicos de classificação e notificação de alteração para quando os itens da lista são alterados (por exemplo, o terceiro item em uma lista de clientes tem uma alteração no campo de endereço), bem como quando a própria lista é alterada (por exemplo, o número de itens na lista aumenta ou diminui). A notificação de alteração é importante se você planeja ter vários controles associados aos mesmos dados e deseja que as alterações de dados feitas em um dos controles sejam propagadas para os outros controles associados.

  > [!NOTE]
  > A notificação de alteração está habilitada para a interface <xref:System.ComponentModel.IBindingList> por meio da propriedade <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A>, que, quando `true`, gera um evento <xref:System.ComponentModel.IBindingList.ListChanged>, indicando que a lista foi alterada ou um item na lista foi alterado.

  O tipo de alteração é descrito pela propriedade <xref:System.ComponentModel.ListChangedType> do parâmetro <xref:System.ComponentModel.ListChangedEventArgs>. Portanto, sempre que o modelo de dados for atualizado, quaisquer exibições dependentes, como outros controles associados à mesma fonte de dados, também serão atualizadas. No entanto, os objetos contidos na lista terão que notificar a lista quando forem alterados para que a lista possa gerar o evento <xref:System.ComponentModel.IBindingList.ListChanged>.

  > [!NOTE]
  > O <xref:System.ComponentModel.BindingList%601> fornece uma implementação genérica da interface <xref:System.ComponentModel.IBindingList>.

- interface <xref:System.ComponentModel.IBindingListView>

  Uma classe que implementa a interface <xref:System.ComponentModel.IBindingListView> fornece toda a funcionalidade de uma implementação de <xref:System.ComponentModel.IBindingList>, bem como a filtragem e a funcionalidade de classificação avançada. Essa implementação oferece filtragem baseada em cadeia de caracteres e classificação de várias colunas com pares de propriedade descritor-direção.

- interface <xref:System.ComponentModel.IEditableObject>

  Uma classe que implementa a interface <xref:System.ComponentModel.IEditableObject> permite que um objeto controle quando as alterações feitas nesse objeto são permanentes. Essa implementação permite que você os métodos <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> e <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>, que permitem reverter as alterações feitas no objeto. Veja a seguir uma breve explicação do funcionamento dos métodos <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> e <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> e como eles funcionam em conjunto com os outros para habilitar uma possível reversão das alterações feitas nos dados:

  - O método <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> sinaliza o início de uma edição em um objeto. Um objeto que implementa essa interface precisará armazenar todas as atualizações após a chamada do método <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> de forma que as atualizações possam ser descartadas se o método <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> for chamado. Na Windows Forms de vinculação de dados, você pode chamar <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> várias vezes dentro do escopo de uma única transação de edição (por exemplo, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). As implementações de <xref:System.ComponentModel.IEditableObject> devem controlar se o <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> já foi chamado e ignorar as chamadas subsequentes para <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Como esse método pode ser chamado várias vezes, é importante que as chamadas subsequentes a ele sejam não destrutivas; ou seja, as chamadas subsequentes <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> não podem destruir as atualizações que foram feitas ou alterar os dados que foram salvos na primeira chamada <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>.

  - O método <xref:System.ComponentModel.IEditableObject.EndEdit%2A> envia por push todas as alterações desde que <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> foi chamado no objeto subjacente, se o objeto estiver no modo de edição no momento.

  - O método <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> descarta as alterações feitas no objeto.

  Para obter mais informações sobre como os métodos <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> e <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> funcionam, consulte [salvar dados de volta no banco de dado](/visualstudio/data-tools/save-data-back-to-the-database).

  Essa noção transacional de funcionalidade de dados é usada pelo controle <xref:System.Windows.Forms.DataGridView>.

- interface <xref:System.ComponentModel.ICancelAddNew>

  Uma classe que implementa a interface <xref:System.ComponentModel.ICancelAddNew> geralmente implementa a interface <xref:System.ComponentModel.IBindingList> e permite que você Reverta uma adição feita à fonte de dados com o método <xref:System.ComponentModel.IBindingList.AddNew%2A>. Se sua fonte de dados implementar a interface <xref:System.ComponentModel.IBindingList>, você também deverá fazer com que ela implemente a interface <xref:System.ComponentModel.ICancelAddNew>.

- interface <xref:System.ComponentModel.IDataErrorInfo>

  Uma classe que implementa a interface <xref:System.ComponentModel.IDataErrorInfo> permite que os objetos ofereçam informações de erro personalizadas a controles associados:

  - A propriedade <xref:System.ComponentModel.IDataErrorInfo.Error%2A> retorna um texto de mensagem de erro geral (por exemplo, "ocorreu um erro").

  - A propriedade <xref:System.ComponentModel.IDataErrorInfo.Item%2A> retorna uma cadeia de caracteres com a mensagem de erro específica da coluna (por exemplo, "o valor na coluna `State` é inválido").

- interface <xref:System.Collections.IEnumerable>

  Uma classe que implementa a interface <xref:System.Collections.IEnumerable> normalmente é consumida por ASP.NET. Windows Forms suporte para essa interface só está disponível por meio do componente <xref:System.Windows.Forms.BindingSource>.

  > [!NOTE]
  > O componente <xref:System.Windows.Forms.BindingSource> copia todos os itens de <xref:System.Collections.IEnumerable> em uma lista separada para fins de associação.

- interface <xref:System.ComponentModel.ITypedList>

  Uma classe de coleções que implementa a interface <xref:System.ComponentModel.ITypedList> fornece a capacidade de controlar a ordem e o conjunto de propriedades expostas ao controle associado.

  > [!NOTE]
  > Quando você implementar o método <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> e a matriz <xref:System.ComponentModel.PropertyDescriptor> não for nula, a última entrada na matriz será o descritor de propriedade que descreve a propriedade da lista que é outra lista de itens.

- interface <xref:System.ComponentModel.ICustomTypeDescriptor>

  Uma classe que implementa a interface <xref:System.ComponentModel.ICustomTypeDescriptor> fornece informações dinâmicas sobre ela mesma. Essa interface é semelhante a <xref:System.ComponentModel.ITypedList>, mas é usada para objetos em vez de listas. Essa interface é usada pelo <xref:System.Data.DataRowView> para projetar o esquema das linhas subjacentes. Uma implementação simples de <xref:System.ComponentModel.ICustomTypeDescriptor> é fornecida pela classe <xref:System.ComponentModel.CustomTypeDescriptor>.

  > [!NOTE]
  > Para dar suporte à associação de tempo de design a tipos que implementam <xref:System.ComponentModel.ICustomTypeDescriptor>, o tipo também deve implementar <xref:System.ComponentModel.IComponent> e existir como uma instância no formulário.

- interface <xref:System.ComponentModel.IListSource>

  Uma classe que implementa a interface <xref:System.ComponentModel.IListSource> permite a associação baseada em lista em objetos que não são de lista. O método <xref:System.ComponentModel.IListSource.GetList%2A> de <xref:System.ComponentModel.IListSource> é usado para retornar uma lista vinculável de um objeto que não herda de <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> é usado pela classe <xref:System.Data.DataSet>.

- interface <xref:System.ComponentModel.IRaiseItemChangedEvents>

  Uma classe que implementa a interface <xref:System.ComponentModel.IRaiseItemChangedEvents> é uma lista vinculável que também implementa a interface <xref:System.ComponentModel.IBindingList>. Essa interface é usada para indicar se o tipo gera eventos <xref:System.ComponentModel.IBindingList.ListChanged> do tipo <xref:System.ComponentModel.ListChangedType.ItemChanged> por meio de sua propriedade <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>.

  > [!NOTE]
  > Você deve implementar o <xref:System.ComponentModel.IRaiseItemChangedEvents> se sua fonte de dados fornecer a propriedade para listar a conversão de eventos descrita anteriormente e estiver interagindo com o componente <xref:System.Windows.Forms.BindingSource>. Caso contrário, o <xref:System.Windows.Forms.BindingSource> também executará a propriedade para listar a conversão de eventos, resultando em um desempenho mais lento.

- interface <xref:System.ComponentModel.ISupportInitialize>

  Um componente que implementa a interface <xref:System.ComponentModel.ISupportInitialize> aproveita as vantagens das otimizações do lote para definir propriedades e inicializar propriedades codependentes. O <xref:System.ComponentModel.ISupportInitialize> contém dois métodos:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> sinaliza que a inicialização do objeto está iniciando.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> sinaliza que a inicialização do objeto está sendo concluída.

- interface <xref:System.ComponentModel.ISupportInitializeNotification>

  Um componente que implementa a interface <xref:System.ComponentModel.ISupportInitializeNotification> também implementa a interface <xref:System.ComponentModel.ISupportInitialize>. Essa interface permite que você notifique outros componentes <xref:System.ComponentModel.ISupportInitialize> de que a inicialização foi concluída. A interface <xref:System.ComponentModel.ISupportInitializeNotification> contém dois membros:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> retorna um valor de `boolean` indicando se o componente é inicializado.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> ocorre quando <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> é chamado.

- interface <xref:System.ComponentModel.INotifyPropertyChanged>

  Uma classe que implementa essa interface é um tipo que aciona um evento quando qualquer um dos seus valores de propriedade são alterados. Essa interface foi projetada para substituir o padrão de ter um evento de alteração para cada propriedade de um controle. Quando usado em um <xref:System.ComponentModel.BindingList%601>, um objeto comercial deve implementar a interface <xref:System.ComponentModel.INotifyPropertyChanged> e a BindingList @ no__t-21 converterá eventos <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> em eventos <xref:System.ComponentModel.BindingList%601.ListChanged> do tipo <xref:System.ComponentModel.ListChangedType.ItemChanged>.

  > [!NOTE]
  > Para que a notificação de alteração ocorra em uma associação entre um cliente associado e uma fonte de dados, o tipo de fonte de dados ligada deve implementar a interface <xref:System.ComponentModel.INotifyPropertyChanged> (preferencial) ou você pode fornecer eventos *propertyName*`Changed` para o tipo associado, mas você Não deve fazer ambos.

### <a name="interfaces-for-implementation-by-component-authors"></a>Interfaces para implementação por autores de componentes

As seguintes interfaces são projetadas para consumo pelo mecanismo de associação de dados dos Windows Forms:

- interface <xref:System.Windows.Forms.IBindableComponent>

  Uma classe que implementa essa interface é um componente de não controle que dá suporte à vinculação de dados. Essa classe retorna as associações de dados e o contexto de associação do componente por meio das propriedades <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> e <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> desta interface.

  > [!NOTE]
  > Se o componente herdar de <xref:System.Windows.Forms.Control>, você não precisará implementar a interface <xref:System.Windows.Forms.IBindableComponent>.

- interface <xref:System.Windows.Forms.ICurrencyManagerProvider>

  Uma classe que implementa a interface <xref:System.Windows.Forms.ICurrencyManagerProvider> é um componente que fornece seu próprio <xref:System.Windows.Forms.CurrencyManager> para gerenciar as associações associadas a esse componente específico. O acesso ao @no__t personalizado é fornecido pela propriedade <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>.

  > [!NOTE]
  > Uma classe que herda de <xref:System.Windows.Forms.Control> gerencia associações automaticamente por meio de sua propriedade <xref:System.Windows.Forms.Control.BindingContext%2A>, portanto, os casos em que você precisa implementar o <xref:System.Windows.Forms.ICurrencyManagerProvider> são bastante raros.

## <a name="see-also"></a>Consulte também

- [Vinculação de dados e os Windows Forms](data-binding-and-windows-forms.md)
- [Como: Criar um controle de associação simples em um Windows Form @ no__t-0
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)

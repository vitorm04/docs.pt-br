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
ms.openlocfilehash: 9f102b584d2ed0b5a9d2bbb0e7ce3f7871ec40b2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046365"
---
# <a name="interfaces-related-to-data-binding"></a>Interfaces relacionadas à associação de dados

Com o ADO.NET, você pode criar várias estruturas de dados diferentes para atender às necessidades de associação do seu aplicativo e aos dados com os quais você está trabalhando. Talvez você queira criar suas próprias classes que forneçam ou consumam dados nos Windows Forms. Esses objetos podem oferecer vários níveis de funcionalidade e complexidade, desde a vinculação de dados básica até o fornecimento de suporte em tempo de design, verificação de erros, notificação de alterações ou até mesmo suporte para uma reversão estruturada das alterações feitas nos próprios dados.

## <a name="consumers-of-data-binding-interfaces"></a>Consumidores de interfaces de associação de dados

As seções a seguir descrevem dois grupos de objetos de interface. O primeiro grupo lista as interfaces que são implementadas nas fontes de dados por autores de fonte de dados. Essas interfaces são projetadas para serem consumidas pelos consumidores de fonte de dados, que são, na maioria dos casos, controles ou componentes dos Windows Forms. O segundo grupo lista as interfaces projetadas para serem usadas por autores de componente. Os autores de componente usam essas interfaces quando estão criando um componente que dá suporte à vinculação de dados a ser consumida pelo mecanismo de vinculação de dados dos Windows Forms. Você pode implementar essas interfaces nas classes associadas ao seu formulário para habilitar a vinculação de dados. Cada caso apresenta uma classe que implementa uma interface que habilita a interação com os dados. As ferramentas de experiência de design de dados de desenvolvimento rápido de aplicativos (RAD) do Visual Studio já aproveitam essa funcionalidade.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Interfaces para implementação por autores de fonte de dados

As seguintes interfaces são projetadas para serem consumidas por controles dos Windows Forms:

- <xref:System.Collections.IList>interface

  Uma classe que implementa a <xref:System.Collections.IList> interface pode ser um <xref:System.Array>, <xref:System.Collections.ArrayList>ou <xref:System.Collections.CollectionBase>. Essas são listas indexadas de itens do <xref:System.Object>tipo. Essas listas devem conter tipos homogêneos, porque o primeiro item do índice determina o tipo. <xref:System.Collections.IList>estaria disponível para associação somente em tempo de execução.

  > [!NOTE]
  > Se você quiser criar uma lista de objetos comerciais para associação com Windows Forms, considere usar o <xref:System.ComponentModel.BindingList%601>. O <xref:System.ComponentModel.BindingList%601> é uma classe extensível que implementa as interfaces primárias necessárias para a ligação de dados de Windows Forms bidirecional.

- <xref:System.ComponentModel.IBindingList>interface

  Uma classe que implementa a <xref:System.ComponentModel.IBindingList> interface fornece um nível muito mais alto de funcionalidade de vinculação de dados. Essa implementação oferece recursos básicos de classificação e notificação de alteração para quando os itens da lista são alterados (por exemplo, o terceiro item em uma lista de clientes tem uma alteração no campo de endereço), bem como quando a própria lista é alterada (por exemplo, o número de itens na lista aumenta ou diminui). A notificação de alteração é importante se você planeja ter vários controles associados aos mesmos dados e deseja que as alterações de dados feitas em um dos controles sejam propagadas para os outros controles associados.

  > [!NOTE]
  > A notificação de alteração <xref:System.ComponentModel.IBindingList> é habilitada para a <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> interface por meio da `true`propriedade que, <xref:System.ComponentModel.IBindingList.ListChanged> quando, gera um evento, indicando que a lista foi alterada ou um item na lista foi alterado.

  O tipo de alteração é descrito pela <xref:System.ComponentModel.ListChangedType> propriedade <xref:System.ComponentModel.ListChangedEventArgs> do parâmetro. Portanto, sempre que o modelo de dados for atualizado, quaisquer exibições dependentes, como outros controles associados à mesma fonte de dados, também serão atualizadas. No entanto, os objetos contidos na lista terão que notificar a lista quando forem alterados para que a lista possa <xref:System.ComponentModel.IBindingList.ListChanged> gerar o evento.

  > [!NOTE]
  > O <xref:System.ComponentModel.BindingList%601> fornece uma implementação genérica <xref:System.ComponentModel.IBindingList> da interface.

- <xref:System.ComponentModel.IBindingListView>interface

  Uma classe que implementa a <xref:System.ComponentModel.IBindingListView> interface fornece toda a funcionalidade de uma implementação do <xref:System.ComponentModel.IBindingList>, bem como a funcionalidade de filtragem e classificação avançada. Essa implementação oferece filtragem baseada em cadeia de caracteres e classificação de várias colunas com pares de propriedade descritor-direção.

- <xref:System.ComponentModel.IEditableObject>interface

  Uma classe que implementa a <xref:System.ComponentModel.IEditableObject> interface permite que um objeto controle quando as alterações feitas nesse objeto são permanentes. Essa implementação lhe dá os <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>métodos, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>e <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> , que permitem reverter as alterações feitas no objeto. Veja a seguir uma breve explicação do funcionamento dos <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>métodos, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>e <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> e como eles funcionam em conjunto com um outro para permitir uma possível reversão das alterações feitas nos dados:

  - O <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> método sinaliza o início de uma edição em um objeto. Um objeto que implementa essa interface precisará armazenar todas as atualizações após a <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> chamada do método de forma que as atualizações possam ser descartadas se o <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> método for chamado. Na Windows Forms de vinculação de dados, você <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> pode chamar várias vezes dentro do escopo de uma única transação de edição ( <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>por <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>exemplo <xref:System.ComponentModel.IEditableObject.EndEdit%2A>,,). As implementações de <xref:System.ComponentModel.IEditableObject> devem controlar se <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> já foram chamadas e ignoradas chamadas subsequentes <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>para. Como esse método pode ser chamado várias vezes, é importante que as chamadas subsequentes a ele sejam não destrutivas; ou seja, as <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> chamadas subsequentes não podem destruir as atualizações que foram feitas ou alterar os dados que foram salvos na <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> primeira chamada.

  - O <xref:System.ComponentModel.IEditableObject.EndEdit%2A> método envia todas as alterações desde <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> que o foi chamado no objeto subjacente, se o objeto estiver no modo de edição no momento.

  - O <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> método descarta todas as alterações feitas no objeto.

  Para obter mais informações sobre como <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>os <xref:System.ComponentModel.IEditableObject.EndEdit%2A>métodos, <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> e funcionam, consulte [salvar dados de volta no banco de dado](/visualstudio/data-tools/save-data-back-to-the-database).

  Essa noção transacional de funcionalidade de dados é usada pelo <xref:System.Windows.Forms.DataGridView> controle.

- <xref:System.ComponentModel.ICancelAddNew>interface

  Uma classe que implementa a <xref:System.ComponentModel.ICancelAddNew> interface geralmente implementa a <xref:System.ComponentModel.IBindingList> interface e permite que você Reverta uma adição feita à fonte de dados com <xref:System.ComponentModel.IBindingList.AddNew%2A> o método. Se sua fonte de dados implementar <xref:System.ComponentModel.IBindingList> a interface, você também deverá fazer com que <xref:System.ComponentModel.ICancelAddNew> ela implemente a interface.

- <xref:System.ComponentModel.IDataErrorInfo>interface

  Uma classe que implementa a <xref:System.ComponentModel.IDataErrorInfo> interface permite que os objetos ofereçam informações de erro personalizadas a controles associados:

  - A <xref:System.ComponentModel.IDataErrorInfo.Error%2A> propriedade retorna texto de mensagem de erro geral (por exemplo, "ocorreu um erro").

  - A <xref:System.ComponentModel.IDataErrorInfo.Item%2A> propriedade retorna uma cadeia de caracteres com a mensagem de erro específica da coluna (por exemplo, "o valor `State` na coluna é inválido").

- <xref:System.Collections.IEnumerable>interface

  Uma classe que implementa a <xref:System.Collections.IEnumerable> interface normalmente é consumida por ASP.net. Windows Forms suporte para essa interface só está disponível por meio <xref:System.Windows.Forms.BindingSource> do componente.

  > [!NOTE]
  > O <xref:System.Windows.Forms.BindingSource> componente copia todos <xref:System.Collections.IEnumerable> os itens em uma lista separada para fins de associação.

- <xref:System.ComponentModel.ITypedList>interface

  Uma classe Collections que implementa a <xref:System.ComponentModel.ITypedList> interface fornece a capacidade de controlar a ordem e o conjunto de propriedades expostas ao controle ligado.

  > [!NOTE]
  > Quando você implementar o <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> método e a <xref:System.ComponentModel.PropertyDescriptor> matriz não for nula, a última entrada na matriz será o descritor de propriedade que descreve a propriedade da lista que é outra lista de itens.

- <xref:System.ComponentModel.ICustomTypeDescriptor>interface

  Uma classe que implementa a <xref:System.ComponentModel.ICustomTypeDescriptor> interface fornece informações dinâmicas sobre si mesma. Essa interface é semelhante a <xref:System.ComponentModel.ITypedList> , mas é usada para objetos em vez de listas. Essa interface é usada pelo <xref:System.Data.DataRowView> para projetar o esquema das linhas subjacentes. Uma implementação simples do <xref:System.ComponentModel.ICustomTypeDescriptor> é fornecida <xref:System.ComponentModel.CustomTypeDescriptor> pela classe.

  > [!NOTE]
  > Para dar suporte à associação de tempo de design a <xref:System.ComponentModel.ICustomTypeDescriptor>tipos que implementam, o <xref:System.ComponentModel.IComponent> tipo também deve implementar e existir como uma instância no formulário.

- <xref:System.ComponentModel.IListSource>interface

  Uma classe que implementa a <xref:System.ComponentModel.IListSource> interface do habilita a associação baseada em lista em objetos que não são de lista. O <xref:System.ComponentModel.IListSource.GetList%2A> método de <xref:System.ComponentModel.IListSource> é usado para retornar uma lista vinculável de um objeto que não herda de <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource>é usado pela <xref:System.Data.DataSet> classe.

- <xref:System.ComponentModel.IRaiseItemChangedEvents>interface

  Uma classe que implementa a <xref:System.ComponentModel.IRaiseItemChangedEvents> interface é uma lista vinculável que também implementa <xref:System.ComponentModel.IBindingList> a interface. Essa interface é usada para indicar se o tipo gera <xref:System.ComponentModel.IBindingList.ListChanged> eventos do tipo <xref:System.ComponentModel.ListChangedType.ItemChanged> por meio <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> de sua propriedade.

  > [!NOTE]
  > Você deve implementar o <xref:System.ComponentModel.IRaiseItemChangedEvents> se sua fonte de dados fornecer a propriedade para listar a conversão de eventos descrita anteriormente e estiver <xref:System.Windows.Forms.BindingSource> interagindo com o componente. Caso contrário, <xref:System.Windows.Forms.BindingSource> o também executará a propriedade para listar a conversão de eventos, resultando em um desempenho mais lento.

- <xref:System.ComponentModel.ISupportInitialize>interface

  Um componente que implementa a <xref:System.ComponentModel.ISupportInitialize> interface aproveita as vantagens das otimizações do lote para definir propriedades e inicializar propriedades codependentes. O <xref:System.ComponentModel.ISupportInitialize> contém dois métodos:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>sinaliza que a inicialização do objeto está iniciando.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>sinaliza que a inicialização do objeto está sendo concluída.

- <xref:System.ComponentModel.ISupportInitializeNotification>interface

  Um componente que implementa a <xref:System.ComponentModel.ISupportInitializeNotification> interface também implementa a <xref:System.ComponentModel.ISupportInitialize> interface. Essa interface permite que você notifique outros <xref:System.ComponentModel.ISupportInitialize> componentes que a inicialização foi concluída. A <xref:System.ComponentModel.ISupportInitializeNotification> interface contém dois membros:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A>Retorna um `boolean` valor que indica se o componente é inicializado.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized>ocorre quando <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> é chamado.

- <xref:System.ComponentModel.INotifyPropertyChanged>interface

  Uma classe que implementa essa interface é um tipo que aciona um evento quando qualquer um dos seus valores de propriedade são alterados. Essa interface foi projetada para substituir o padrão de ter um evento de alteração para cada propriedade de um controle. Quando usado em um <xref:System.ComponentModel.BindingList%601>, um objeto comercial deve implementar a <xref:System.ComponentModel.INotifyPropertyChanged> \`interface e a BindingList 1 converterá <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> eventos em <xref:System.ComponentModel.BindingList%601.ListChanged> eventos do tipo <xref:System.ComponentModel.ListChangedType.ItemChanged>.

  > [!NOTE]
  > Para que a notificação de alteração ocorra em uma associação entre um cliente associado e uma fonte de dados, o tipo de fonte de dados <xref:System.ComponentModel.INotifyPropertyChanged> ligada deve implementar a interface (preferencial) ou fornecer eventos *PropertyName* `Changed` para o tipo associado, Mas você não deve fazer ambos.

### <a name="interfaces-for-implementation-by-component-authors"></a>Interfaces para implementação por autores de componentes

As seguintes interfaces são projetadas para consumo pelo mecanismo de associação de dados dos Windows Forms:

- <xref:System.Windows.Forms.IBindableComponent>interface

  Uma classe que implementa essa interface é um componente de não controle que dá suporte à vinculação de dados. Essa classe retorna as associações de dados e o contexto de associação do componente por <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> meio <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> das propriedades e desta interface.

  > [!NOTE]
  > Se o seu componente for <xref:System.Windows.Forms.Control>herdado de, você não precisará <xref:System.Windows.Forms.IBindableComponent> implementar a interface.

- <xref:System.Windows.Forms.ICurrencyManagerProvider>interface

  Uma classe que implementa a <xref:System.Windows.Forms.ICurrencyManagerProvider> interface é um componente que fornece sua própria <xref:System.Windows.Forms.CurrencyManager> para gerenciar as associações associadas a esse componente específico. <xref:System.Windows.Forms.CurrencyManager> O<xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> acesso ao personalizado é fornecido pela propriedade.

  > [!NOTE]
  > Uma classe que herda de <xref:System.Windows.Forms.Control> gerencia associações automaticamente por meio de <xref:System.Windows.Forms.Control.BindingContext%2A> sua propriedade, portanto, os casos em que você precisa <xref:System.Windows.Forms.ICurrencyManagerProvider> implementar o são bastante raros.

## <a name="see-also"></a>Consulte também

- [Vinculação de dados e os Windows Forms](data-binding-and-windows-forms.md)
- [Como: Criar um controle de associação simples em um formulário do Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Associação de dados do Windows Forms](windows-forms-data-binding.md)

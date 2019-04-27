---
title: Usando as ações implementar o comportamento do lado do servidor
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 4467d52df5dbb134947111e96782e257eef253e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875245"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Usando as ações implementar o comportamento do lado do servidor

As ações OData fornecem uma maneira de implementar um comportamento que age mediante um recurso recuperado de um serviço OData. Por exemplo, considere um filme como um recurso. Há muitas coisas que você pode fazer com um filme: check-out, avaliar/comentar ou check-in. Estes são exemplos de Ações que podem ser implementadas por um WCF Data Service que gerencia filmes. As ações são descritas em uma resposta OData que contém um recurso no qual a Ação pode ser invocada. Quando um usuário solicita um recurso que representa um filme, a resposta retornada do WCF Data Service contém informações sobre as Ações disponíveis para esse recurso. A disponibilidade de uma Ação pode depender do estado do serviço de dados ou recurso. Por exemplo, quando um filme fez o check-out, ele não pode ter o check-out feito por outro usuário. Os clientes podem invocar uma ação somente especificando uma URL. Por exemplo, `http://MyServer/MovieService.svc/Movies(6)` identificaria um filme digital específico e `http://MyServer/MovieService.svc/Movies(6)/Checkout` faria para invocar a ação do filme específico. As ações permitem que você exponha o modelo de serviço sem expor o modelo de dados. Continuando o exemplo do serviço de filmes, talvez você queira permitir que um usuário avalie um filme, mas não expor os dados de avaliação diretamente como um recurso. Você pode implementar uma Ação de Avaliação para permitir que o usuário avalie um filme, mas não acessar os dados de avaliação diretamente como um recurso.
  
## <a name="implementing-an-action"></a>Implementando uma ação  
 Para implementar uma ação de serviço, você deve implementar o <xref:System.IServiceProvider>, [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)), e [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) interfaces. <xref:System.IServiceProvider> permite que o WCF Data Services para obter sua implementação de [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)). [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) permite que o WCF Data Services criar, localizar, descreva e chame ações de serviço. [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) permite que você invocar o código que implementa o comportamento das ações de serviço e obter os resultados, se houver. Lembre-se de que o WCF Data Services são Serviços do WCF por chamada, uma nova instância do serviço será criada cada vez que o serviço for chamado.  Verifique se nenhum trabalho desnecessário é feito quando o serviço é criado.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 O <xref:System.IServiceProvider> contém um método chamado <xref:System.IServiceProvider.GetService%2A>. Este método é chamado pelo WCF Data Services para recuperar um número de provedores de serviços, inclusive provedores de serviços de metadados e provedores de ação de serviço de dados. Quando for solicitado para um provedor de ação do serviço de dados, retornar seu [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) implementação.  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) contém métodos que permitem que você recupere informações sobre as ações disponíveis. Quando você implementa [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) está aumentando os metadados para o serviço que é definido pela implementação do seu serviço do [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) com ações e manipulação de expedição a essas ações conforme apropriado.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 O [AdvertiseServiceAction método](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859971(v=vs.103)) é chamado para determinar quais ações estão disponíveis para o recurso especificado. Este método é chamado apenas para as ações que não estão sempre disponíveis. É usado para verificar se a ação deve ser incluída na resposta OData com base no estado do recurso que está sendo solicitado ou no estado do serviço. Como essa verificação é feita cabe completamente a você. Se é caro calcular a disponibilidade e o recurso atual estiver em um feed, é aceitável ignorar a verificação e divulgar a ação. O parâmetro `inFeed` estará definido como `true` se o recurso atual que está sendo retornado fizer parte de um feed.  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859940(v=vs.103)) é chamado para criar um [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) que contém um delegado que encapsula o código que implementa o comportamento da ação. Isso cria o [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) da instância, mas não chama a ação. As ações do WCF Data Service têm efeitos colaterais e precisam trabalhar junto com o Provedor de Atualização para salvar essas alterações no disco. O [IDataServiceInvokable.Invoke](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859924(v=vs.103)) método é chamado de SaveChanges () de atualização do provedor método é chamado.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Esse método retorna uma coleção de [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) instâncias que representam todas as ações que expõe um WCF Data Service. [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) é a representação de metadados de uma ação, que inclui informações como o nome da ação, seus parâmetros e seu tipo de retorno.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Esse método retorna uma coleção de todos os [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) instâncias que podem ser associadas ao tipo de parâmetro de associação especificadas. Em outras palavras, todos os [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))s que podem atuar no tipo de recurso especificado (também chamado de tipo de parâmetro de associação). Isso é usado quando o serviço retorna um recurso para incluir informações sobre as ações que podem ser invocadas em relação a esse recurso. Esse método deve retornar apenas as ações que podem ser associadas ao tipo de parâmetro de associação exato (sem tipo derivado). Este método é chamado uma vez por solicitação por tipo encontrado e o resultado é armazenado em cache pelo WCF Data Services.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Esse método pesquisa um especificado [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) e retorna `true` se o [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) for encontrado. Se encontrado, o [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) é retornado na `serviceAction` `out` parâmetro.  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Essa interface oferece um modo de executar uma ação do WCF Data Service. Ao implementar IDataServiceInvokable, você é responsável por 3 coisas:  
  
1. Capturar e potencialmente fazer o marshaling dos parâmetros  
  
2. Distribuir os parâmetros para o código que realmente implementa a Ação quando Invoke() é chamado  
  
3. Armazenar os resultados de Invoke() para que eles possam ser recuperados usando GetResult()  
  
 Os parâmetros podem ser passados como tokens. Isso ocorre porque é possível escrever um provedor de serviços de dados que funcione com os tokens que representam recursos. Se for esse o caso, você precisará converter (realizar marshaling) esses tokens em recursos reais antes de distribuir para a ação real. Depois que tiver sido realizado o marshaling do parâmetro, ele deverá estar em um estado editável de forma que as alterações ao recurso que ocorram quando a ação é invocada sejam salvas e gravadas em disco.  
  
 Essa interface requer dois métodos: Invoke e GetResult adequados. Invoke chama o representante que implementa o comportamento da ação e GetResult retorna o resultado da ação.  
  
## <a name="invoking-a-wcf-data-service-action"></a>Chamar uma ação do WCF Data Service  
 As ações são chamadas usando uma solicitação HTTP POST. O URL especifica o recurso seguido pelo nome da ação. Os parâmetros são passados no corpo da solicitação. Por exemplo, se houve um serviço chamado MovieService que expôs uma ação chamada Avaliar. Você pode usar a seguinte URL para chamar a ação Avaliar em um filme específico:  
  
 `http://MovieServer/MovieService.svc/Movies(1)/Rate`
  
 Movies(1) especifica o filme que você deseja avaliar e Avaliar especifica a ação. O valor real da avaliação estará no corpo da solicitação de HTTP conforme mostrado no seguinte exemplo:  
  
```  
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
```  
  
> [!WARNING]
> O código de exemplo acima somente funcionará com o WCF Data Services 5.2 e posterior que tem o suporte para JSON light. Se estiver usando uma versão anterior do WCF Data Services, você deverá especificar o tipo de conteúdo detalhado de json da seguinte maneira: `application/json;odata=verbose`.  
  
 Como alternativa, você pode chamar uma ação usando o cliente do WCF Data Services conforme mostrado no seguinte snippet de código.  
  
```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
//...  
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```
  
 No snippet de código acima, a classe `MoviesModel` foi gerada com o Visual Studio para Adicionar a Referência de Serviço a um WCF Data Service.  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)
- [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)
- [Desenvolvendo e implantando o WCF Data Services](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)
- [Provedores de serviços de dados personalizados](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)

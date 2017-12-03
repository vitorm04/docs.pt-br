---
title: Consumir feeds de OData de um fluxo de trabalho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c538ead434a7e5abe85f0d28ac7bf7edae98cbb8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Consumir feeds de OData de um fluxo de trabalho
WCF Services Data é um componente de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] que permite que você crie serviços que usam o protocolo aberto de dados (OData) para exibir e receber dados sobre a Web ou intranet usando a semântica de transferência representacional de estado (RESTO). OData expõem dados como recursos que são endereçáveis por URIs. Qualquer aplicativo pode interagir com um serviço de dados com base OData- se pode enviar uma solicitação HTTP e processar o avanço de OData que um serviço de dados retorna. Além disso, Data WCF Services inclui bibliotecas de cliente que fornece uma experiência mais rica de programação quando você consome feeds de OData de aplicativos de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] . Este tópico fornece uma visão geral de consumir um avanço de OData em um fluxo de trabalho com e sem o uso das bibliotecas de cliente.  
  
## <a name="using-the-sample-northwind-odata-service"></a>Usando o serviço de OData de exemplo Northwind  
 Os exemplos neste tópico usam o exemplo Northwind, serviço de dados localizado em [http://services.odata.org/Northwind/Northwind.svc/](http://go.microsoft.com/fwlink/?LinkID=187426). Este serviço é fornecido como parte do [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185248) e fornece acesso somente leitura para os dados de exemplo Northwind. Se o acesso de gravação for desejado, ou se um serviço de dados WCF local for desejado, você pode seguir as etapas da [WCF Data Services Quickstart](http://go.microsoft.com/fwlink/?LinkID=131076) para criar um serviço OData local que fornece acesso ao banco de dados Northwind. Se você segue o quickstart, substitua o URI local para aquele fornecido no exemplo de código neste tópico.  
  
## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>Consumir um avanço de OData usando as bibliotecas de cliente  
 Data WCF Services inclui as bibliotecas de cliente para permitir que consomem mais facilmente um avanço de OData de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] e dos aplicativos cliente. Essas bibliotecas simplificam o envio e o recebimento de mensagens HTTP. Elas também convertem a carga da mensagem em objetos CLR que representam dados de entidade. As bibliotecas de cliente apresentam as duas classes principais <xref:System.Data.Services.Client.DataServiceContext> e <xref:System.Data.Services.Client.DataServiceQuery%601>. Essas classes permitem consultar um serviço de dados e, em seguida, trabalhar com os dados de entidade retornada como objetos CLR. Esta seção aborda duas abordagens para criar as atividades que usam as bibliotecas de cliente.  
  
### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>Adicionando uma referência de serviço a WCF Services Data  
 Para gerar as bibliotecas de cliente do Northwind, você pode usar o **adicionar referência de serviço** da caixa de diálogo [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] para adicionar uma referência para o serviço Northwind OData.  
  
 ![Adicionar referência de serviço](../../../docs/framework/windows-workflow-foundation/media/addservicereferencetonorthwindodataservice.gif "AddServiceReferencetoNorthwindODataService")  
  
 Observe que não há nenhuma operação de serviço exposta pelo serviço e, no **serviços** lista há itens que representam as entidades expostas pelo serviço de dados Northwind. Quando a referência de serviço é adicionada, as classes serão geradas para essas entidades e podem ser usadas no código do cliente. Os exemplos neste tópico usam essas classes e a classe de `NorthwindEntities` para executar consultas.  
  
> [!NOTE]
>  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Gerando a biblioteca de cliente do serviço de dados (WCF Data Services)](http://go.microsoft.com/fwlink/?LinkID=191611).  
  
### <a name="using-asynchronous-methods"></a>Usando métodos assíncronos  
 Para corrigir os problemas possíveis de latência que podem ocorrer ao acessar recursos sobre a Web, nós seja recomendável acessar WCF Services Data de forma assíncrona. As bibliotecas de cliente de Data WCF Services incluem métodos assíncronos para chamar consultas, e [!INCLUDE[wf](../../../includes/wf-md.md)] fornece a classe de <xref:System.Activities.AsyncCodeActivity> para criar atividades assíncronas. <xref:System.Activities.AsyncCodeActivity> derivado atividades pode ser escrito para tirar proveito de classes de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] que possuem métodos assíncronos, ou o código a ser executado de forma assíncrona pode ser colocado em um método e ser chamado usando um representante. Esta seção fornece dois exemplos de uma atividade derivada <xref:System.Activities.AsyncCodeActivity> ; um que usa os métodos assíncronos das bibliotecas de cliente de Data WCF Services e um que usa um representante.  
  
> [!NOTE]
>  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Operações assíncronas (WCF Data Services)](http://go.microsoft.com/fwlink/?LinkId=193396) e [criando atividades assíncrono](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
### <a name="using-client-library-asynchronous-methods"></a>Usando métodos assíncronos de biblioteca de cliente  
 A classe de <xref:System.Data.Services.Client.DataServiceQuery%601> fornece <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> e métodos de <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> para ver um serviço de OData de forma assíncrona. Esses métodos podem ser chamados de <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> e as substituições de <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> de uma classe derivada de <xref:System.Activities.AsyncCodeActivity> . Quando o <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> retorna de substituição, o fluxo de trabalho pode ficar ocioso (mas não persistem), e quando o trabalho assíncrona é concluído, <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> é chamado pelo tempo de execução.  
  
 No exemplo a seguir, uma atividade de `OrdersByCustomer` é definida que possui dois argumentos conectados. O argumento de `CustomerId` representa o cliente que identifica qual as regras para retornar, e o argumento de `ServiceUri` representa o URI de serviço de OData a ser consultado. Porque a atividade deriva de `AsyncCodeActivity<IEnumerable<Order>>` há também um argumento de saída de <xref:System.Activities.Activity%601.Result%2A> que é usado para retornar os resultados da consulta. A substituição de <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> cria uma consulta LINQ que selecionar todos os pedidos do cliente especificado. Esta consulta é especificado como <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> de <xref:System.Activities.AsyncCodeActivityContext>passado, e o método de <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> de consulta é então chamado. Observe que o retorno de chamada e indica que é passado em <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> de consulta são aqueles que são passados ao método de <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> de atividade. Quando a consulta terminou de executar, o método de <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> da atividade é chamado. A consulta é recuperada de <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, e o método de <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> de consulta é então chamado. Esse método retorna <xref:System.Collections.Generic.IEnumerable%601> do tipo de entidade especificado; nesse caso `Order`. Como `IEnumerable<Order>` é o tipo genérico do <xref:System.Activities.AsyncCodeActivity%601>, esse `IEnumerable` é definido como o <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> da atividade.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]  
  
 No exemplo a seguir, a atividade de `OrdersByCustomer` recuperar uma lista de pedidos para o cliente especificado, e então uma atividade de <xref:System.Activities.Statements.ForEach%601> enumera os pedidos retornados e grava a data de cada pedido no console.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]  
  
 Quando esse fluxo de trabalho é chamado, os seguintes dados são gravados no console:  
  
 **Chamando o WCF Data Services...**  
**8/25/1997**   
**10/3/1997**   
**10/13/1997**   
**1/15/1998**   
**3/16/1998**   
**4/9/1998**    
> [!NOTE]
>  Se uma conexão com o servidor de OData não pode ser estabelecida, você receberá uma exceção similar à seguinte exceção:  
>   
>  Exceção sem tratamento: System.InvalidOperationException: Ocorreu um erro ao processar a solicitação. ---> System.Net.WebException: Incapaz de se conectar ao servidor remoto --- System.Net.Sockets.SocketException: Uma tentativa> de conexão falhou porque a parte conectada não respondeu corretamente após um período de tempo, ou conexão estabelecida falhou porque o host conectado não respondeu.  
  
 Se qualquer processamento adicional dos dados retornados pela consulta é necessário, pode ser feito em uma substituição de <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> de atividade. O <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> e o <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> são chamados usando o segmento de fluxo de trabalho, e qualquer código nessas alternativas não funciona de forma assíncrona. Se o processamento adicional é abrangente ou longo, ou os resultados da consulta são paginados, você deve considerar a abordagem discutido na seção a seguir, que usa um representante para executar a consulta e executar processamento adicional de forma assíncrona.  
  
### <a name="using-a-delegate"></a>Usando um representante  
 Além de chamar o método assíncrona de uma classe de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] , uma atividade baseadas em <xref:System.Activities.AsyncCodeActivity>também pode definir a lógica assíncrono em um de seus métodos. Este método é especificado usando um delegado em uma substituição de <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> de atividade. Quando o método retorna, o tempo de execução chama a substituição de <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> de atividade. Para chamar um serviço de OData de um fluxo de trabalho, esse método pode ser usado para ver o serviço e fornecer qualquer processamento adicional.  
  
 No exemplo a seguir, uma atividade de `ListCustomers` é definida. Esta atividade consulta o serviço de dados de exemplo Northwind e retorna `List<Customer>` que contém todos os clientes na base de dados Northwind. Assíncrono o trabalho é executado pelo método de `GetCustomers` . Este método consulta o serviço para todos os clientes, e copiar em `List<Customer>`. Então verifica para ver se os resultados são paginados. Em caso afirmativo, consulte o serviço para a próxima página de resultados, adicioná-los à lista, e continua-o até que todos os dados do cliente sejam recuperados.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]paginação no WCF Data Services, consulte. [Como: carregar resultados (WCF Data Services) paginados](http://go.microsoft.com/fwlink/?LinkId=193452).  
  
 Depois que todos os clientes são adicionados, a lista será retornada. O método de `GetCustomers` é especificado em uma substituição de <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> de atividade. Desde que o método possui um valor de retorno, `Func<string, List<Customer>>` é criado para especificar o método.  
  
> [!NOTE]
>  Se o método que executa o trabalho assíncrono não tem um valor de retorno, um <xref:System.Action> é usado em vez de um <!--zz <xref:System.Func> --> `System.Func`. Para obter exemplos de criação de um exemplo de assíncrono usando os dois métodos, consulte [criando atividades assíncronos](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 Isso <!--zz <xref:System.Func> --> `System.Func` é atribuído para o <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>e, em seguida, `BeginInvoke` é chamado. Desde que o método a ser chamado não tem acesso ao ambiente de atividade de argumentos, o valor do argumento de `ServiceUri` é passado como o primeiro parâmetro, juntamente com o retorno de chamada e indica que foram passados em <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Quando `GetCustomers` retorna, o tempo de execução chama <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. O código em <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> recupera o representante de <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, chama `EndInvoke`, e retorna o resultado, que é a lista de clientes retornados pelo método de `GetCustomers` .  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#200](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]  
  
 No exemplo a seguir, a atividade de `ListCustomers` recuperar uma lista de clientes, e então uma atividade de <xref:System.Activities.Statements.ForEach%601> enumera-os e escreve-ao nome do nome da empresa e de contatos de cada cliente no console.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]  
  
 Quando esse fluxo de trabalho é chamado, os seguintes dados são gravados no console. Como esta consulta retorna vários clientes, somente a parte de saída é mostrada aqui.  
  
 **Chamando o WCF Data Services...**  
**Alfreds Futterkiste, entre em contato com: Anders de Maria**   
**Ana Trujillo Emparedados y helados, entre em contato com: Ana Trujillo**   
**Taquería António Moreno, entre em contato com: António Moreno**   
**Em torno de haste, entre em contato com: Thomas Hardy**   
**Berglunds snabbköp, entre em contato com: Christina Berglund**   
**...**    
## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>Consumir um avanço de OData sem usar as bibliotecas de cliente  
 OData expõem dados como recursos que são endereçáveis por URIs. Quando você usa bibliotecas de cliente essas URIs são criados para você, mas você não tem que usar as bibliotecas de cliente. Se desejado, serviços de OData podem ser acessados diretamente sem usar as bibliotecas de cliente. Para não usar as bibliotecas de cliente o local do serviço e os dados desejados são especificados por um URI e os resultados são retornados em resposta a solicitação HTTP. Esses dados brutos podem ser processados ou manipulado na forma desejada. Uma maneira para recuperar os resultados de uma consulta de OData é usando a classe de <xref:System.Net.WebClient> . Nesse exemplo, o nome de contato para o cliente representado pela chave ALFKI é recuperado.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]  
  
 Quando esse código é executado, a saída a seguir são exibidas no console:  
  
 **Dados brutos retornados:**  
**\<? versão xml = "1.0" encoding = "utf-8" autônomo = "yes"? >**   
**\<ContactName xmlns = "http://schemas.microsoft.com/ado/2007/08/dataservices" > Maria Anders\</ContactName >** em um fluxo de trabalho, o código deste exemplo pode ser incorporado a <xref:System.Activities.CodeActivity.Execute%2A> substituição de um <xref:System.Activities.CodeActivity>-base atividade personalizada, mas a mesma funcionalidade também pode ser feita usando o <xref:System.Activities.Expressions.InvokeMethod%601> atividade. A atividade de <xref:System.Activities.Expressions.InvokeMethod%601> permite que autores de fluxo de trabalho para chamar métodos estáticos e de instância de uma classe, e também tem uma opção chamar o método de forma assíncrona especificado. No exemplo a seguir, uma atividade de <xref:System.Activities.Expressions.InvokeMethod%601> é configurada para chamar o método de <xref:System.Net.WebClient.DownloadString%2A> da classe de <xref:System.Net.WebClient> e retornar uma lista de clientes.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> pode chamar métodos estáticos e de instância de uma classe. Desde que <xref:System.Net.WebClient.DownloadString%2A> é um método de instância da classe de <xref:System.Net.WebClient> , uma nova instância da classe <xref:System.Net.WebClient> é especificada para <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>. `DownloadString` é especificado como <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, o URI que contém a consulta é especificado na coleção de <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> , e o valor de retorno é atribuído ao valor de <xref:System.Activities.Activity%601.Result%2A> . O valor de <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> é definido como `true`, o que significa que a chamada ao método executará de forma assíncrona com relação ao fluxo de trabalho. No exemplo a seguir, um fluxo de trabalho é construído que usa a atividade de <xref:System.Activities.Expressions.InvokeMethod%601> para ver o serviço de dados de exemplo Northwind para uma lista de pedidos para um cliente específico, e os dados retornados são gravados no console.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]  
  
 Quando esse fluxo de trabalho é chamado, a seguinte saída é exibida no console. Como esta consulta retorna vários pedidos, somente a parte de saída é mostrada aqui.  
  
 **Chamando o WCF Data Services...**  
**Dados brutos retornados:**   
**\<? versão xml = "1.0" encoding = "utf-8" autônomo = "yes"? >**   
**\<feed**   
 **XML: base = "http://services.odata.org/Northwind/Northwind.svc/"**  
 **xmlns:d = "http://schemas.microsoft.com/ado/2007/08/dataservices"**  
 **xmlns:m = "http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"**  
 **xmlns = "http://www.w3.org/2005/Atom" >**  
 **\<tipo de título = "text" > pedidos \< /title >**  
 **\<ID > http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/pedidos\</id >**  
 **\<atualizado > 2010-05-19T19:37:07Z\</ atualizada >**  
 **\<link rel = "auto" title = "Orders" href = "Orders" / >**  
 **\<entrada >**  
 **\<ID > http://services.odata.org/Northwind/Northwind.svc/Orders (10643)\</id >**  
 **\<tipo de título = "text" > \< /title >**  
 **\<atualizado > 2010-05-19T19:37:07Z\</ atualizada >**  
 **\<Autor >**  
 **\<nome / >**  
 **\</Author >**  
 **\<link rel = "edit" title = "Order" href="Orders(10643)" / >**  
 **\<link rel = "http://schemas.microsoft.com/ado/2007/08/dataservices/related/Customer"**  
 **tipo = "application/atom + xml; digite = entry" title = "Customer" href = "Pedidos (10643) / cliente" / >**  
**...**  Este exemplo fornece um método que os autores de aplicativo de fluxo de trabalho podem usar para receber os dados brutos retornados de um serviço de OData. [!INCLUDE[crabout](../../../includes/crabout-md.md)]acessando o WCF Data Services usando URIs, consulte [acessar recursos de serviço de dados (WCF Data Services)](http://go.microsoft.com/fwlink/?LinkId=193397) e [OData: convenções de URI](http://go.microsoft.com/fwlink/?LinkId=185564).

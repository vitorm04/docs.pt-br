---
title: Chamando operações de serviço (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 1b8a00c7716a60daec4e4f6af6ae8e3a7a45e943
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346170"
---
# <a name="calling-service-operations-wcf-data-services"></a>Chamando operações de serviço (WCF Data Services)
O Protocolo Open Data (OData) define as operações de serviço para um serviço de dados. WCF Data Services permite que você defina operações como métodos no serviço de dados. Assim como outros recursos de serviço de dados, essas operações de serviço são endereçadas usando URIs. Uma operação de serviço pode retornar coleções de tipos de entidade, instâncias de tipo de entidade única e tipos primitivos, como inteiro e cadeia de caracteres. Uma operação de serviço também pode retornar `null` (`Nothing` em Visual Basic). A biblioteca de cliente WCF Data Services pode ser usada para acessar as operações de serviço que dão suporte a solicitações HTTP GET. Esses tipos de operações de serviço são definidos como métodos que têm o <xref:System.ServiceModel.Web.WebGetAttribute> aplicado. Para obter mais informações, consulte [operações de serviço](service-operations-wcf-data-services.md).  
  
 As operações de serviço são expostas nos metadados retornados por um serviço de dados que implementa o OData. Nos metadados, as operações de serviço são representadas como elementos de `FunctionImport`. Ao gerar o <xref:System.Data.Services.Client.DataServiceContext>fortemente tipado, as ferramentas Adicionar Referência de Serviço e DataSvcUtil. exe ignoram esse elemento. Por isso, você não encontrará um método no contexto que possa ser usado para chamar uma operação de serviço diretamente. No entanto, você ainda pode usar o cliente WCF Data Services para chamar operações de serviço de uma destas duas maneiras:  
  
- Chamando o método <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> no <xref:System.Data.Services.Client.DataServiceContext>, fornecendo o URI da operação de serviço, juntamente com quaisquer parâmetros. Esse método é usado para chamar qualquer operação de obtenção de serviço.  
  
- Usando o método <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> no <xref:System.Data.Services.Client.DataServiceContext> para criar um objeto <xref:System.Data.Services.Client.DataServiceQuery%601>. Ao chamar <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, o nome da operação de serviço é fornecido para o parâmetro `entitySetName`. Esse método retorna um objeto <xref:System.Data.Services.Client.DataServiceQuery%601> que chama a operação de serviço quando enumerado ou quando o método <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> é chamado. Esse método é usado para chamar operações GET Service que retornam uma coleção. Um único parâmetro pode ser fornecido usando o método <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>. O objeto de <xref:System.Data.Services.Client.DataServiceQuery%601> retornado por esse método pode ser mais composto como qualquer objeto de consulta. Para obter mais informações, consulte [consultando o serviço de dados](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Considerações para chamar operações de serviço  
 As considerações a seguir se aplicam ao usar o cliente WCF Data Services para chamar operações de serviço.  
  
- Ao acessar o serviço de dados de forma assíncrona, você deve usar os métodos equivalentes <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A>assíncronos /<xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> nos métodos <xref:System.Data.Services.Client.DataServiceContext> ou <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> no <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
- A biblioteca de cliente WCF Data Services não pode materializar os resultados de uma operação de serviço que retorna uma coleção de tipos primitivos.  
  
- A biblioteca de cliente WCF Data Services não dá suporte à chamada de operações de serviço POST. As operações de serviço que são chamadas por um HTTP POST são definidas usando o <xref:System.ServiceModel.Web.WebInvokeAttribute> com o parâmetro `Method="POST"`. Para chamar uma operação de serviço usando uma solicitação HTTP POST, você deve usar um <xref:System.Net.HttpWebRequest>.  
  
- Você não pode usar <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> para chamar uma operação GET Service que retorna um único resultado, de uma entidade ou tipo primitivo, ou que requer mais de um parâmetro de entrada. Em vez disso, você deve chamar o método <xref:System.Data.Services.Client.DataServiceContext.Execute%2A>.  
  
- Considere a criação de um método de extensão na classe parcial de <xref:System.Data.Services.Client.DataServiceContext> fortemente tipada, que é gerada pelas ferramentas, que usa o método <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> ou <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> para chamar uma operação de serviço. Isso permite que você chame operações de serviço diretamente do contexto. Para obter mais informações, consulte a postagem no blog [operações de serviço e o cliente de WCF Data Services](https://blogs.msdn.microsoft.com/astoriateam/2010/05/26/service-operations-and-the-wcf-data-services-client/).  
  
- Quando você usa <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> para chamar uma operação de serviço, a biblioteca de cliente automaticamente escapa os caracteres fornecidos para o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> executando a codificação por porcentagem de caracteres reservados, como e comercial (&) e saída de aspas simples em cadeias de caractere. No entanto, ao chamar um dos métodos *Execute* para chamar uma operação de serviço, você deve se lembrar de executar essa saída de qualquer valor de cadeia de caracteres fornecido pelo usuário. As aspas simples em URIs têm escape como pares de aspas simples.  
  
## <a name="examples-of-calling-service-operations"></a>Exemplos de chamada de operações de serviço  
 Esta seção contém os seguintes exemplos de como chamar operações de serviço usando a biblioteca de cliente WCF Data Services:  
  
- [Chamando Execute&lt;T&gt; para retornar uma coleção de entidades](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Usando CreateQuery&lt;T&gt; retornar uma coleção de entidades](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Chamando Execute&lt;T&gt; para retornar uma única entidade](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Chamar execute&lt;T&gt; para retornar uma coleção de valores primitivos](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Chamar execute&lt;T&gt; para retornar um único valor primitivo](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Chamando uma operação de serviço que não retorna dados](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Chamando uma operação de serviço de forma assíncrona](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Chamando Execute\<T > para retornar uma coleção de entidades  
 O exemplo a seguir chama uma operação de serviço chamada GetOrdersByCity, que usa um parâmetro de cadeia de caracteres de `city` e retorna um <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Neste exemplo, a operação de serviço retorna uma coleção de objetos `Order` com objetos `Order_Detail` relacionados.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Usando CreateQuery\<T > retornar uma coleção de entidades  
 O exemplo a seguir usa o <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> para retornar uma <xref:System.Data.Services.Client.DataServiceQuery%601> que é usada para chamar a mesma operação de serviço GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Neste exemplo, o método <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> é usado para adicionar o parâmetro à consulta e o método <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> é usado para incluir objetos Order_Details relacionados nos resultados.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Chamando Execute\<T > para retornar uma única entidade  
 O exemplo a seguir chama uma operação de serviço chamada GetNewestOrder que retorna apenas uma entidade Order:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Neste exemplo, o método <xref:System.Linq.Enumerable.FirstOrDefault%2A> é usado para solicitar apenas uma entidade de ordem na execução.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Chamar execute\<T > para retornar uma coleção de valores primitivos  
 O exemplo a seguir chama uma operação de serviço que retorna uma coleção de valores de cadeia de caracteres:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Chamar execute\<T > para retornar um único valor primitivo  
 O exemplo a seguir chama uma operação de serviço que retorna um único valor de cadeia de caracteres:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Novamente neste exemplo, o método <xref:System.Linq.Enumerable.FirstOrDefault%2A> é usado para solicitar apenas um único valor inteiro na execução.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Chamando uma operação de serviço que não retorna dados  
 O exemplo a seguir chama uma operação de serviço que não retorna nenhum dado:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Como os dados não são retornados, o valor da execução não é atribuído. A única indicação de que a solicitação foi bem-sucedida é que nenhuma <xref:System.Data.Services.Client.DataServiceQueryException> é gerada.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Chamando uma operação de serviço de forma assíncrona  
 O exemplo a seguir chama uma operação de serviço de forma assíncrona chamando <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> e <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Como nenhum dado é retornado, o valor retornado pela execução não é atribuído. A única indicação de que a solicitação foi bem-sucedida é que nenhuma <xref:System.Data.Services.Client.DataServiceQueryException> é gerada.  
  
 O exemplo a seguir chama a mesma operação de serviço de forma assíncrona usando <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Veja também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)

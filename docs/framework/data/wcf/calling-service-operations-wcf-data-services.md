---
title: Chamando operações de serviço (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 41aac38cec97ae1afdd3c3c051d04ff242e7729d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174349"
---
# <a name="calling-service-operations-wcf-data-services"></a>Chamando operações de serviço (WCF Data Services)
O OData (Open Data Protocol, protocolo de dados abertos) define operações de serviço para um serviço de dados. O WCF Data Services permite definir operações como métodos no serviço de dados. Como outros recursos de serviço de dados, essas operações de serviço são tratadas usando URIs. Uma operação de serviço pode retornar coleções de tipos de entidades, instâncias de tipo de entidade única e tipos primitivos, como inteiro e string. Uma operação de `null` serviço`Nothing` também pode retornar (no Visual Basic). A biblioteca de clientes do WCF Data Services pode ser usada para acessar operações de serviço que suportam solicitações HTTP GET. Esses tipos de operações de serviço <xref:System.ServiceModel.Web.WebGetAttribute> são definidas como métodos que têm o aplicado. Para obter mais informações, consulte [Operações de Serviço](service-operations-wcf-data-services.md).  
  
 As operações de serviço são expostas nos metadados retornados por um serviço de dados que implementa o OData. Nos metadados, as operações `FunctionImport` de serviço são representadas como elementos. Ao gerar as ferramentas De <xref:System.Data.Services.Client.DataServiceContext>referência de serviço e DataSvcUtil.exe, as ferramentas Add Service Reference e DataSvcUtil.exe ignoram esse elemento. Por causa disso, você não encontrará um método no contexto que pode ser usado para chamar uma operação de serviço diretamente. No entanto, você ainda pode usar o cliente WCF Data Services para chamar as operações de serviço de uma dessas duas maneiras:  
  
- Ao ligar <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> para <xref:System.Data.Services.Client.DataServiceContext>o método no , fornecendo o URI da operação de serviço, juntamente com quaisquer parâmetros. Este método é usado para chamar qualquer operação de serviço GET.  
  
- Usando o <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> método <xref:System.Data.Services.Client.DataServiceContext> para criar <xref:System.Data.Services.Client.DataServiceQuery%601> um objeto. Ao <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>ligar, o nome da operação `entitySetName` de serviço é fornecido ao parâmetro. Este método <xref:System.Data.Services.Client.DataServiceQuery%601> retorna um objeto que chama a operação <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> de serviço quando enumerado ou quando o método é chamado. Este método é usado para chamar as operações de serviço GET que retornam uma coleção. Um único parâmetro pode ser <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> fornecido usando o método. O <xref:System.Data.Services.Client.DataServiceQuery%601> objeto retornado por este método pode ser composto ainda mais contra qualquer objeto de consulta. Para obter mais informações, consulte [Consultando o Serviço de Dados](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Considerações para operações de serviço de chamada  
 As seguintes considerações se aplicam ao usar o cliente WCF Data Services para chamar operações de serviço.  
  
- Ao acessar o serviço de dados assíncronamente, você <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> deve <xref:System.Data.Services.Client.DataServiceContext> usar <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> os métodos assíncronos equivalentes em ou nos métodos em <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
- A biblioteca de clientes wcf data services não pode materializar os resultados de uma operação de serviço que retorna uma coleção de tipos primitivos.  
  
- A biblioteca de clientes do WCF Data Services não suporta chamadas de operações de serviço POST. As operações de serviço chamadas por um <xref:System.ServiceModel.Web.WebInvokeAttribute> POST `Method="POST"` HTTP são definidas usando o com o parâmetro. Para chamar uma operação de serviço usando uma solicitação <xref:System.Net.HttpWebRequest>HTTP POST, você deve usar um .  
  
- Você não <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> pode usar para chamar uma operação de serviço GET que retorna um único resultado, de entidade ou tipo primitivo, ou que requer mais de um parâmetro de entrada. Em vez disso, deve chamar o <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> método.  
  
- Considere criar um método de extensão <xref:System.Data.Services.Client.DataServiceContext> na classe parcial fortemente digitada, <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> que <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> é gerada pelas ferramentas, que usa o método ou o método para chamar uma operação de serviço. Isso permite que você ligue para as operações de serviço diretamente do contexto. Para obter mais informações, consulte o blog post [Service Operations e o WCF Data Services Client](https://docs.microsoft.com/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client).  
  
- Quando você <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> usa para chamar uma operação de serviço, a <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> biblioteca do cliente escapa automaticamente de caracteres fornecidos para a codificação percentual de caracteres reservados, como ampersand (&) e escapando de aspas únicas em strings. No entanto, quando você chama um dos métodos *Execute* para chamar uma operação de serviço, você deve lembrar-se de executar isso escapando de quaisquer valores de string fornecidos pelo usuário. Aspas únicas em URIs são escapadas como pares de aspas únicas.  
  
## <a name="examples-of-calling-service-operations"></a>Exemplos de Operações de Serviço de Chamada  
 Esta seção contém os seguintes exemplos de como chamar operações de serviço usando a biblioteca de clientes do WCF Data Services:  
  
- [Chamando&lt;&gt; executar t para retornar uma coleção de entidades](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Usando o&lt;CreateQuery T&gt; para retornar uma coleção de entidades](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Chamando&lt;&gt; executar t para retornar uma única entidade](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Chamando&lt;&gt; Executar T para retornar uma coleção de valores primitivos](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Chamando&lt;&gt; Execute T para retornar um único valor primitivo](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Chamando uma operação de serviço que devolve nenhum dado](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Chamando uma Operação de Serviço Assíncronamente](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Chamando\<executar t> para retornar uma coleção de entidades  
 O exemplo a seguir chama uma operação de serviço chamada `city` GetOrdersByCity, que pega um parâmetro de seqüência de e retorna um: <xref:System.Linq.IQueryable%601>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Neste exemplo, a operação de `Order` serviço retorna `Order_Detail` uma coleção de objetos com objetos relacionados.  
  
<a name="CreateQueryIQueryable"></a>
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Usando o\<CreateQuery T> para retornar uma coleção de entidades  
 O exemplo a <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> seguir <xref:System.Data.Services.Client.DataServiceQuery%601> usa o retorno de um que é usado para chamar a mesma operação de serviço GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Neste exemplo, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> o método é usado para adicionar o parâmetro <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> à consulta, e o método é usado para incluir objetos relacionados Order_Details nos resultados.  
  
<a name="ExecuteSingleEntity"></a>
### <a name="calling-executet-to-return-a-single-entity"></a>Chamando\<executar t> para retornar uma única entidade  
 O exemplo a seguir chama uma operação de serviço chamada GetNewestOrder que retorna apenas uma única entidade de Ordem:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Neste exemplo, <xref:System.Linq.Enumerable.FirstOrDefault%2A> o método é usado para solicitar apenas uma única entidade de Ordem na execução.  
  
<a name="ExecutePrimitiveCollection"></a>
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Chamando\<Executar T> para retornar uma coleção de valores primitivos  
 O exemplo a seguir chama uma operação de serviço que retorna uma coleção de valores de string:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Chamar\<executar t> para retornar um único valor primitivo  
 O exemplo a seguir chama uma operação de serviço que retorna um único valor de string:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Novamente neste exemplo, <xref:System.Linq.Enumerable.FirstOrDefault%2A> o método é usado para solicitar apenas um único valor inteiro na execução.  
  
<a name="ExecuteVoid"></a>
### <a name="calling-a-service-operation-that-returns-no-data"></a>Chamando uma operação de serviço que devolve nenhum dado  
 O exemplo a seguir chama uma operação de serviço que não retorna dados:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Como os dados não são devolvidos, o valor da execução não é atribuído. A única indicação de que o <xref:System.Data.Services.Client.DataServiceQueryException> pedido foi bem sucedido é que não é levantado.  
  
<a name="ExecuteAsync"></a>
### <a name="calling-a-service-operation-asynchronously"></a>Chamando uma Operação de Serviço Assíncronamente  
 O exemplo a seguir chama uma operação <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> de <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>serviço assíncronamente ligando e:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Como nenhum dado é devolvido, o valor devolvido pela execução não é atribuído. A única indicação de que o <xref:System.Data.Services.Client.DataServiceQueryException> pedido foi bem sucedido é que não é levantado.  
  
 O exemplo a seguir chama a mesma operação <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>de serviço de forma assíncrona usando :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Confira também

- [Biblioteca de cliente do WCF Data Services](wcf-data-services-client-library.md)

---
title: Chamando operações de serviço (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 21ae73054935373607909902e0b3e82ba5146f43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791152"
---
# <a name="calling-service-operations-wcf-data-services"></a>Chamando operações de serviço (WCF Data Services)
O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] define as operações de serviço para um serviço de dados. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]permite que você defina operações como métodos no serviço de dados. Assim como outros recursos de serviço de dados, essas operações de serviço são endereçadas usando URIs. Uma operação de serviço pode retornar coleções de tipos de entidade, instâncias de tipo de entidade única e tipos primitivos, como inteiro e cadeia de caracteres. Uma operação de serviço também pode `null` retornar`Nothing` (em Visual Basic). A [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente pode ser usada para acessar as operações de serviço que dão suporte a solicitações HTTP Get. Esses tipos de operações de serviço são definidos como métodos que têm <xref:System.ServiceModel.Web.WebGetAttribute> o aplicado. Para obter mais informações, consulte [operações de serviço](service-operations-wcf-data-services.md).  
  
 As operações de serviço são expostas nos metadados retornados por um serviço de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]dados que implementa o. Nos metadados, as operações de serviço são representadas como `FunctionImport` elementos. Ao gerar o tipo fortemente tipado <xref:System.Data.Services.Client.DataServiceContext>, as ferramentas Adicionar referência de serviço e datasvcutil. exe ignoram esse elemento. Por isso, você não encontrará um método no contexto que possa ser usado para chamar uma operação de serviço diretamente. No entanto, você ainda pode [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] usar o cliente para chamar operações de serviço de uma destas duas maneiras:  
  
- Chamando o <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> método <xref:System.Data.Services.Client.DataServiceContext>no, fornecendo o URI da operação de serviço, juntamente com quaisquer parâmetros. Esse método é usado para chamar qualquer operação de obtenção de serviço.  
  
- Usando o <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> método <xref:System.Data.Services.Client.DataServiceContext> no para criar um <xref:System.Data.Services.Client.DataServiceQuery%601> objeto. Ao chamar <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, o nome da operação de serviço é fornecido para o `entitySetName` parâmetro. Esse método retorna um <xref:System.Data.Services.Client.DataServiceQuery%601> objeto que chama a operação de serviço quando enumerado ou quando <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> o método é chamado. Esse método é usado para chamar operações GET Service que retornam uma coleção. Um único parâmetro pode ser fornecido usando o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> método. O <xref:System.Data.Services.Client.DataServiceQuery%601> objeto retornado por esse método pode ser mais composto como qualquer objeto de consulta. Para obter mais informações, consulte [consultando o serviço de dados](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Considerações para chamar operações de serviço  
 As considerações a seguir se aplicam [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ao usar o cliente para chamar operações de serviço.  
  
- Ao acessar o serviço de dados de forma assíncrona, você deve <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> usar os <xref:System.Data.Services.Client.DataServiceContext> métodos assíncronos <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> / / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> equivalentes em ou os <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> métodos em <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
- A [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente não pode materializar os resultados de uma operação de serviço que retorna uma coleção de tipos primitivos.  
  
- A [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente não dá suporte à chamada de operações de serviço post. As operações de serviço que são chamadas por um http post são definidas usando <xref:System.ServiceModel.Web.WebInvokeAttribute> o com `Method="POST"` o parâmetro. Para chamar uma operação de serviço usando uma solicitação HTTP POST, você deve usar um <xref:System.Net.HttpWebRequest>.  
  
- Você não pode <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> usar para chamar uma operação Get Service que retorna um único resultado, de uma entidade ou tipo primitivo, ou que requer mais de um parâmetro de entrada. Em vez disso, você <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> deve chamar o método.  
  
- Considere a criação de um método de extensão na classe <xref:System.Data.Services.Client.DataServiceContext> parcial fortemente tipada, que é gerada pelas ferramentas, que usa o <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> ou o <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> método para chamar uma operação de serviço. Isso permite que você chame operações de serviço diretamente do contexto. Para obter mais informações, consulte a postagem no blog [operações de serviço e o cliente de WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=215668).  
  
- Quando você usa <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> o para chamar uma operação de serviço, a biblioteca de cliente automaticamente escapa os caracteres <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> fornecidos ao executando a codificação por porcentagem de caracteres reservados, como e comercial (&) e saída de aspas simples em seqüências. No entanto, ao chamar um dos métodos *Execute* para chamar uma operação de serviço, você deve se lembrar de executar essa saída de qualquer valor de cadeia de caracteres fornecido pelo usuário. As aspas simples em URIs têm escape como pares de aspas simples.  
  
## <a name="examples-of-calling-service-operations"></a>Exemplos de chamada de operações de serviço  
 Esta seção contém os seguintes exemplos de como chamar operações de serviço usando a biblioteca [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] de cliente:  
  
- [Chamando Execute&lt;T&gt; para retornar uma coleção de entidades](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Usando CreateQuery&lt;T&gt; para retornar uma coleção de entidades](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Chamando Execute&lt;T&gt; para retornar uma única entidade](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Chamando Execute&lt;T&gt; para retornar uma coleção de valores primitivos](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Chamando Execute&lt;T&gt; para retornar um único valor primitivo](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Chamando uma operação de serviço que não retorna dados](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Chamando uma operação de serviço de forma assíncrona](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Chamando Execute\<T > para retornar uma coleção de entidades  
 O exemplo a seguir chama uma operação de serviço chamada GetOrdersByCity, que usa um parâmetro `city` de cadeia de <xref:System.Linq.IQueryable%601>caracteres de e retorna um:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Neste exemplo, a operação de serviço retorna uma coleção de `Order` objetos com objetos `Order_Detail` relacionados.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Usando CreateQuery\<T > retornar uma coleção de entidades  
 O exemplo a seguir usa <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> o para retornar <xref:System.Data.Services.Client.DataServiceQuery%601> um que é usado para chamar a mesma operação de serviço GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Neste exemplo, o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> método é usado para adicionar o parâmetro à consulta e o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método é usado para incluir objetos Detalhes_Pedido relacionados nos resultados.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Chamando Execute\<T > para retornar uma única entidade  
 O exemplo a seguir chama uma operação de serviço chamada GetNewestOrder que retorna apenas uma entidade Order:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Neste exemplo, o <xref:System.Linq.Enumerable.FirstOrDefault%2A> método é usado para solicitar apenas uma entidade de ordem na execução.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Chamando Execute\<T > para retornar uma coleção de valores primitivos  
 O exemplo a seguir chama uma operação de serviço que retorna uma coleção de valores de cadeia de caracteres:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Chamando Execute\<T > para retornar um único valor primitivo  
 O exemplo a seguir chama uma operação de serviço que retorna um único valor de cadeia de caracteres:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Novamente neste exemplo, o <xref:System.Linq.Enumerable.FirstOrDefault%2A> método é usado para solicitar apenas um único valor inteiro na execução.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Chamando uma operação de serviço que não retorna dados  
 O exemplo a seguir chama uma operação de serviço que não retorna nenhum dado:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Como os dados não são retornados, o valor da execução não é atribuído. A única indicação de que a solicitação foi bem-sucedida é que <xref:System.Data.Services.Client.DataServiceQueryException> não é gerado.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Chamando uma operação de serviço de forma assíncrona  
 O exemplo a seguir chama uma operação de serviço de <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> forma <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>assíncrona chamando e:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Como nenhum dado é retornado, o valor retornado pela execução não é atribuído. A única indicação de que a solicitação foi bem-sucedida é que <xref:System.Data.Services.Client.DataServiceQueryException> não é gerado.  
  
 O exemplo a seguir chama a mesma operação de serviço de <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>forma assíncrona usando:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)

---
title: Chamar operações de serviço (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: aaee236487fedcb0c5d8ad113391bd628b11bb41
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517948"
---
# <a name="calling-service-operations-wcf-data-services"></a>Chamar operações de serviço (WCF Data Services)
O [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] define as operações de serviço para um serviço de dados. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite que você defina essas operações como métodos no serviço de dados. Assim como outros recursos do serviço de dados, essas operações de serviço são endereçadas por meio de URIs. Uma operação de serviço pode retornar coleções de tipos de entidade, as instâncias de tipo de entidade única e tipos primitivos, como integer e string. Uma operação de serviço também pode retornar `null` (`Nothing` no Visual Basic). O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente pode ser usada para acessar operações de serviço que oferecem suporte a solicitações HTTP GET. Esses tipos de operações de serviço são definidos como métodos que têm o <xref:System.ServiceModel.Web.WebGetAttribute> aplicado. Para obter mais informações, consulte [operações de serviço](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Operações de serviço são expostas nos metadados retornados por um serviço de dados que implementa o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Nos metadados, operações de serviço são representadas como `FunctionImport` elementos. Ao gerar fortemente tipado <xref:System.Data.Services.Client.DataServiceContext>, as ferramentas de adicionar referência de serviço e DataSvcUtil.exe ignorar esse elemento. Por isso, você não encontrará um método no contexto de que pode ser usado para chamar uma operação de serviço diretamente. No entanto, você ainda pode usar o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] cliente para chamar operações de serviço em uma destas duas maneiras:  
  
-   Chamando o <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> método no <xref:System.Data.Services.Client.DataServiceContext>, fornecendo o URI da operação de serviço, juntamente com quaisquer parâmetros. Esse método é usado para chamar qualquer operação de serviço GET.  
  
-   Usando o <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> método em de <xref:System.Data.Services.Client.DataServiceContext> para criar um <xref:System.Data.Services.Client.DataServiceQuery%601> objeto. Ao chamar <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, o nome da operação de serviço é fornecido para o `entitySetName` parâmetro. Esse método retorna um <xref:System.Data.Services.Client.DataServiceQuery%601> objeto que chama a operação de serviço quando enumerada, ou quando o <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> método é chamado. Esse método é usado para chamar operações de serviço GET que retornam uma coleção. Um único parâmetro pode ser fornecido usando o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> método. O <xref:System.Data.Services.Client.DataServiceQuery%601> objeto retornado por esse método pode ser composto adicionalmente em relação a como qualquer objeto de consulta. Para obter mais informações, consulte [consultando o Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Considerações para chamar operações de serviço  
 As seguintes considerações se aplicam ao usar o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] cliente para chamar operações de serviço.  
  
-   Ao acessar o serviço de dados de forma assíncrona, você deve usar o equivalente assíncrono <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> métodos em <xref:System.Data.Services.Client.DataServiceContext> ou o <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> métodos em <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente não pode materializar os resultados de uma operação de serviço que retorna uma coleção de tipos primitivos.  
  
-   O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente não dá suporte a operações de serviço chamadas POST. Operações de serviço que são chamadas por um HTTP POST são definidas usando o <xref:System.ServiceModel.Web.WebInvokeAttribute> com o `Method="POST"` parâmetro. Para chamar uma operação de serviço usando uma solicitação HTTP POST, em vez disso, você deve usar um <xref:System.Net.HttpWebRequest>.  
  
-   Não é possível usar <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> para chamar uma operação de serviço GET que retorna um único resultado de entidade ou tipo primitivo, ou que exige a mais de um parâmetro de entrada. Em vez disso, você deve chamar o <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> método.  
  
-   Considere a criação de um método de extensão em fortemente tipado <xref:System.Data.Services.Client.DataServiceContext> classe parcial, que é gerada pelas ferramentas, que usa o <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> ou o <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> método para chamar uma operação de serviço. Isso permite que você chamar operações de serviço diretamente do contexto. Para obter mais informações, consulte o postagem no blog [operações de serviço e o WCF Data Services Client](https://go.microsoft.com/fwlink/?LinkId=215668).  
  
-   Quando você usa <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> para chamar uma operação de serviço, a biblioteca de cliente automaticamente ignora os caracteres fornecidos para o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> ao executar a codificação por porcentagem dos caracteres reservados, como "e" comercial (&) e o escape de aspas em cadeias de caracteres. No entanto, quando você chama um dos *Execute* métodos para chamar uma operação de serviço, você deve se lembrar de executar este escape de quaisquer valores de cadeia de caracteres fornecida pelo usuário. Aspas nos URIs são escapadas como pares de aspas.  
  
## <a name="examples-of-calling-service-operations"></a>Exemplos de como chamar operações de serviço  
 Esta seção contém os seguintes exemplos de como chamar operações de serviço usando o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente:  
  
-   [Chamar Execute&lt;T&gt; para retornar uma coleção de entidades](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
-   [Usando CreateQuery&lt;T&gt; para retornar uma coleção de entidades](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
-   [Chamar Execute&lt;T&gt; para retornar uma única entidade](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
-   [Chamar Execute&lt;T&gt; para retornar uma coleção de valores primitivos](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
-   [Chamar Execute&lt;T&gt; para retornar um único valor primitivo](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
-   [Chamar uma operação de serviço que não retorna nenhum dado](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
-   [Chamando uma operação de serviço de forma assíncrona](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Chamar Execute\<T > para retornar uma coleção de entidades  
 O exemplo a seguir chama uma operação de serviço chamada GetOrdersByCity, que usa um parâmetro de cadeia de caracteres do `city` e retorna um <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 Neste exemplo, a operação de serviço retorna uma coleção de `Order` objetos com relacionados `Order_Detail` objetos.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Usando CreateQuery\<T > para retornar uma coleção de entidades  
 O exemplo a seguir usa o <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> para retornar um <xref:System.Data.Services.Client.DataServiceQuery%601> que é usado para chamar a operação de serviço GetOrdersByCity mesma:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 Neste exemplo, o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> método é usado para adicionar o parâmetro à consulta e o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método é usado para incluir objetos relacionados do Order_Details nos resultados.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Chamar Execute\<T > para retornar uma única entidade  
 O exemplo a seguir chama uma operação de serviço chamada GetNewestOrder que retorna uma única entidade ordem:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 Neste exemplo, o <xref:System.Linq.Enumerable.FirstOrDefault%2A> método é usado para solicitar apenas uma única entidade Order em execução.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Chamar Execute\<T > para retornar uma coleção de valores primitivos  
 O exemplo a seguir chama uma operação de serviço que retorna uma coleção de valores de cadeia de caracteres:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Chamar Execute\<T > para retornar um único valor primitivo  
 O exemplo a seguir chama uma operação de serviço que retorna um valor de cadeia de caracteres única:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Novamente neste exemplo, o <xref:System.Linq.Enumerable.FirstOrDefault%2A> método é usado para solicitar apenas um único valor inteiro em execução.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Chamar uma operação de serviço que não retorna nenhum dado  
 O exemplo a seguir chama uma operação de serviço que não retorna nenhum dado:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Porque os dados não são retornados, o valor da execução não está atribuído. A única indicação de que a solicitação foi bem-sucedida é que nenhum <xref:System.Data.Services.Client.DataServiceQueryException> é gerado.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Chamando uma operação de serviço de forma assíncrona  
 O exemplo a seguir chama uma operação de serviço de forma assíncrona chamando <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> e <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Como nenhum dado é retornado, o valor retornado pela execução não é atribuído. A única indicação de que a solicitação foi bem-sucedida é que nenhum <xref:System.Data.Services.Client.DataServiceQueryException> é gerado.  
  
 O exemplo a seguir chama a mesma operação de serviço de forma assíncrona usando <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)

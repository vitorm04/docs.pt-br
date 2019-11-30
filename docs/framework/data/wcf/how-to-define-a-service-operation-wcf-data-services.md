---
title: Como definir uma operação de serviço (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: e9d15698c1e020f5b4179efb3e8492f3754ff02f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569136"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>Como definir uma operação de serviço (WCF Data Services)

WCF Data Services expor métodos que são definidos no servidor como operações de serviço. As operações de serviço permitem que um serviço de dados forneça acesso por meio de um URI para um método definido no servidor. Para definir uma operação de serviço, aplique o atributo [`WebGet]` ou `[WebInvoke]` ao método. Para dar suporte a operadores de consulta, a operação de serviço deve retornar uma instância de <xref:System.Linq.IQueryable%601>. As operações de serviço podem acessar a fonte de dados subjacente por meio da propriedade <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> no <xref:System.Data.Services.DataService%601>. Para obter mais informações, consulte [operações de serviço](service-operations-wcf-data-services.md).

O exemplo neste tópico define uma operação de serviço chamada `GetOrdersByCity` que retorna uma instância de <xref:System.Linq.IQueryable%601> filtrada de `Orders` e objetos `Order_Details` relacionados. O exemplo acessa a instância de <xref:System.Data.Objects.ObjectContext> que é a fonte de dados para o serviço de dados de exemplo Northwind. Esse serviço é criado quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Para definir uma operação de serviço no serviço de dados Northwind

1. No projeto do serviço de dados Northwind, abra o arquivo Northwind.svc.

2. Na classe `Northwind`, defina um método de operação de serviço chamado `GetOrdersByCity` da seguinte maneira:

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. No método `InitializeService` da classe `Northwind`, adicione o seguinte código para habilitar o acesso à operação de serviço:

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a>Para consultar a operação do serviço GetOrdersByCity

- Em um navegador da Web, insira um dos seguintes URIs para invocar a operação de serviço que é definida no exemplo a seguir:

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a>Exemplo

O exemplo a seguir implementa uma operação de serviço chamada `GetOrderByCity` no serviço de dados Northwind. Esta operação usa o Entity Framework ADO.NET para retornar um conjunto de `Orders` e objetos `Order_Details` relacionados como uma instância de <xref:System.Linq.IQueryable%601> com base no nome de cidade fornecido.

> [!NOTE]
> Há suporte para operadores de consulta neste ponto de extremidade de operação de serviço porque o método retorna uma instância de <xref:System.Linq.IQueryable%601>.

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a>Consulte também

- [Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)

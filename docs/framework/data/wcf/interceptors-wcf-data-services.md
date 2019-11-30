---
title: Interceptores (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: c9799037ae0ea8b29b5e989859aff29c310593d4
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568978"
---
# <a name="interceptors-wcf-data-services"></a>Interceptores (WCF Data Services)
WCF Data Services permite que um aplicativo intercepte mensagens de solicitação para que você possa adicionar lógica personalizada a uma operação. Você pode usar essa lógica personalizada para validar dados em mensagens de entrada. Você também pode usá-la para restringir mais o escopo de uma solicitação de consulta, como inserir uma política de autorização personalizada com base na solicitação.  
  
 A interceptação é executada por métodos especialmente atribuídos no serviço de dados. Esses métodos são chamados por WCF Data Services no ponto apropriado do processamento de mensagens. Os interceptores são definidos em uma base de conjunto por entidade, e os métodos do Interceptor não podem aceitar parâmetros da solicitação, como as operações de serviço podem. Os métodos do interceptor de consulta, que são chamados ao processar uma solicitação HTTP GET, devem retornar uma expressão lambda que determina se uma instância do conjunto de entidades do Interceptor deve ser retornada pelos resultados da consulta. Esta expressão é usada pelo serviço de dados para refinar mais a operação solicitada. Veja a seguir um exemplo de definição de um interceptor de consulta.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Os interceptores de alteração, que são chamados para processar operações sem consulta, devem retornar `void` (`Nothing` no Visual Basic). Os métodos de interceptor de alteração devem aceitar estes dois parâmetros:  
  
1. Um parâmetro de um tipo que seja compatível com o tipo de entidade do conjunto de entidades. Quando o serviço de dados chamar o interceptor de alteração, o valor desse parâmetro refletirá as informações de entidade enviadas pela solicitação.  
  
2. Um parâmetro do tipo <xref:System.Data.Services.UpdateOperations>. Quando o serviço de dados chamar o interceptor de alteração, o valor desse parâmetro refletirá a operação que a solicitação estiver tentando executar.  
  
 Veja a seguir um exemplo de definição de um interceptor de alteração.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Os atributos a seguir têm suporte para interceptação.  
  
 **[QueryInterceptor (** *EntitySetName* **)]**  
 Os métodos com o atributo <xref:System.Data.Services.QueryInterceptorAttribute> aplicado são chamados quando uma solicitação HTTP GET é recebida para o recurso de destino do conjunto de entidades. Esses métodos devem sempre retornar uma expressão lambda no formato `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor (** *EntitySetName* **)]**  
 Os métodos com o atributo <xref:System.Data.Services.ChangeInterceptorAttribute> aplicado são chamados quando uma solicitação HTTP, que não seja HTTP GET, é recebida para o recurso de destino do conjunto de entidades. Esses métodos devem sempre retornar `void` (`Nothing` no Visual Basic).  
  
 Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também

- [Operações de serviço](service-operations-wcf-data-services.md)

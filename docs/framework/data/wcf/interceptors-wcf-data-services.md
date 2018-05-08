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
ms.openlocfilehash: f3ff08dd4cd20e7ce226750a386cfddb27731923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="interceptors-wcf-data-services"></a>Interceptores (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite que um aplicativo interceptar mensagens de solicitação para que você possa adicionar lógica personalizada para uma operação. Você pode usar essa lógica personalizada para validar dados em mensagens de entrada. Você também pode usá-la para restringir mais o escopo de uma solicitação de consulta, como inserir uma política de autorização personalizada com base na solicitação.  
  
 A interceptação é executada por métodos especialmente atribuídos no serviço de dados. Esses métodos são chamados pelo [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] no ponto apropriado no processamento de mensagens. Interceptores são definidos em uma base de conjunto por entidade e métodos interceptador não podem aceitar parâmetros da solicitação pode ser operações de serviço. Métodos de interceptador de consulta, que são chamados durante o processamento de uma solicitação HTTP GET, devem retornar uma expressão lambda que determina se uma instância da entidade do interceptador definida deve ser retornada pelos resultados da consulta. Esta expressão é usada pelo serviço de dados para refinar mais a operação solicitada. Veja a seguir um exemplo de definição de um interceptor de consulta.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Os interceptores de alteração, que são chamados para processar operações sem consulta, devem retornar `void` (`Nothing` no Visual Basic). Os métodos de interceptor de alteração devem aceitar estes dois parâmetros:  
  
1.  Um parâmetro de um tipo que seja compatível com o tipo de entidade do conjunto de entidades. Quando o serviço de dados chamar o interceptor de alteração, o valor desse parâmetro refletirá as informações de entidade enviadas pela solicitação.  
  
2.  Um parâmetro do tipo <xref:System.Data.Services.UpdateOperations>. Quando o serviço de dados chamar o interceptor de alteração, o valor desse parâmetro refletirá a operação que a solicitação estiver tentando executar.  
  
 Veja a seguir um exemplo de definição de um interceptor de alteração.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
 Os atributos a seguir têm suporte para interceptação.  
  
 **[QueryInterceptor (** *EnitySetName* **)]**  
 Os métodos com o atributo <xref:System.Data.Services.QueryInterceptorAttribute> aplicado são chamados quando uma solicitação HTTP GET é recebida para o recurso de destino do conjunto de entidades. Esses métodos devem sempre retornar uma expressão lambda no formato `Expression<Func<T,bool>>`.  
  
 **[ChangeInterceptor (** *EnitySetName* **)]**  
 Os métodos com o atributo <xref:System.Data.Services.ChangeInterceptorAttribute> aplicado são chamados quando uma solicitação HTTP, que não seja HTTP GET, é recebida para o recurso de destino do conjunto de entidades. Esses métodos devem sempre retornar `void` (`Nothing` no Visual Basic).  
  
 Para obter mais informações, consulte [como: interceptar mensagens do serviço de dados](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Operações de serviço](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)

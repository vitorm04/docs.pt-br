---
title: Como criar um contrato unidirecional
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d08fcb955c972ffbd7ef0a48625f1005ab366dd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-one-way-contract"></a>Como criar um contrato unidirecional
Este tópico mostra as etapas básicas para criar métodos que usam um contrato unidirecional. Esses métodos invocar operações em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de um cliente de serviço, mas não espera uma resposta. Esse tipo de contrato pode ser usado, por exemplo, para publicar as notificações para vários assinantes. Você também pode usar os contratos unidirecionais ao criar um contrato duplex (bidirecional), que permite que clientes e servidores para se comunicar uns com os outros independentemente para que qualquer um pode iniciar chamadas para o outro. Isso pode permitir que, em particular, o servidor fazer chamadas unidirecionais para o cliente que o cliente pode tratar eventos. Para obter informações detalhadas sobre como especificar métodos unidirecionais, consulte o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade e o <xref:System.ServiceModel.OperationContractAttribute> classe.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]criar um aplicativo cliente para um contrato duplex, consulte [como: serviços do Access com unidirecional e contratos de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md). Para obter um exemplo de funcionamento, consulte o [unidirecional](../../../../docs/framework/wcf/samples/one-way.md) exemplo.  
  
### <a name="to-create-a-one-way-contract"></a>Para criar um contrato unidirecional  
  
1.  Criar o contrato de serviço aplicando o <xref:System.ServiceModel.ServiceContractAttribute> classe para a interface que define os métodos de serviço deve ser implementado.  
  
2.  Indicar quais métodos na interface um cliente pode chamada aplicando o <xref:System.ServiceModel.OperationContractAttribute> classe para eles.  
  
3.  Designar operações que não devem ter nenhuma saída (nenhum valor de retorno e nenhum limite ou parâmetros ref) como unidirecional, definindo o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `true`. Observe que as operações que executar o <xref:System.ServiceModel.OperationContractAttribute> classe satisfazer um contrato de solicitação-resposta por padrão porque o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> é de propriedade `false` por padrão. Portanto, você deve especificar explicitamente o valor da propriedade de atributo para ser `true` se você quiser um contrato unidirecional para o método.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define um contrato para um serviço que inclui vários métodos unidirecionais. Todos os métodos têm contratos unidirecionais exceto `Equals`, que usa como padrão solicitação-resposta e retorna um resultado.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Serviços de design e implantação](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Como definir um contrato de serviço](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Sessão](../../../../docs/framework/wcf/samples/session.md)  
 [Como criar um contrato duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)

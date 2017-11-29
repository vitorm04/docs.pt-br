---
title: Tratamento de erros HTTP Web do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3366ab851c6e6b66a5df94bdb24baad4ae0c8d14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-web-http-error-handling"></a>Tratamento de erros HTTP Web do WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Tratamento de erros de Web HTTP permite que você retorne erros de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços Web HTTP que especificam um status HTTP de código e retornar detalhes do erro usando o mesmo formato que a operação (por exemplo, XML ou JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Tratamento de erros HTTP Web do WCF  
 O <xref:System.ServiceModel.Web.WebFaultException> classe define um construtor que permite que você especifique um código de status HTTP. Esse código de status, em seguida, é retornado ao cliente. Uma versão genérica do <xref:System.ServiceModel.Web.WebFaultException> classe <xref:System.ServiceModel.Web.WebFaultException%601> permite que você retorne um tipo definido pelo usuário que contém informações sobre o erro que ocorreu. Este objeto personalizado é serializado usando o formato especificado pela operação e retornado ao cliente. O exemplo a seguir mostra como retornar um código de status HTTP.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 O exemplo a seguir mostra como retornar um código de status HTTP e informações adicionais em um tipo definido pelo usuário. `MyErrorDetail`é um tipo definido pelo usuário que contém informações adicionais sobre o erro que ocorreu.  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 O código anterior retorna uma resposta HTTP com o código de status proibido e um corpo que contém uma instância do `MyErrorDetails` objeto. O formato da `MyErrorDetails` objeto é determinado por:  
  
-   O valor da `ResponseFormat` parâmetro o <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo especificado na operação do serviço.  
  
-   O valor de <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
-   O valor de <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> propriedade acessando o <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como esses valores afetam a formatação da operação, consulte [formatação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException>é um <xref:System.ServiceModel.FaultException> e, portanto, pode ser usado como o modelo de programação de exceção de falha para os serviços que expõem pontos de extremidade SOAP, bem como a web pontos de extremidade HTTP.  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de programação WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Formatação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [Defining and Specifying Faults](../../../../docs/framework/wcf/defining-and-specifying-faults.md) (Definindo e especificando falhas)  
 [Tratando exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md) (Enviando e recebendo falhas)

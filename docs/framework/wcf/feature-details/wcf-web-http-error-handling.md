---
title: Tratamento de erros HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 228f8cdbe5ddde63f2b6afd82a27055f2241e058
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498479"
---
# <a name="wcf-web-http-error-handling"></a>Tratamento de erros HTTP Web do WCF
Tratamento de erros do Windows Communication Foundation (WCF) HTTP da Web permite que você retorne erros dos serviços WCF Web HTTP que especifique um código de status HTTP e retornam detalhes do erro usando o mesmo formato que a operação (por exemplo, XML ou JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Tratamento de erros HTTP Web do WCF  
 O <xref:System.ServiceModel.Web.WebFaultException> classe define um construtor que permite que você especifique um código de status HTTP. Esse código de status, em seguida, é retornado ao cliente. Uma versão genérica do <xref:System.ServiceModel.Web.WebFaultException> classe <xref:System.ServiceModel.Web.WebFaultException%601> permite que você retorne um tipo definido pelo usuário que contém informações sobre o erro que ocorreu. Este objeto personalizado é serializado usando o formato especificado pela operação e retornado ao cliente. O exemplo a seguir mostra como retornar um código de status HTTP.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 O exemplo a seguir mostra como retornar um código de status HTTP e informações adicionais em um tipo definido pelo usuário. `MyErrorDetail` é um tipo definido pelo usuário que contém informações adicionais sobre o erro que ocorreu.  
  
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
  
 Para obter mais informações sobre como esses valores afetam a formatação da operação, consulte [formatação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> é um <xref:System.ServiceModel.FaultException> e, portanto, pode ser usado como o modelo de programação de exceção de falha para os serviços que expõem pontos de extremidade SOAP, bem como a web pontos de extremidade HTTP.  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Formatação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [Definindo e especificando falhas](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [Tratamento de exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Enviando e recebendo falhas](../../../../docs/framework/wcf/sending-and-receiving-faults.md)

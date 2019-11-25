---
title: Tratamento de erros HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 34912bccaefb645541f47d083c5c307b20ff77c5
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975950"
---
# <a name="wcf-web-http-error-handling"></a>Tratamento de erros HTTP Web do WCF
O tratamento de erros HTTP Web do Windows Communication Foundation (WCF) permite que você retorne erros de serviços HTTP Web WCF que especificam um código de status HTTP e retornam detalhes do erro usando o mesmo formato que a operação (por exemplo, XML ou JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Tratamento de erros HTTP Web do WCF  
 A classe <xref:System.ServiceModel.Web.WebFaultException> define um construtor que permite que você especifique um código de status HTTP. Esse código de status é retornado para o cliente. Uma versão genérica da classe <xref:System.ServiceModel.Web.WebFaultException>, <xref:System.ServiceModel.Web.WebFaultException%601> permite que você retorne um tipo definido pelo usuário que contém informações sobre o erro que ocorreu. Esse objeto personalizado é serializado usando o formato especificado pela operação e retornado ao cliente. O exemplo a seguir mostra como retornar um código de status HTTP.  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 O exemplo a seguir mostra como retornar um código de status HTTP e informações extras em um tipo definido pelo usuário. `MyErrorDetail` é um tipo definido pelo usuário que contém informações adicionais sobre o erro ocorrido.  
  
```csharp
public string Operation2()
{
   // Operation logic  
   // ...
   MyErrorDetail detail = new MyErrorDetail()
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 O código anterior retorna uma resposta HTTP com o código de status proibido e um corpo que contém uma instância do objeto `MyErrorDetails`. O formato do objeto `MyErrorDetails` é determinado por:  
  
- O valor do parâmetro `ResponseFormat` do atributo <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> especificado na operação de serviço.  
  
- O valor de <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
- O valor da propriedade <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> acessando o <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 Para obter mais informações sobre como esses valores afetam a formatação da operação, consulte [formatação do WCF Web http](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> é um <xref:System.ServiceModel.FaultException> e, portanto, pode ser usado como o modelo de programação de exceção de falha para serviços que expõem pontos de extremidade SOAP, bem como pontos de extremidade HTTP da Web.  
  
## <a name="see-also"></a>Consulte também

- [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Formatação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [Definindo e especificando falhas](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [Tratamento de exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Enviando e recebendo falhas](../../../../docs/framework/wcf/sending-and-receiving-faults.md)

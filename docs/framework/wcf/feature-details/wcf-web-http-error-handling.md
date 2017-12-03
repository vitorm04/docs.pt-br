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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 156960a6594f5475e339b36e5dabf46f26d13d62
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="dcc4e-102">Tratamento de erros HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="dcc4e-102">WCF Web HTTP Error Handling</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="dcc4e-103">Tratamento de erros de Web HTTP permite que você retorne erros de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços Web HTTP que especificam um status HTTP de código e retornar detalhes do erro usando o mesmo formato que a operação (por exemplo, XML ou JSON).</span><span class="sxs-lookup"><span data-stu-id="dcc4e-103"> Web HTTP error handling enables you to return errors from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="dcc4e-104">Tratamento de erros HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="dcc4e-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="dcc4e-105">O <xref:System.ServiceModel.Web.WebFaultException> classe define um construtor que permite que você especifique um código de status HTTP.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="dcc4e-106">Esse código de status, em seguida, é retornado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-106">This status code is then returned to the client.</span></span> <span data-ttu-id="dcc4e-107">Uma versão genérica do <xref:System.ServiceModel.Web.WebFaultException> classe <xref:System.ServiceModel.Web.WebFaultException%601> permite que você retorne um tipo definido pelo usuário que contém informações sobre o erro que ocorreu.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="dcc4e-108">Este objeto personalizado é serializado usando o formato especificado pela operação e retornado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="dcc4e-109">O exemplo a seguir mostra como retornar um código de status HTTP.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="dcc4e-110">O exemplo a seguir mostra como retornar um código de status HTTP e informações adicionais em um tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="dcc4e-111">`MyErrorDetail`é um tipo definido pelo usuário que contém informações adicionais sobre o erro que ocorreu.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="dcc4e-112">O código anterior retorna uma resposta HTTP com o código de status proibido e um corpo que contém uma instância do `MyErrorDetails` objeto.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="dcc4e-113">O formato da `MyErrorDetails` objeto é determinado por:</span><span class="sxs-lookup"><span data-stu-id="dcc4e-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="dcc4e-114">O valor da `ResponseFormat` parâmetro o <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo especificado na operação do serviço.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="dcc4e-115">O valor de <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="dcc4e-116">O valor de <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> propriedade acessando o <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="dcc4e-117">como esses valores afetam a formatação da operação, consulte [formatação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="dcc4e-117"> how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="dcc4e-118"><xref:System.ServiceModel.Web.WebFaultException>é um <xref:System.ServiceModel.FaultException> e, portanto, pode ser usado como o modelo de programação de exceção de falha para os serviços que expõem pontos de extremidade SOAP, bem como a web pontos de extremidade HTTP.</span><span class="sxs-lookup"><span data-stu-id="dcc4e-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc4e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcc4e-119">See Also</span></span>  
 [<span data-ttu-id="dcc4e-120">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="dcc4e-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="dcc4e-121">Formatação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="dcc4e-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 <span data-ttu-id="dcc4e-122">[Defining and Specifying Faults](../../../../docs/framework/wcf/defining-and-specifying-faults.md) (Definindo e especificando falhas)</span><span class="sxs-lookup"><span data-stu-id="dcc4e-122">[Defining and Specifying Faults](../../../../docs/framework/wcf/defining-and-specifying-faults.md)</span></span>  
 [<span data-ttu-id="dcc4e-123">Tratando exceções e falhas</span><span class="sxs-lookup"><span data-stu-id="dcc4e-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 <span data-ttu-id="dcc4e-124">[Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md) (Enviando e recebendo falhas)</span><span class="sxs-lookup"><span data-stu-id="dcc4e-124">[Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md)</span></span>

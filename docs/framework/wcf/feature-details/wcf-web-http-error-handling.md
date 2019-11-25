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
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="e23a3-102">Tratamento de erros HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="e23a3-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="e23a3-103">O tratamento de erros HTTP Web do Windows Communication Foundation (WCF) permite que você retorne erros de serviços HTTP Web WCF que especificam um código de status HTTP e retornam detalhes do erro usando o mesmo formato que a operação (por exemplo, XML ou JSON).</span><span class="sxs-lookup"><span data-stu-id="e23a3-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="e23a3-104">Tratamento de erros HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="e23a3-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="e23a3-105">A classe <xref:System.ServiceModel.Web.WebFaultException> define um construtor que permite que você especifique um código de status HTTP.</span><span class="sxs-lookup"><span data-stu-id="e23a3-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="e23a3-106">Esse código de status é retornado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="e23a3-106">This status code is then returned to the client.</span></span> <span data-ttu-id="e23a3-107">Uma versão genérica da classe <xref:System.ServiceModel.Web.WebFaultException>, <xref:System.ServiceModel.Web.WebFaultException%601> permite que você retorne um tipo definido pelo usuário que contém informações sobre o erro que ocorreu.</span><span class="sxs-lookup"><span data-stu-id="e23a3-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="e23a3-108">Esse objeto personalizado é serializado usando o formato especificado pela operação e retornado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="e23a3-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="e23a3-109">O exemplo a seguir mostra como retornar um código de status HTTP.</span><span class="sxs-lookup"><span data-stu-id="e23a3-109">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="e23a3-110">O exemplo a seguir mostra como retornar um código de status HTTP e informações extras em um tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e23a3-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="e23a3-111">`MyErrorDetail` é um tipo definido pelo usuário que contém informações adicionais sobre o erro ocorrido.</span><span class="sxs-lookup"><span data-stu-id="e23a3-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="e23a3-112">O código anterior retorna uma resposta HTTP com o código de status proibido e um corpo que contém uma instância do objeto `MyErrorDetails`.</span><span class="sxs-lookup"><span data-stu-id="e23a3-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="e23a3-113">O formato do objeto `MyErrorDetails` é determinado por:</span><span class="sxs-lookup"><span data-stu-id="e23a3-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="e23a3-114">O valor do parâmetro `ResponseFormat` do atributo <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> especificado na operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="e23a3-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="e23a3-115">O valor de <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="e23a3-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="e23a3-116">O valor da propriedade <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> acessando o <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="e23a3-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="e23a3-117">Para obter mais informações sobre como esses valores afetam a formatação da operação, consulte [formatação do WCF Web http](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="e23a3-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="e23a3-118"><xref:System.ServiceModel.Web.WebFaultException> é um <xref:System.ServiceModel.FaultException> e, portanto, pode ser usado como o modelo de programação de exceção de falha para serviços que expõem pontos de extremidade SOAP, bem como pontos de extremidade HTTP da Web.</span><span class="sxs-lookup"><span data-stu-id="e23a3-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23a3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e23a3-119">See also</span></span>

- [<span data-ttu-id="e23a3-120">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="e23a3-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="e23a3-121">Formatação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="e23a3-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [<span data-ttu-id="e23a3-122">Definindo e especificando falhas</span><span class="sxs-lookup"><span data-stu-id="e23a3-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [<span data-ttu-id="e23a3-123">Tratamento de exceções e falhas</span><span class="sxs-lookup"><span data-stu-id="e23a3-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="e23a3-124">Enviando e recebendo falhas</span><span class="sxs-lookup"><span data-stu-id="e23a3-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)

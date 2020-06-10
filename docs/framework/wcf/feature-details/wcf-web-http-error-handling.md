---
title: Tratamento de erros HTTP Web do WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: b1d41bebafa2795d390b120ad84475417389479b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598639"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="69e0e-102">Tratamento de erros HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="69e0e-102">WCF Web HTTP Error Handling</span></span>
<span data-ttu-id="69e0e-103">O tratamento de erros HTTP Web do Windows Communication Foundation (WCF) permite que você retorne erros de serviços HTTP Web WCF que especificam um código de status HTTP e retornam detalhes do erro usando o mesmo formato que a operação (por exemplo, XML ou JSON).</span><span class="sxs-lookup"><span data-stu-id="69e0e-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="69e0e-104">Tratamento de erros HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="69e0e-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="69e0e-105">A <xref:System.ServiceModel.Web.WebFaultException> classe define um construtor que permite que você especifique um código de status http.</span><span class="sxs-lookup"><span data-stu-id="69e0e-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="69e0e-106">Esse código de status é retornado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="69e0e-106">This status code is then returned to the client.</span></span> <span data-ttu-id="69e0e-107">Uma versão genérica da <xref:System.ServiceModel.Web.WebFaultException> classe permite que <xref:System.ServiceModel.Web.WebFaultException%601> você retorne um tipo definido pelo usuário que contém informações sobre o erro ocorrido.</span><span class="sxs-lookup"><span data-stu-id="69e0e-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="69e0e-108">Esse objeto personalizado é serializado usando o formato especificado pela operação e retornado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="69e0e-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="69e0e-109">O exemplo a seguir mostra como retornar um código de status HTTP.</span><span class="sxs-lookup"><span data-stu-id="69e0e-109">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="69e0e-110">O exemplo a seguir mostra como retornar um código de status HTTP e informações extras em um tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="69e0e-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="69e0e-111">`MyErrorDetail`é um tipo definido pelo usuário que contém informações adicionais sobre o erro ocorrido.</span><span class="sxs-lookup"><span data-stu-id="69e0e-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
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
  
 <span data-ttu-id="69e0e-112">O código anterior retorna uma resposta HTTP com o código de status proibido e um corpo que contém uma instância do `MyErrorDetails` objeto.</span><span class="sxs-lookup"><span data-stu-id="69e0e-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="69e0e-113">O formato do `MyErrorDetails` objeto é determinado por:</span><span class="sxs-lookup"><span data-stu-id="69e0e-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="69e0e-114">O valor do `ResponseFormat` parâmetro do <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo ou especificado na operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="69e0e-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="69e0e-115">O valor de <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span><span class="sxs-lookup"><span data-stu-id="69e0e-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="69e0e-116">O valor da <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> Propriedade acessando o <xref:System.ServiceModel.Web.OutgoingWebResponseContext> .</span><span class="sxs-lookup"><span data-stu-id="69e0e-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="69e0e-117">Para obter mais informações sobre como esses valores afetam a formatação da operação, consulte [formatação do WCF Web http](wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="69e0e-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="69e0e-118"><xref:System.ServiceModel.Web.WebFaultException>é um <xref:System.ServiceModel.FaultException> e, portanto, pode ser usado como o modelo de programação de exceção de falha para serviços que expõem pontos de extremidade SOAP, bem como pontos de extremidade http da Web.</span><span class="sxs-lookup"><span data-stu-id="69e0e-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e0e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69e0e-119">See also</span></span>

- [<span data-ttu-id="69e0e-120">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="69e0e-120">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="69e0e-121">Formatação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="69e0e-121">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)
- [<span data-ttu-id="69e0e-122">Definindo e especificando falhas</span><span class="sxs-lookup"><span data-stu-id="69e0e-122">Defining and Specifying Faults</span></span>](../defining-and-specifying-faults.md)
- [<span data-ttu-id="69e0e-123">Tratamento de exceções e falhas</span><span class="sxs-lookup"><span data-stu-id="69e0e-123">Handling Exceptions and Faults</span></span>](../extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="69e0e-124">Enviando e recebendo falhas</span><span class="sxs-lookup"><span data-stu-id="69e0e-124">Sending and Receiving Faults</span></span>](../sending-and-receiving-faults.md)

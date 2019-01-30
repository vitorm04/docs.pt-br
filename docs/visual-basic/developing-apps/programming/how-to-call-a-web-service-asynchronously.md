---
title: 'Como: Chamar um serviço Web de forma assíncrona (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 9127b0edce029f8b2944ddf692e85166ee8c89b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616141"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="9b894-102">Como: Chamar um serviço Web de forma assíncrona (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b894-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>
<span data-ttu-id="9b894-103">Este exemplo conecta um manipulador a um evento de manipulador assíncrono do serviço Web, para que ele possa recuperar o resultado de uma chamada de método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="9b894-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="9b894-104">Este exemplo usou o serviço Web DemoTemperatureService em `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="9b894-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>  
  
 <span data-ttu-id="9b894-105">Quando você faz referência a um serviço Web em seu projeto no IDE (Ambiente de Desenvolvimento Integrado) do Visual Studio, ele é adicionado ao objeto `My.WebServices`, e o IDE gera uma classe proxy do cliente para acesso a um serviço Web especificado</span><span class="sxs-lookup"><span data-stu-id="9b894-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>  
  
 <span data-ttu-id="9b894-106">A classe proxy permite chamar os métodos de serviço Web de forma síncrona, em que seu aplicativo aguarda até que a função seja concluída.</span><span class="sxs-lookup"><span data-stu-id="9b894-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="9b894-107">Além disso, o proxy cria membros adicionais para ajudar a chamar o método de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="9b894-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="9b894-108">Para cada função de serviço Web, *NameOfWebServiceFunction*, o proxy cria uma sub-rotina *NameOfWebServiceFunction*`Async`, um evento *NameOfWebServiceFunction*`Completed` e uma classe *NameOfWebServiceFunction*`CompletedEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="9b894-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="9b894-109">Este exemplo demonstra como usar os membros assíncronos para acessar a função `getTemp` do serviço Web DemoTemperatureService.</span><span class="sxs-lookup"><span data-stu-id="9b894-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b894-110">Esse código não funciona em aplicativos Web, pois o ASP.NET não oferece suporte ao objeto `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="9b894-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>  
  
### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="9b894-111">Para chamar um serviço Web de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="9b894-111">To call a Web service asynchronously</span></span>  
  
1.  <span data-ttu-id="9b894-112">Consulte o serviço Web DemoTemperatureService em `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="9b894-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="9b894-113">O endereço é</span><span class="sxs-lookup"><span data-stu-id="9b894-113">The address is</span></span>  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  <span data-ttu-id="9b894-114">Adicione um manipulador de eventos ao evento `getTempCompleted`:</span><span class="sxs-lookup"><span data-stu-id="9b894-114">Add an event handler for the `getTempCompleted` event:</span></span>  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9b894-115">Você não pode usar a instrução `Handles` para associar um manipulador de eventos aos eventos do objeto `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="9b894-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>  
  
3.  <span data-ttu-id="9b894-116">Adicione um campo para acompanhar se o manipulador de eventos tiver sido adicionado ao evento `getTempCompleted`:</span><span class="sxs-lookup"><span data-stu-id="9b894-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  <span data-ttu-id="9b894-117">Adicione um método para adicionar ao manipulador de eventos ao evento `getTempCompleted`, se necessário, e para chamar o método `getTempAsynch`:</span><span class="sxs-lookup"><span data-stu-id="9b894-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsynch` method:</span></span>  
  
    ```  
    Sub CallGetTempAsync(ByVal zipCode As Integer)  
        If Not handlerAttached Then  
            AddHandler My.WebServices.  
                TemperatureService.getTempCompleted,   
                AddressOf Me.TS_getTempCompleted  
            handlerAttached = True  
        End If  
        My.WebServices.TemperatureService.getTempAsync(zipCode)  
    End Sub  
    ```  
  
     <span data-ttu-id="9b894-118">Para chamar o método Web `getTemp` de forma assíncrona, chame o método `CallGetTempAsync`.</span><span class="sxs-lookup"><span data-stu-id="9b894-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="9b894-119">Quando o método Web for concluído, seu valor retornado será transmitido ao manipulador de eventos `getTempCompletedHandler`.</span><span class="sxs-lookup"><span data-stu-id="9b894-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b894-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b894-120">See also</span></span>
- [<span data-ttu-id="9b894-121">Acessando serviços Web do aplicativo</span><span class="sxs-lookup"><span data-stu-id="9b894-121">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [<span data-ttu-id="9b894-122">Objeto My.WebServices</span><span class="sxs-lookup"><span data-stu-id="9b894-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)

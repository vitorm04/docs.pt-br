---
title: "Como acessar propriedades específicas de HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
caps.latest.revision: 8
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6a0c5a2c3a159e4d10da03a584b29e4b77720534
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="c0cd3-102">Como acessar propriedades específicas de HTTP</span><span class="sxs-lookup"><span data-stu-id="c0cd3-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="c0cd3-103">Esta amostra explica como desligar o comportamento **Keep-alive** do HTTP e obter o número de versão do protocolo do servidor Web.</span><span class="sxs-lookup"><span data-stu-id="c0cd3-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0cd3-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0cd3-104">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =   
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c0cd3-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="c0cd3-105">Compiling the Code</span></span>  
 <span data-ttu-id="c0cd3-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c0cd3-106">This example requires:</span></span>  
  
-   <span data-ttu-id="c0cd3-107">Referências ao namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="c0cd3-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0cd3-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0cd3-108">See Also</span></span>  
 <span data-ttu-id="c0cd3-109">[Acessando a Internet por meio de um proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md) </span><span class="sxs-lookup"><span data-stu-id="c0cd3-109">[Accessing the Internet Through a Proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md) </span></span>  
 <span data-ttu-id="c0cd3-110">[Usando protocolos de aplicativo](../../../docs/framework/network-programming/using-application-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="c0cd3-110">[Using Application Protocols](../../../docs/framework/network-programming/using-application-protocols.md) </span></span>  
 [<span data-ttu-id="c0cd3-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="c0cd3-111">HTTP</span></span>](../../../docs/framework/network-programming/http.md)


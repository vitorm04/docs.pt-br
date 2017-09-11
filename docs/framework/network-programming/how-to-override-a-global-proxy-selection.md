---
title: "Como substituir uma seleção de proxy global"
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
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
caps.latest.revision: 8
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cecb98628231e6a8b2847043e3f3c2206c164ae3
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="2f119-102">Como substituir uma seleção de proxy global</span><span class="sxs-lookup"><span data-stu-id="2f119-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="2f119-103">Este exemplo envia uma **WebRequest** para www.contoso.com que substitui a seleção de proxy global com um servidor proxy chamado `alternateproxy` na porta 80.</span><span class="sxs-lookup"><span data-stu-id="2f119-103">This example sends a **WebRequest** to www.contoso.com that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f119-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f119-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2f119-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2f119-105">Compiling the Code</span></span>  
 <span data-ttu-id="2f119-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="2f119-106">This example requires:</span></span>  
  
-   <span data-ttu-id="2f119-107">Referências ao namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="2f119-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f119-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f119-108">See Also</span></span>  
 <span data-ttu-id="2f119-109">[Usando protocolos de aplicativo](../../../docs/framework/network-programming/using-application-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="2f119-109">[Using Application Protocols](../../../docs/framework/network-programming/using-application-protocols.md) </span></span>  
 [<span data-ttu-id="2f119-110">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="2f119-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)


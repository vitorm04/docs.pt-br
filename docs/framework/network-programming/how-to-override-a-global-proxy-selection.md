---
title: Como substituir uma seleção de proxy global
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 244315b5df4200524685bc5b9fb75a0d7fd9b39e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45609038"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="ff5f9-102">Como substituir uma seleção de proxy global</span><span class="sxs-lookup"><span data-stu-id="ff5f9-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="ff5f9-103">Este exemplo envia uma **WebRequest** para `www.contoso.com` que substitui a seleção de proxy global por um servidor proxy chamado `alternateproxy` na porta 80.</span><span class="sxs-lookup"><span data-stu-id="ff5f9-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff5f9-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff5f9-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff5f9-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="ff5f9-105">Compiling the Code</span></span>  
 <span data-ttu-id="ff5f9-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="ff5f9-106">This example requires:</span></span>  
  
-   <span data-ttu-id="ff5f9-107">Uma [diretiva `using`](~/docs/csharp/language-reference/keywords/using-directive.md) para o namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="ff5f9-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff5f9-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff5f9-108">See Also</span></span>  
 [<span data-ttu-id="ff5f9-109">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff5f9-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="ff5f9-110">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="ff5f9-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)

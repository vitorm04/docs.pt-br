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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44185029"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="38df6-102">Como substituir uma seleção de proxy global</span><span class="sxs-lookup"><span data-stu-id="38df6-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="38df6-103">Este exemplo envia uma **WebRequest** para `www.contoso.com` que substitui a seleção de proxy global por um servidor proxy chamado `alternateproxy` na porta 80.</span><span class="sxs-lookup"><span data-stu-id="38df6-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38df6-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38df6-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="38df6-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="38df6-105">Compiling the Code</span></span>  
 <span data-ttu-id="38df6-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="38df6-106">This example requires:</span></span>  
  
-   <span data-ttu-id="38df6-107">Uma [diretiva `using`](~/docs/csharp/language-reference/keywords/using-directive.md) para o namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="38df6-107">A [`using` directive](~/docs/csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38df6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38df6-108">See Also</span></span>  
 [<span data-ttu-id="38df6-109">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="38df6-109">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="38df6-110">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="38df6-110">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)

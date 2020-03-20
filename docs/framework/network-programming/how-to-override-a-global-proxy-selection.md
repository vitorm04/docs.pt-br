---
title: Como substituir uma seleção de proxy global
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048268"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="cc507-102">Como substituir uma seleção de proxy global</span><span class="sxs-lookup"><span data-stu-id="cc507-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="cc507-103">Este exemplo envia uma **WebRequest** para `www.contoso.com` que substitui a seleção de proxy global por um servidor proxy chamado `alternateproxy` na porta 80.</span><span class="sxs-lookup"><span data-stu-id="cc507-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc507-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc507-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cc507-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="cc507-105">Compiling the Code</span></span>  
 <span data-ttu-id="cc507-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="cc507-106">This example requires:</span></span>  
  
- <span data-ttu-id="cc507-107">Uma [ `using` diretiva](../../csharp/language-reference/keywords/using-directive.md) para o **System.Net** namespace.</span><span class="sxs-lookup"><span data-stu-id="cc507-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc507-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="cc507-108">See also</span></span>

- [<span data-ttu-id="cc507-109">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="cc507-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="cc507-110">Acessando a Internet através de um proxy</span><span class="sxs-lookup"><span data-stu-id="cc507-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)

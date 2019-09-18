---
title: 'Como: Substituir uma seleção de proxy global'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: 44845fb67aac4ff9ab9dda8cf4934153c8c4f23c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048268"
---
# <a name="how-to-override-a-global-proxy-selection"></a><span data-ttu-id="34b78-102">Como: Substituir uma seleção de proxy global</span><span class="sxs-lookup"><span data-stu-id="34b78-102">How to: Override a Global Proxy Selection</span></span>
<span data-ttu-id="34b78-103">Este exemplo envia uma **WebRequest** para `www.contoso.com` que substitui a seleção de proxy global por um servidor proxy chamado `alternateproxy` na porta 80.</span><span class="sxs-lookup"><span data-stu-id="34b78-103">This example sends a **WebRequest** to `www.contoso.com` that overrides the global proxy selection with a proxy server named `alternateproxy` on port 80.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34b78-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34b78-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="34b78-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="34b78-105">Compiling the Code</span></span>  
 <span data-ttu-id="34b78-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="34b78-106">This example requires:</span></span>  
  
- <span data-ttu-id="34b78-107">Uma [diretiva `using`](../../csharp/language-reference/keywords/using-directive.md) para o namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="34b78-107">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b78-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34b78-108">See also</span></span>

- [<span data-ttu-id="34b78-109">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="34b78-109">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="34b78-110">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="34b78-110">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)

---
title: 'Como: Habilitar uma WebRequest a usar um proxy para se comunicar com a Internet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: d569603fe22e5d8c8f59d21c2777c7c1bfcd531d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048290"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="255bc-102">Como: Habilitar uma WebRequest a usar um proxy para se comunicar com a Internet</span><span class="sxs-lookup"><span data-stu-id="255bc-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="255bc-103">Este exemplo cria uma instância de proxy global que permitirá que qualquer <xref:System.Net.WebRequest> use um proxy para se comunicar com a Internet.</span><span class="sxs-lookup"><span data-stu-id="255bc-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="255bc-104">O exemplo supõe que o servidor proxy se chama `webproxy` e que ele se comunica na porta 80, a porta HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="255bc-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="255bc-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="255bc-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="255bc-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="255bc-106">Compiling the Code</span></span>  
 <span data-ttu-id="255bc-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="255bc-107">This example requires:</span></span>  
  
- <span data-ttu-id="255bc-108">Uma [diretiva `using`](../../csharp/language-reference/keywords/using-directive.md) para o namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="255bc-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="255bc-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="255bc-109">See also</span></span>

- [<span data-ttu-id="255bc-110">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="255bc-110">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="255bc-111">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="255bc-111">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)

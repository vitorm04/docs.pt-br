---
title: 'Como: Habilitar uma WebRequest a usar um proxy para se comunicar com a Internet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: a2179e767a0556f5223f2f4c1cc91708133120a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103695"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="fbe6d-102">Como: Habilitar uma WebRequest a usar um proxy para se comunicar com a Internet</span><span class="sxs-lookup"><span data-stu-id="fbe6d-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="fbe6d-103">Este exemplo cria uma instância de proxy global que permitirá que qualquer <xref:System.Net.WebRequest> use um proxy para se comunicar com a Internet.</span><span class="sxs-lookup"><span data-stu-id="fbe6d-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="fbe6d-104">O exemplo supõe que o servidor proxy se chama `webproxy` e que ele se comunica na porta 80, a porta HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="fbe6d-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbe6d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fbe6d-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fbe6d-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fbe6d-106">Compiling the Code</span></span>  
 <span data-ttu-id="fbe6d-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="fbe6d-107">This example requires:</span></span>  
  
-   <span data-ttu-id="fbe6d-108">Uma [diretiva `using`](../../csharp/language-reference/keywords/using-directive.md) para o namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="fbe6d-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe6d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbe6d-109">See also</span></span>

- [<span data-ttu-id="fbe6d-110">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="fbe6d-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
- [<span data-ttu-id="fbe6d-111">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="fbe6d-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)

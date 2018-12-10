---
title: Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 1b10d895478a88556cf1d716480de568c8e9c9ad
ms.sourcegitcommit: 2151690e10d91545e2c20d6b5ad222c162b6b83d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2018
ms.locfileid: "50190431"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="a70c2-102">Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet</span><span class="sxs-lookup"><span data-stu-id="a70c2-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="a70c2-103">Este exemplo cria uma instância de proxy global que permitirá que qualquer <xref:System.Net.WebRequest> use um proxy para se comunicar com a Internet.</span><span class="sxs-lookup"><span data-stu-id="a70c2-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="a70c2-104">O exemplo supõe que o servidor proxy se chama `webproxy` e que ele se comunica na porta 80, a porta HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="a70c2-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a70c2-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a70c2-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a70c2-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a70c2-106">Compiling the Code</span></span>  
 <span data-ttu-id="a70c2-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a70c2-107">This example requires:</span></span>  
  
-   <span data-ttu-id="a70c2-108">Uma [diretiva `using`](../../csharp/language-reference/keywords/using-directive.md) para o namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="a70c2-108">A [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a70c2-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a70c2-109">See Also</span></span>  
 [<span data-ttu-id="a70c2-110">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="a70c2-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="a70c2-111">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="a70c2-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)

---
title: Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039545"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="5495e-102">Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet</span><span class="sxs-lookup"><span data-stu-id="5495e-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="5495e-103">Este exemplo cria uma instância de proxy global que permitirá que qualquer <xref:System.Net.WebRequest> use um proxy para se comunicar com a Internet.</span><span class="sxs-lookup"><span data-stu-id="5495e-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="5495e-104">O exemplo supõe que o servidor proxy se chama `webproxy` e que ele se comunica na porta 80, a porta HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="5495e-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="5495e-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5495e-105">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="5495e-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5495e-106">Compiling the Code</span></span>

<span data-ttu-id="5495e-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="5495e-107">This example requires:</span></span>

- <span data-ttu-id="5495e-108">Uma [ `using` diretiva](../../csharp/language-reference/keywords/using-directive.md) C# para o **System.Net** namespace.</span><span class="sxs-lookup"><span data-stu-id="5495e-108">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="5495e-109">Uma [ `Imports` declaração](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) visual básica para o **System.Net** namespace.</span><span class="sxs-lookup"><span data-stu-id="5495e-109">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="5495e-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="5495e-110">See also</span></span>

- [<span data-ttu-id="5495e-111">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="5495e-111">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="5495e-112">Acessando a Internet através de um proxy</span><span class="sxs-lookup"><span data-stu-id="5495e-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)

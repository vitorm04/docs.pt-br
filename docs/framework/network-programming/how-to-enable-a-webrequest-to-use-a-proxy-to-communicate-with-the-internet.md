---
title: Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet
description: Saiba como criar uma instância de proxy global para permitir que qualquer WebRequest use um proxy para se comunicar com a Internet na .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 0fc33cea3f5a7fe4669b110e53e71afdb9561c23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502529"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="23691-103">Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet</span><span class="sxs-lookup"><span data-stu-id="23691-103">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>

<span data-ttu-id="23691-104">Este exemplo cria uma instância de proxy global que permitirá que qualquer <xref:System.Net.WebRequest> use um proxy para se comunicar com a Internet.</span><span class="sxs-lookup"><span data-stu-id="23691-104">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="23691-105">O exemplo supõe que o servidor proxy se chama `webproxy` e que ele se comunica na porta 80, a porta HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="23691-105">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>

## <a name="example"></a><span data-ttu-id="23691-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23691-106">Example</span></span>

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a><span data-ttu-id="23691-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="23691-107">Compiling the Code</span></span>

<span data-ttu-id="23691-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="23691-108">This example requires:</span></span>

- <span data-ttu-id="23691-109">Uma [ `using` diretiva](../../csharp/language-reference/keywords/using-directive.md) C# para o namespace **System.net** .</span><span class="sxs-lookup"><span data-stu-id="23691-109">A C# [`using` directive](../../csharp/language-reference/keywords/using-directive.md) for the **System.Net** namespace.</span></span>
- <span data-ttu-id="23691-110">Uma [ `Imports` instrução](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic para o namespace **System.net** .</span><span class="sxs-lookup"><span data-stu-id="23691-110">A Visual Basic [`Imports` statement](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the **System.Net** namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="23691-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="23691-111">See also</span></span>

- [<span data-ttu-id="23691-112">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="23691-112">Using Application Protocols</span></span>](using-application-protocols.md)
- [<span data-ttu-id="23691-113">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="23691-113">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)

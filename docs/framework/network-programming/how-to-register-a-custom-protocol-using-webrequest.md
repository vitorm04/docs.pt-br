---
title: Como registrar um protocolo personalizado usando WebRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048260"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="e2fd0-102">Como registrar um protocolo personalizado usando WebRequest</span><span class="sxs-lookup"><span data-stu-id="e2fd0-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="e2fd0-103">Este exemplo mostra como registrar uma classe específica de protocolo que é definida em outro local.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="e2fd0-104">Neste exemplo, `CustomWebRequestCreator` é o objeto implementado pelo usuário que implementa o método **create** que retorna o objeto `CustomWebRequest`.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="e2fd0-105">O exemplo de código pressupõe que você tenha escrito o código `CustomWebRequest` que implementa o protocolo personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2fd0-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2fd0-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e2fd0-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e2fd0-107">Compiling the Code</span></span>  
 <span data-ttu-id="e2fd0-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e2fd0-108">This example requires:</span></span>  
  
 <span data-ttu-id="e2fd0-109">Referências ao namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="e2fd0-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fd0-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2fd0-110">See also</span></span>

- [<span data-ttu-id="e2fd0-111">Programando protocolos conectáveis</span><span class="sxs-lookup"><span data-stu-id="e2fd0-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)

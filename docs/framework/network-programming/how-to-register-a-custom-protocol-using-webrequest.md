---
title: Como registrar um protocolo personalizado usando WebRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5f863aa61058e87a7911bab3b02c3ba345419596
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193598"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="a2d78-102">Como registrar um protocolo personalizado usando WebRequest</span><span class="sxs-lookup"><span data-stu-id="a2d78-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="a2d78-103">Este exemplo mostra como registrar uma classe específica de protocolo que é definido em outro local.</span><span class="sxs-lookup"><span data-stu-id="a2d78-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="a2d78-104">Neste exemplo, `CustomWebRequestCreator` é o objeto implementado pelo usuário que implementa o método **create** que retorna o objeto `CustomWebRequest`.</span><span class="sxs-lookup"><span data-stu-id="a2d78-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="a2d78-105">O exemplo de código pressupõe que você tenha escrito o código `CustomWebRequest` que implementa o protocolo personalizado.</span><span class="sxs-lookup"><span data-stu-id="a2d78-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2d78-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2d78-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a2d78-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a2d78-107">Compiling the Code</span></span>  
 <span data-ttu-id="a2d78-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a2d78-108">This example requires:</span></span>  
  
 <span data-ttu-id="a2d78-109">Referências ao namespace <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="a2d78-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d78-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2d78-110">See Also</span></span>  
 [<span data-ttu-id="a2d78-111">Programando protocolos conectáveis</span><span class="sxs-lookup"><span data-stu-id="a2d78-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)

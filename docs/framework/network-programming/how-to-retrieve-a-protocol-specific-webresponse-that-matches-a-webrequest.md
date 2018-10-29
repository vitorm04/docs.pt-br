---
title: Como recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: f1da226fb62c55f37183404765430c094f1cd63f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188268"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="9cf60-102">Como recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest</span><span class="sxs-lookup"><span data-stu-id="9cf60-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="9cf60-103">Esse exemplo mostra como recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest.</span><span class="sxs-lookup"><span data-stu-id="9cf60-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cf60-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9cf60-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9cf60-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9cf60-105">Compiling the Code</span></span>  
 <span data-ttu-id="9cf60-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="9cf60-106">This example requires:</span></span>  
  
-   <span data-ttu-id="9cf60-107">Referências ao namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="9cf60-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf60-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cf60-108">See Also</span></span>  
 [<span data-ttu-id="9cf60-109">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="9cf60-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)

---
title: Como recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d15b63482cb37fa986dd065beefcf6baee4c8312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394206"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="b129c-102">Como recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest</span><span class="sxs-lookup"><span data-stu-id="b129c-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="b129c-103">Esse exemplo mostra como recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest.</span><span class="sxs-lookup"><span data-stu-id="b129c-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b129c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b129c-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b129c-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b129c-105">Compiling the Code</span></span>  
 <span data-ttu-id="b129c-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="b129c-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b129c-107">Referências ao namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="b129c-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b129c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b129c-108">See Also</span></span>  
 [<span data-ttu-id="b129c-109">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="b129c-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)

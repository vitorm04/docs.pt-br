---
title: 'Como: Solicitar uma página da Web e recuperar os resultados como um fluxo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: b3d24a958ec93084d03d2ad2e0eb6d9d2507e155
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048172"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="a511f-102">Como: Solicitar uma página da Web e recuperar os resultados como um fluxo</span><span class="sxs-lookup"><span data-stu-id="a511f-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="a511f-103">Este exemplo mostra como solicitar uma página da Web e recuperar os resultados em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="a511f-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a511f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a511f-104">Example</span></span>  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a511f-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a511f-105">Compiling the Code</span></span>  
 <span data-ttu-id="a511f-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="a511f-106">This example requires:</span></span>  
  
- <span data-ttu-id="a511f-107">Referências aos namespaces <xref:System.IO> e <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="a511f-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a511f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a511f-108">See also</span></span>

- [<span data-ttu-id="a511f-109">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="a511f-109">Requesting Data</span></span>](requesting-data.md)

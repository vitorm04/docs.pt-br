---
title: Como solicitar uma página da Web e recuperar os resultados como um fluxo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 31856e7fc7136b3bdb8fab9fdf8185de32a3007a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395207"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="38318-102">Como solicitar uma página da Web e recuperar os resultados como um fluxo</span><span class="sxs-lookup"><span data-stu-id="38318-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="38318-103">Este exemplo mostra como solicitar uma página da Web e recuperar os resultados em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="38318-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38318-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38318-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="38318-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="38318-105">Compiling the Code</span></span>  
 <span data-ttu-id="38318-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="38318-106">This example requires:</span></span>  
  
-   <span data-ttu-id="38318-107">Referências aos namespaces <xref:System.IO> e <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="38318-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38318-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38318-108">See Also</span></span>  
 [<span data-ttu-id="38318-109">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="38318-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)

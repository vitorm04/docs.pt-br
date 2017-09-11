---
title: "Como solicitar uma página da Web e recuperar os resultados como um fluxo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
caps.latest.revision: 12
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ec19e46289131ec137081c610c1a8194ad22611f
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="4c45a-102">Como solicitar uma página da Web e recuperar os resultados como um fluxo</span><span class="sxs-lookup"><span data-stu-id="4c45a-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="4c45a-103">Este exemplo mostra como solicitar uma página da Web e recuperar os resultados em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="4c45a-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c45a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c45a-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4c45a-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="4c45a-105">Compiling the Code</span></span>  
 <span data-ttu-id="4c45a-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="4c45a-106">This example requires:</span></span>  
  
-   <span data-ttu-id="4c45a-107">Referências aos namespaces <xref:System.IO> e <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="4c45a-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c45a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c45a-108">See Also</span></span>  
 [<span data-ttu-id="4c45a-109">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="4c45a-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)


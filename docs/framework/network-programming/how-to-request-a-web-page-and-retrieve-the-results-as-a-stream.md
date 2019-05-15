---
title: 'Como: Solicitar uma página da Web e recuperar os resultados como um fluxo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 74cb739d381c0b1422d9277be8c3c338a46f8fba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647413"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="9e042-102">Como: Solicitar uma página da Web e recuperar os resultados como um fluxo</span><span class="sxs-lookup"><span data-stu-id="9e042-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="9e042-103">Este exemplo mostra como solicitar uma página da Web e recuperar os resultados em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="9e042-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e042-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e042-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9e042-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9e042-105">Compiling the Code</span></span>  
 <span data-ttu-id="9e042-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="9e042-106">This example requires:</span></span>  
  
- <span data-ttu-id="9e042-107">Referências aos namespaces <xref:System.IO> e <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="9e042-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e042-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e042-108">See also</span></span>

- [<span data-ttu-id="9e042-109">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="9e042-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)

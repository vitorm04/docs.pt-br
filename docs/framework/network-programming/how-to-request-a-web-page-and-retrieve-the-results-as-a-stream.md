---
title: Como solicitar uma página da Web e recuperar os resultados como um fluxo
description: Este exemplo mostra como solicitar uma página da Web e recuperar os resultados em um fluxo no .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: bd57f9af6be29c783d044e785ebb36aaa8592df2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502477"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="75230-103">Como solicitar uma página da Web e recuperar os resultados como um fluxo</span><span class="sxs-lookup"><span data-stu-id="75230-103">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="75230-104">Este exemplo mostra como solicitar uma página da Web e recuperar os resultados em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="75230-104">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="75230-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="75230-105">Example</span></span>

```csharp
var myClient = new WebClient();
Stream response = myClient.OpenRead("https://docs.microsoft.com/dotnet/");
// The stream data is used here.
response.Close();
```

```vb
Dim myClient As New WebClient()
Dim response As Stream = myClient.OpenRead("https://docs.microsoft.com/dotnet/")
' The stream data is used here.
response.Close()
```

## <a name="compiling-the-code"></a><span data-ttu-id="75230-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="75230-106">Compiling the Code</span></span>

 <span data-ttu-id="75230-107">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="75230-107">This example requires:</span></span>

- <span data-ttu-id="75230-108">Referências aos namespaces <xref:System.IO> e <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="75230-108">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="75230-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="75230-109">See also</span></span>

- [<span data-ttu-id="75230-110">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="75230-110">Requesting Data</span></span>](requesting-data.md)

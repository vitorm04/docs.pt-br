---
title: 'Como: Solicitar uma página da Web e recuperar os resultados como um fluxo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 65bda268cd77959dbcd786c365d0a30c324b89ce
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393114"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Como: Solicitar uma página da Web e recuperar os resultados como um fluxo

Este exemplo mostra como solicitar uma página da Web e recuperar os resultados em um fluxo.
  
## <a name="example"></a>Exemplo

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

## <a name="compiling-the-code"></a>Compilando o código

 Este exemplo requer:

- Referências aos namespaces <xref:System.IO> e <xref:System.Net>.

## <a name="see-also"></a>Consulte também

- [Solicitando dados](requesting-data.md)

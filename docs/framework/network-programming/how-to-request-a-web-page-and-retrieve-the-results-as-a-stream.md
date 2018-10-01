---
title: Como solicitar uma página da Web e recuperar os resultados como um fluxo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2ceaa7cbaf2035276a0ba0105f3969f0249c6132
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47402598"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Como solicitar uma página da Web e recuperar os resultados como um fluxo
Este exemplo mostra como solicitar uma página da Web e recuperar os resultados em um fluxo.  
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos namespaces <xref:System.IO> e <xref:System.Net>.  
  
## <a name="see-also"></a>Consulte também  
 [Solicitando dados](../../../docs/framework/network-programming/requesting-data.md)

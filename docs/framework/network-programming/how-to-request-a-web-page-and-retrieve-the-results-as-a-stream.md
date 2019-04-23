---
title: 'Como: Solicitar uma página da Web e recuperar os resultados como um fluxo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 23c094f0a3f528750c9589dbc99a0ada86236967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097194"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Como: Solicitar uma página da Web e recuperar os resultados como um fluxo
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

- [Solicitando dados](../../../docs/framework/network-programming/requesting-data.md)

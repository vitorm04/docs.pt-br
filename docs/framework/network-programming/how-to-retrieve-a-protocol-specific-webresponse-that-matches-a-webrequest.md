---
title: 'Como: Recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 21a5a81c6a5457897078db03fe35eaff330ed62d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647362"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>Como: Recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest
Esse exemplo mostra como recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências ao namespace **System.Net**.  
  
## <a name="see-also"></a>Consulte também

- [Solicitando dados](../../../docs/framework/network-programming/requesting-data.md)

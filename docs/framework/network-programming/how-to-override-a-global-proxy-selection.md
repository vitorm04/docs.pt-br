---
title: 'Como: Substituir uma seleção de proxy global'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
ms.openlocfilehash: f822aa18b6eecaa1b1302ad6cc6b94f0b016e330
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127368"
---
# <a name="how-to-override-a-global-proxy-selection"></a>Como: Substituir uma seleção de proxy global
Este exemplo envia uma **WebRequest** para `www.contoso.com` que substitui a seleção de proxy global por um servidor proxy chamado `alternateproxy` na porta 80.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
req.Proxy = new WebProxy("http://alternateproxy:80/");  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com/")  
req.Proxy = New WebProxy("http://alternateproxy:80/")  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma [diretiva `using`](~/docs/csharp/language-reference/keywords/using-directive.md) para o namespace **System.Net**.  
  
## <a name="see-also"></a>Consulte também

- [Usando protocolos de aplicativo](../../../docs/framework/network-programming/using-application-protocols.md)
- [Acessando a Internet por meio de um proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)

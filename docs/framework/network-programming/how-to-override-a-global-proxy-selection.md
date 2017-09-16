---
title: "Como substituir uma seleção de proxy global"
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
ms.assetid: 0da481a9-b414-4230-beb0-e3ceba882fe5
caps.latest.revision: 8
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cecb98628231e6a8b2847043e3f3c2206c164ae3
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-override-a-global-proxy-selection"></a>Como substituir uma seleção de proxy global
Este exemplo envia uma **WebRequest** para www.contoso.com que substitui a seleção de proxy global com um servidor proxy chamado `alternateproxy` na porta 80.  
  
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
  
-   Referências ao namespace **System.Net**.  
  
## <a name="see-also"></a>Consulte também  
 [Usando protocolos de aplicativo](../../../docs/framework/network-programming/using-application-protocols.md)   
 [Acessando a Internet por meio de um proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)


---
title: Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 86bf21580db9bc6d9890f0935e283b653ba2e0b5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397784"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet
Este exemplo cria uma instância de proxy global que permitirá que qualquer <xref:System.Net.WebRequest> use um proxy para se comunicar com a Internet. O exemplo supõe que o servidor proxy se chama `webproxy` e que ele se comunica na porta 80, a porta HTTP padrão.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências ao namespace **System.Net**.  
  
## <a name="see-also"></a>Consulte também  
 [Usando protocolos de aplicativo](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Acessando a Internet por meio de um proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)

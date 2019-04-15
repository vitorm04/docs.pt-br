---
title: 'Como: Habilitar uma WebRequest a usar um proxy para se comunicar com a Internet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: a2179e767a0556f5223f2f4c1cc91708133120a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103695"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Como: Habilitar uma WebRequest a usar um proxy para se comunicar com a Internet
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
  
-   Uma [diretiva `using`](../../csharp/language-reference/keywords/using-directive.md) para o namespace **System.Net**.  
  
## <a name="see-also"></a>Consulte também

- [Usando protocolos de aplicativo](../../../docs/framework/network-programming/using-application-protocols.md)
- [Acessando a Internet por meio de um proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)

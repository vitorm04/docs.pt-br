---
title: Como registrar um protocolo personalizado usando WebRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1f78f98f94daa51c17a1294285e13dfddd457106
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47230963"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Como registrar um protocolo personalizado usando WebRequest
Este exemplo mostra como registrar uma classe específica de protocolo que é definido em outro local. Neste exemplo, `CustomWebRequestCreator` é o objeto implementado pelo usuário que implementa o método **create** que retorna o objeto `CustomWebRequest`. O exemplo de código pressupõe que você tenha escrito o código `CustomWebRequest` que implementa o protocolo personalizado.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
 Referências ao namespace <xref:System.Net>.  
  
## <a name="see-also"></a>Consulte também  
 [Programando protocolos conectáveis](../../../docs/framework/network-programming/programming-pluggable-protocols.md)

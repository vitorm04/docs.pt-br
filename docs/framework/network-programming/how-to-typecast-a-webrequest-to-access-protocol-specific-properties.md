---
title: Como fazer a conversão de tipo de uma WebRequest para acessar propriedades específicas de protocolo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: ec5b9f1db17cf1c90484b0a44063efef9fa16cf9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50180082"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>Como fazer a conversão de tipo de uma WebRequest para acessar propriedades específicas de protocolo
Este exemplo mostra como fazer a conversão de tipo de uma WebRequest para que você possa acessar propriedades específicas de protocolo.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Programando protocolos conectáveis](../../../docs/framework/network-programming/programming-pluggable-protocols.md)

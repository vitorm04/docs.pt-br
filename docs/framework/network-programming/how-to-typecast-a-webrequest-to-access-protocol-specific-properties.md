---
title: Como fazer a conversão de tipo de uma WebRequest para acessar propriedades específicas de protocolo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b4cde78ead9bdb8becf0f12497f4b37ad5a73bb3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47421516"
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

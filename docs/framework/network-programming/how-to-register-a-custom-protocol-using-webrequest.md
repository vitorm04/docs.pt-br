---
title: Como registrar um protocolo personalizado usando WebRequest
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
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: 11
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4ab725a2ef25c0b5898c9a9788f27781b0ef0ef7
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# Como registrar um protocolo personalizado usando WebRequest
Este exemplo mostra como registrar uma classe específica de protocolo que é definido em outro local. Neste exemplo, `CustomWebRequestCreator` é o objeto implementado pelo usuário que implementa o método **create** que retorna o objeto `CustomWebRequest`. O exemplo de código pressupõe que você tenha escrito o código `CustomWebRequest` que implementa o protocolo personalizado.  
  
## Exemplo  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## Compilando o código  
 Este exemplo requer:  
  
 Referências ao namespace <xref:System.Net>.  
  
## Consulte também  
 [Programando protocolos conectáveis](../../../docs/framework/network-programming/programming-pluggable-protocols.md)


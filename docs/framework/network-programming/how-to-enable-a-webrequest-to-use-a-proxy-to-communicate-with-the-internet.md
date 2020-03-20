---
title: Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
ms.openlocfilehash: 8b38973e4cb2c83ce32b8a08e54d828a8eeef879
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73039545"
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a>Como habilitar uma WebRequest a usar um proxy para se comunicar com a Internet

Este exemplo cria uma instância de proxy global que permitirá que qualquer <xref:System.Net.WebRequest> use um proxy para se comunicar com a Internet. O exemplo supõe que o servidor proxy se chama `webproxy` e que ele se comunica na porta 80, a porta HTTP padrão.

## <a name="example"></a>Exemplo

```csharp
var proxyObject = new WebProxy("http://webproxy:80/");
GlobalProxySelection.Select = proxyObject;
```

```vb
Dim proxyObject As New WebProxy("http://webproxy:80/")
GlobalProxySelection.Select = proxyObject
```

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Uma [ `using` diretiva](../../csharp/language-reference/keywords/using-directive.md) C# para o **System.Net** namespace.
- Uma [ `Imports` declaração](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) visual básica para o **System.Net** namespace.

## <a name="see-also"></a>Confira também

- [Usando protocolos de aplicativo](using-application-protocols.md)
- [Acessando a Internet através de um proxy](accessing-the-internet-through-a-proxy.md)

---
title: Serialização de caracteres de controle com DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b6468bc4ae37765d969a1f92b16967cc656ab7ff
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452624"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Mitigação: serialização de caracteres de controle com o DataContractJsonSerializer

A partir do .NET Framework 4,7, a maneira como os caracteres de controle são serializados com a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> foi alterada para estar em conformidade com ECMAScript V6 e V8. 
 
## <a name="impact"></a>Impacto

No .NET Framework 4.6.2 e versões anteriores, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não serializava alguns caracteres de controle especiais, como `\b`, `\f`e `\t`, de forma que fosse compatível com os padrões ECMAScript V6 e V8.

Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4,7, a serialização desses caracteres de controle é compatível com ECMAScript V6 e V8. As seguintes APIs são afetadas:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Atenuação

Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4,7, esse comportamento é habilitado por padrão.

Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção `<runtime>` do arquivo app.config ou web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Confira também

- [Compatibilidade de aplicativos](application-compatibility.md)

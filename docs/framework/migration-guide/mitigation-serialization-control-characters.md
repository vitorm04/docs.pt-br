---
title: Serialização de caracteres de controle com DataContractJsonSerializer
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: b60b78f9ee944552fafbe75754ecd29d60dd4093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181204"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Mitigação: Serialização de caracteres de controle com o DataContractJsonSerializer

Começando com .NET Framework 4.7, a forma como <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> os caracteres de controle são serializados com o mudou para estar em conformidade com eCMAScript V6 e V8.

## <a name="impact"></a>Impacto

No .NET Framework 4.6.2 e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nas versões anteriores, `\b`o `\f`não `\t`serializava alguns caracteres de controle especiais, como , e , de uma forma compatível com os padrões ECMAScript V6 e V8.

Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4.7, a serialização desses caracteres de controle é compatível com ECMAScript V6 e V8. As seguintes APIs são afetadas:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>

## <a name="mitigation"></a>Atenuação

Para aplicativos que visam versões do .NET Framework a partir do .NET Framework 4.7, esse comportamento é ativado por padrão.

Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção `<runtime>` do arquivo app.config ou web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```

## <a name="see-also"></a>Confira também

- [Compatibilidade de aplicativos](application-compatibility.md)

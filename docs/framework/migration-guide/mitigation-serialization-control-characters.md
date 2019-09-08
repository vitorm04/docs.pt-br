---
title: 'Mitigação: Serialização de caracteres de controle com o DataContractJsonSerializer'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b26c8cc01b7af1c3b345d2f274a1d25a19d689
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789851"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a>Mitigação: Serialização de caracteres de controle com o DataContractJsonSerializer

A partir do .NET Framework 4.7, a maneira com a qual os caracteres de controle são serializados com o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> foi alterada para estar em conformidade com o ECMAScript V6 e V8. 
 
## <a name="impact"></a>Impacto

No .NET framework 4.6.2 e nas versões anteriores, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> não serializava alguns caracteres de controle especiais, como `\b`, `\f` e `\t`, de uma forma compatível com os padrões ECMAScript V6 e V8.

Para aplicativos destinados a versões do .NET Framework, a partir do .NET Framework 4.7, a serialização desses caracteres de controle é compatível com o ECMAScript V6 e V8. As seguintes APIs são afetadas:

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a>Redução

Para aplicativos destinados a versões do .NET Framework, a partir do .NET Framework 4.7, esse comportamento é habilitado por padrão.

Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção `<runtime>` do arquivo app.config ou web.config:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a>Consulte também

- [Alterações de redirecionamento no .NET Framework 4.7](retargeting-changes-in-the-net-framework-4-7.md)

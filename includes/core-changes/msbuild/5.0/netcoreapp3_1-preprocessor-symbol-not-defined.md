---
ms.openlocfilehash: de35df21d1887bc95a3106edba312c53daad8b68
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654726"
---
### <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a>NETCOREAPP3_1 símbolo de pré-processador não está definido ao direcionar para o .NET 5

No .NET 5,0 RC2 e versões posteriores, os projetos não definem mais os símbolos de pré-processador para versões anteriores, mas apenas para a versão que eles visam. Esse é o mesmo comportamento do .NET Core 1,0-3,1.

#### <a name="version-introduced"></a>Versão introduzida

5,0 RC2

#### <a name="change-description"></a>Descrição das alterações

No .NET 5,0 Preview 7 até RC1, projetos que visam `net5.0` definir tanto os símbolos como os `NETCOREAPP3_1` de `NET5_0` pré-processador. A intenção por trás dessa mudança de comportamento era que, a partir do .NET 5,0, os símbolos de compilação condicional [seriam cumulativos](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).

No .NET 5,0 RC2 e posterior, os projetos definem apenas símbolos para os monikers do Framework de destino (TFM) que ele tem como destino e não para versões anteriores.

#### <a name="reason-for-change"></a>Motivo da alteração

A alteração da visualização 7 foi revertida devido aos comentários do cliente. A definição de símbolos para versões anteriores surpreendeu e confundiu clientes, e algumas assumiu que era um bug no compilador C#.

#### <a name="recommended-action"></a>Ação recomendada

Certifique-se de que sua `#if` lógica não assuma que `NETCOREAPP3_1` é definida quando o projeto é direcionado `net5.0` ou superior. Em vez disso, suponha que `NETCOREAPP3_1` seja definido apenas quando o projeto se destina explicitamente `netcoreapp3.1` .

Por exemplo, se o seu projeto tem vários destinos para .NET Core 2,1 e .NET Core 3,1 e você chama as APIs que foram introduzidas no .NET Core 3,1, sua `#if` lógica deve ter a seguinte aparência:

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

#### <a name="category"></a>Categoria

MSBuild

#### <a name="affected-apis"></a>APIs afetadas

N/D

<!--

#### Affected APIs

Not detectable via API analysis.

-->

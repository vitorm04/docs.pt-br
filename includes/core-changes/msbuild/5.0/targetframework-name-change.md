---
ms.openlocfilehash: 1ddc2cea19872b44ff9659bcebd76117587ea89a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159477"
---
### <a name="targetframework-change-from-netcoreapp-to-net"></a>TargetFramework alterar de netcoreapp para net

O valor da Propriedade MSBuild `TargetFramework` foi alterado de `netcoreapp3.1` para `net5.0` . Isso pode interromper o código que depende da análise do valor de `TargetFramework` .

#### <a name="version-introduced"></a>Versão introduzida

5.0

#### <a name="change-description"></a>Descrição das alterações

No .NET Core 1,0-3,1, o valor da Propriedade MSBuild `TargetFramework` começa com `netcoreapp` , por exemplo, `netcoreapp3.1` para aplicativos direcionados ao .NET Core 3,1. A partir do .NET 5,0, esse valor é simplificado apenas para começar `net` , por exemplo, `net5.0` para o .NET 5,0.

Para obter mais informações, consulte [o futuro de .net Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) e [nomes de estrutura de destino no .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).

#### <a name="reason-for-change"></a>Motivo da alteração

- Simplifica o `TargetFramework` valor.
- Permite que os projetos incluam um `TargetPlatform` na `TargetFramework` propriedade.

#### <a name="recommended-action"></a>Ação recomendada

Se você tiver uma lógica que analise o valor de `TargetFramework` , você precisará atualizá-la. Por exemplo, a seguinte condição do MSBuild depende do valor de `TargetFramework` .

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

Para esse requisito, você pode atualizar o código para comparar o identificador de estrutura de destino.

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

#### <a name="category"></a>Categoria

MSBuild

#### <a name="affected-apis"></a>APIs afetadas

N/D

<!--

#### Affected APIs

Not detectable via API analysis.

-->

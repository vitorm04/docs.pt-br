---
ms.openlocfilehash: 54bee14f6de409550357194e905b6ee5d8ef8f18
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678987"
---
### <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>OutputType definido como WinExe para aplicativos WPF e WinForms

`OutputType` é definido automaticamente como `WinExe` para Windows Presentation Foundation (WPF) e Windows Forms aplicativos. Quando `OutputType` é definido como `WinExe` , uma janela do console não é aberta quando o aplicativo é executado.

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, o valor especificado para `OutputType` no arquivo de projeto é usado. Por exemplo:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

A partir do .NET 5,0, `OutputType` é definido automaticamente como `WinExe` para aplicativos do WPF e Windows Forms. Por exemplo:

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

#### <a name="reason-for-change"></a>Motivo da alteração

Supõe-se que a maioria dos usuários não queira que uma janela do console seja aberta quando um aplicativo do WPF ou Windows Forms é executado. Além disso, [agora que esses tipos de aplicativos usam o SDK do .net](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) em vez do SDK de área de trabalho do Windows, o padrão correto será definido. Além disso, quando o suporte para o destino do iOS e do Android for adicionado, será mais fácil realizar vários destinos entre várias plataformas se todos usarem o mesmo tipo de saída.

#### <a name="version-introduced"></a>Versão introduzida

.NET 5,0 Preview 8

#### <a name="recommended-action"></a>Ação recomendada

Nenhuma ação é necessária em sua parte. No entanto, se você quiser reverter para o comportamento antigo, defina a `DisableWinExeOutputInference` propriedade como `true` em seu arquivo de projeto.

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

#### <a name="category"></a>Categoria

- Windows Forms
- Windows Presentation Framework (WPF)

#### <a name="affected-apis"></a>APIs afetadas

Não detectável via análise de API.

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->

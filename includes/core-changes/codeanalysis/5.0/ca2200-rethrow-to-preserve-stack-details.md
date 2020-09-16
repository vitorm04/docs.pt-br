---
ms.openlocfilehash: b697bbf6844759de8babd4245667e7b333884ff8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538912"
---
### <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Relançar para preservar detalhes da pilha

A regra do analisador de código .NET [CA2200](/visualstudio/code-quality/ca2200) está habilitada, por padrão, a partir do .NET 5,0. Ele produz um aviso de compilação para quaisquer `catch` blocos que relançam uma exceção e a exceção é explicitamente especificada na `throw` instrução.

#### <a name="change-description"></a>Descrição das alterações

A partir do .NET 5,0, o SDK do .NET inclui [analisadores de código-fonte .net](../../../../docs/fundamentals/productivity/code-analysis.md). Várias dessas regras estão habilitadas, por padrão, incluindo [CA2200](/visualstudio/code-quality/ca2200). Se o seu projeto contiver código que viole essa regra e estiver configurado para tratar avisos como erros, essa alteração poderá interromper sua compilação.

O código de sinalizadores CA2200 de regra em que as exceções são relançadas e a variável de exceção é especificada na `throw` instrução. Quando uma exceção é lançada, parte das informações que ela transporta é o rastreamento de pilha. O rastreamento de pilha é uma lista da hierarquia de chamada de método que começa com o método que gera a exceção e termina com o método que captura a exceção. Se uma exceção for relançada especificando a exceção na `throw` instrução, o rastreamento de pilha reiniciará no método atual e a lista de chamadas de método entre o método original que gerou a exceção e o método atual será perdido. Para manter as informações de rastreamento da pilha original com a exceção, use a `throw` instrução sem especificar a exceção.

O trecho de código a seguir não produz um aviso para a regra CA2200. No entanto, *a linha* comentada dispararia uma violação.

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

#### <a name="version-introduced"></a>Versão introduzida

RC1 5,0

#### <a name="recommended-action"></a>Ação recomendada

- Relançar exceções sem especificar a exceção explicitamente. Para obter mais informações, consulte [CA2200](/visualstudio/code-quality/ca2200).

- Para desabilitar completamente a análise de código, defina `EnableNETAnalyzers` como `false` em seu arquivo de projeto. Para obter mais informações, consulte [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Categoria

Análise de código

#### <a name="affected-apis"></a>APIs afetadas

Não detectável via análise de API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

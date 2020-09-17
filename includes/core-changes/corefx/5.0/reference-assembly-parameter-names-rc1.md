---
ms.openlocfilehash: 760c9ce2427bc1f5e9276e66ecb6d2cf2ed83c16
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738808"
---
### <a name="parameter-names-changed-in-rc1"></a>Nomes de parâmetros alterados no RC1

Alguns nomes de parâmetro de assembly de referência foram alterados para corresponder nomes de parâmetro nos assemblies de implementação.

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET 5,0 Preview e RC, alguns nomes de parâmetros de [assembly de referência](../../../../docs/standard/assembly/reference-assemblies.md) são diferentes para seus parâmetros correspondentes no assembly de implementação. Isso pode causar problemas ao usar argumentos nomeados e reflexão.

No .NET 5,0 RC2, esses nomes de parâmetro incompatíveis foram atualizados nos assemblies de referência para corresponder exatamente aos nomes de parâmetro correspondentes nos assemblies de implementação.

A tabela a seguir mostra as APIs e os nomes de parâmetro que foram alterados.

| API | Nome do parâmetro antigo | Nome do novo parâmetro |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

#### <a name="reason-for-change"></a>Motivo da alteração

Os nomes de parâmetro foram alterados quanto à consistência e para evitar falhas ao usar argumentos nomeados e reflexão.

#### <a name="version-introduced"></a>Versão introduzida

5,0 RC2

#### <a name="recommended-action"></a>Ação recomendada

Se você encontrar um erro de compilador devido a uma alteração de nome de parâmetro, atualize o nome do parâmetro de acordo.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->

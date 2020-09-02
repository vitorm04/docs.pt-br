---
ms.openlocfilehash: bba9659b92e5aabc276c585929c99898316036c5
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359123"
---
### <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a>Verificações IsSupported de hardware intrínsecas podem diferir para tipos aninhados

A verificação `<Isa>.X64.IsSupported` , em que `<Isa>` se refere às classes no <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> namespace, agora pode produzir um resultado diferente para versões anteriores do .net.

> [!TIP]
> O *ISA* significa arquitetura padrão do setor.

#### <a name="version-introduced"></a>Versão introduzida

5,0 Preview 8

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, alguns dos <xref:System.Runtime.Intrinsics.X86> tipos intrínsecos a hardware, por exemplo,, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> não expõevam uma `X64` classe aninhada. Para esses tipos, chamar `<Isa>.X64.IsSupported` resolvido para uma `IsSupported` propriedade em uma classe aninhada `X64` de uma classe pai de `<Isa>` . Isso significava que a propriedade poderia retornar `true` mesmo quando `<Isa>.IsSupported` retorna `false` .

No .NET 5,0 e versões posteriores, todos os <xref:System.Runtime.Intrinsics.X86> tipos expõem uma `X64` classe aninhada que relata adequadamente o suporte. Isso garante que a hierarquia geral permaneça correta e que `<Isa>.X64.IsSupported` , se for `true` , `<Isa>.IsSupported` também possa ser considerada `true` .

#### <a name="reason-for-change"></a>Motivo da alteração

A intenção era que `<Isa>.X64.IsSupported` , se estiver `true` , `<Isa>.IsSupported` também esteja implícita `true` . No entanto, devido à forma como a resolução de membros funciona em C#, as classes que não tinham uma classe aninhada apresentaram `X64` uma situação em que isso não era sempre o caso e levou a bugs no código do usuário.

#### <a name="recommended-action"></a>Ação recomendada

Se necessário, ajuste o código que verifica `IsSupported` para verificar o ISA apropriado.

#### <a name="category"></a>Categoria

Bibliotecas principais do .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->

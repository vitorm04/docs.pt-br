---
ms.openlocfilehash: a35439efce25db94e70420fc6aeaf04816525758
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263318"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Tipo de exceção do serializador `JsonException` JSON alterado de para`NotSupportedException`

No .NET Core 3,0 Preview 6 a 8, o serializador geraria <xref:System.Text.Json.JsonException> um quando ele encontrou um tipo de coleção derivada sem suporte. A partir do .NET Core 3,0 Preview 9, o serializador <xref:System.NotSupportedException> gera um em vez disso.

#### <a name="change-description"></a>Alterar descrição

No .NET Core 3,0 Preview 6 até a versão prévia 8, o serializador <xref:System.Text.Json.JsonException> geraria um quando ele encontrou um tipo de coleção derivada sem suporte. Um *tipo de coleção derivada sem suporte* é qualquer tipo de coleção que não seja atribuível a um dos seguintes tipos:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>`
- <xref:System.Collections.IDictionary>
- [Cadeia\<de caracteres IDictionary, T >](xref:System.Collections.Generic.IDictionary%602)

A partir do .NET Core 3,0 Preview 9, o serializador <xref:System.NotSupportedException> gera um ao encontrar um tipo de coleção sem suporte. O novo tipo de exceção melhor reflete por que a operação de desserialização está falhando.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Se você estiver <xref:System.Text.Json.JsonException> se deparando ao desserializar, convém considerar também <xref:System.NotSupportedException>a captura.

#### <a name="category"></a>Categoria

CoreFx

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->

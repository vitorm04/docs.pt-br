---
ms.openlocfilehash: 39d1b2dba8077bf9bf998775f8967d455f36b549
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119278"
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

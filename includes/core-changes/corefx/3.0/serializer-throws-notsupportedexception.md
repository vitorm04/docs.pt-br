---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568209"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>O tipo de exceção do serializador JSON foi alterado de `JsonException` para `NotSupportedException`

No .NET Core 3,0 Preview 6 a 8, o serializador lançaria um <xref:System.Text.Json.JsonException> quando ele encontrou um tipo de coleção derivada sem suporte. A partir do .NET Core 3,0 Preview 9, o serializador gera um <xref:System.NotSupportedException> em vez disso.

#### <a name="change-description"></a>Alterar descrição

No .NET Core 3,0 Preview 6 até a versão prévia 8, o serializador lançaria um <xref:System.Text.Json.JsonException> quando ele encontrou um tipo de coleção derivada sem suporte. Um *tipo de coleção derivada sem suporte* é qualquer tipo de coleção que não seja atribuível a um dos seguintes tipos:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [IDictionary\<cadeia de caracteres, T >](xref:System.Collections.Generic.IDictionary%602)

A partir do .NET Core 3,0 Preview 9, o serializador gera um <xref:System.NotSupportedException> ao encontrar um tipo de coleção sem suporte. O novo tipo de exceção melhor reflete por que a operação de desserialização está falhando.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 9

#### <a name="recommended-action"></a>Ação recomendada

Se estiver capturando <xref:System.Text.Json.JsonException> ao desserializar, talvez você queira considerar também a possibilidade de detectar <xref:System.NotSupportedException>.

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

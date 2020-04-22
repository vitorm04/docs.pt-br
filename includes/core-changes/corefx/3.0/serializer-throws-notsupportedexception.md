---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021662"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Tipo de exceção serializador Json mudou de `JsonException` para`NotSupportedException`

No .NET Core 3.0 Preview 6 a 8, o serializador lançaria um <xref:System.Text.Json.JsonException> quando encontrasse um tipo de coleção derivada sem suporte. Começando no .NET Core 3.0 Preview 9, o serializador lança um <xref:System.NotSupportedException> em vez disso.

#### <a name="change-description"></a>Descrição da alteração

No .NET Core 3.0 Preview 6 até a <xref:System.Text.Json.JsonException> Visualização 8, o serializador lançaria um quando encontrasse um tipo de coleção derivada sem suporte. Um *tipo de coleção derivado sem suporte* é qualquer tipo de coleção que não seja atribuído a um dos seguintes tipos:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [String\<iDictionary,T>](xref:System.Collections.Generic.IDictionary%602)

Começando com .NET Core 3.0 Preview 9, o serializador lança um <xref:System.NotSupportedException> ao encontrar um tipo de coleção sem suporte. O novo tipo de exceção reflete melhor por que a operação de desserialização está falhando.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 9

#### <a name="recommended-action"></a>Ação recomendada

Se você está <xref:System.Text.Json.JsonException> pegando ao desserializar, você <xref:System.NotSupportedException>pode querer considerar também pegar .

#### <a name="category"></a>Categoria

Bibliotecas Core .NET

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->

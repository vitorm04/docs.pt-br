---
ms.openlocfilehash: 572ebc47d26e30738fc4e5b8a8fab1f2643e3d83
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997726"
---
### <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a>Construtores não públicos sem parâmetros não usados para desserialização

Para consistência em todos os monikers de estrutura de destino com suporte (TFMs), não públicos, construtores sem parâmetros não são mais usados para desserialização com <xref:System.Text.Json.JsonSerializer> , por padrão.

#### <a name="change-description"></a>Descrição das alterações

No .NET Core 3,0 e 3,1, construtores internos e privados podem ser usados para desserialização. Em .NET Standard 2,0 e 2,1, construtores internos e privados não são permitidos e um <xref:System.MissingMethodException> será gerado se nenhum construtor público sem parâmetros for definido.

A partir do .NET 5,0, os construtores não públicos, incluindo construtores sem parâmetros, são ignorados pelo serializador por padrão. O serializador usa um dos seguintes construtores para desserialização:

- Construtor público anotado com <xref:System.Text.Json.Serialization.JsonConstructorAttribute> .
- Construtor público sem parâmetros.
- Construtor com parâmetros públicos (se for o único construtor público presente).

Se nenhum desses construtores estiver disponível, um <xref:System.NotSupportedException> será gerado se você tentar desserializar o tipo.

#### <a name="version-introduced"></a>Versão introduzida

5.0

#### <a name="reason-for-change"></a>Motivo da alteração

- Para impor um comportamento consistente entre todos os TFMs (monikers de estrutura de destino) que se <xref:System.Text.Json?displayProperty=fullName> baseiam para o (.NET Core 3,0 e versões posteriores e .NET Standard 2,0 e 2,1)
- Porque <xref:System.Text.Json.JsonSerializer> não deve chamar a área da superfície não pública de um tipo, seja um construtor, uma propriedade ou um campo.

#### <a name="recommended-action"></a>Ação recomendada

- Se você possui o tipo e é viável, torne o construtor sem parâmetros público.
- Caso contrário, implemente um `JsonConverter<T>` para o tipo e controle o comportamento de desserialização.

#### <a name="category"></a>Categoria

Serialização

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->

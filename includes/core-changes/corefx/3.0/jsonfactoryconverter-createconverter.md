---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568163"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Assinatura de JsonFactoryConverter. Createconverter alterada

Para facilitar a composição de classes de <xref:System.Text.Json.Serialization.JsonConverterFactory>, o método <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> foi tornado público e recebeu um segundo argumento do tipo <xref:System.Text.Json.JsonSerializerOptions>.

#### <a name="change-description"></a>Alterar descrição

A assinatura do método `CreateConverter` no .NET Core anterior à versão 3,0 Preview 8 foi:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

No .NET Core 3,0 Preview 8 e versões posteriores, é:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Antes dessa alteração, era difícil compor conversores de fábrica lacrados, já que não havia uma maneira fácil de obter o <xref:System.Text.Json.Serialization.JsonConverter%601> dele. Tornar o método de fábrica público e também passar o <xref:System.Text.Json.JsonSerializerOptions> atual permite uma composição muito mais flexível.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 8

#### <a name="recommended-action"></a>Ação recomendada

As classes derivadas precisam ser atualizadas e recompiladas.

#### <a name="affected-apis"></a>APIs afetadas

<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->

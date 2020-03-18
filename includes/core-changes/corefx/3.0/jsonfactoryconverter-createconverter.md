---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147556"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>JsonFactoryConverter.CreateConverter assinatura alterada

Para facilitar a <xref:System.Text.Json.Serialization.JsonConverterFactory> composição <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> das classes, o método foi tornado <xref:System.Text.Json.JsonSerializerOptions>público e recebeu um segundo argumento de tipo .

#### <a name="change-description"></a>Descrição da alteração

A assinatura `CreateConverter` do método no .NET Core antes da versão 3.0 Preview 8 foi:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

Em .NET Core 3.0 Preview 8 e versões posteriores, é:

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

Antes dessa mudança, era difícil compor conversores de fábrica selados, já que não havia uma maneira fácil de obter a <xref:System.Text.Json.Serialization.JsonConverter%601> partir dele. Tornar o método de fábrica <xref:System.Text.Json.JsonSerializerOptions> público e também passar a corrente permitem uma composição muito mais flexível.

#### <a name="version-introduced"></a>Versão introduzida

3.0 Visualização 8

#### <a name="recommended-action"></a>Ação recomendada

As classes derivadas precisam ser atualizadas e recompiladas.

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->

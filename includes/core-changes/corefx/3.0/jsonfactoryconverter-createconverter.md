---
ms.openlocfilehash: 43da6233b70927e7320874772976b9e93a0bd69f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721515"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Assinatura de JsonFactoryConverter. Createconverter alterada

Para facilitar a composição de <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, o <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> método foi tornado público e recebeu um segundo argumento do tipo <xref:System.Text.Json.JsonSerializerOptions> .

#### <a name="change-description"></a>Descrição da alteração

A assinatura do `CreateConverter` método no .NET Core anterior à versão 3,0 Preview 8 foi:

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

Antes dessa alteração, era difícil compor conversores de fábrica lacrados, já que não havia uma maneira fácil de obtê <xref:System.Text.Json.Serialization.JsonConverter%601> -lo. Tornando o método de fábrica público e também passando a <xref:System.Text.Json.JsonSerializerOptions> permissão atual para uma composição muito mais flexível.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 8

#### <a name="recommended-action"></a>Ação recomendada

As classes derivadas precisam ser atualizadas e recompiladas.

#### <a name="affected-apis"></a>APIs afetadas

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

#### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->

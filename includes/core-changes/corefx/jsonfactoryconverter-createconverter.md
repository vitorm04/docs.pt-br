---
ms.openlocfilehash: f5b0064f9f01923c6353fd8e2b274bd7407ccbd8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237282"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a>Assinatura de JsonFactoryConverter. Createconverter alterada

Para facilitar a composição de classes <xref:System.Text.Json.Serialization.JsonConverterFactory>, o método <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> foi tornado público e recebeu um segundo argumento do tipo <xref:System.Text.Json.JsonSerializerOptions>.

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

Antes dessa alteração, era difícil compor conversores de fábrica lacrados, já que não havia uma maneira fácil de obter o <xref:System.Text.Json.Serialization.JsonConverter%601> a partir dele. Tornar o método de fábrica público e também passar o <xref:System.Text.Json.JsonSerializerOptions> atual permite uma composição muito mais flexível.

#### <a name="version-introduced"></a>Versão introduzida

3,0 Preview 8

#### <a name="recommended-action"></a>Ação recomendada

As classes derivadas precisam ser atualizadas e recompiladas.

#### <a name="affected-apis"></a>APIs afetadas

[https://aka.ms/AzureNVblog](<xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>).

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->

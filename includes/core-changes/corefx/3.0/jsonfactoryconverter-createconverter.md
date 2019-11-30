---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568163"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="6886a-101">Assinatura de JsonFactoryConverter. Createconverter alterada</span><span class="sxs-lookup"><span data-stu-id="6886a-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="6886a-102">Para facilitar a composição de classes de <xref:System.Text.Json.Serialization.JsonConverterFactory>, o método <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> foi tornado público e recebeu um segundo argumento do tipo <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="6886a-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6886a-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="6886a-103">Change description</span></span>

<span data-ttu-id="6886a-104">A assinatura do método `CreateConverter` no .NET Core anterior à versão 3,0 Preview 8 foi:</span><span class="sxs-lookup"><span data-stu-id="6886a-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="6886a-105">No .NET Core 3,0 Preview 8 e versões posteriores, é:</span><span class="sxs-lookup"><span data-stu-id="6886a-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="6886a-106">Antes dessa alteração, era difícil compor conversores de fábrica lacrados, já que não havia uma maneira fácil de obter o <xref:System.Text.Json.Serialization.JsonConverter%601> dele.</span><span class="sxs-lookup"><span data-stu-id="6886a-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="6886a-107">Tornar o método de fábrica público e também passar o <xref:System.Text.Json.JsonSerializerOptions> atual permite uma composição muito mais flexível.</span><span class="sxs-lookup"><span data-stu-id="6886a-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6886a-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="6886a-108">Version introduced</span></span>

<span data-ttu-id="6886a-109">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="6886a-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6886a-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="6886a-110">Recommended action</span></span>

<span data-ttu-id="6886a-111">As classes derivadas precisam ser atualizadas e recompiladas.</span><span class="sxs-lookup"><span data-stu-id="6886a-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6886a-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6886a-112">Affected APIs</span></span>

<span data-ttu-id="6886a-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6886a-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->

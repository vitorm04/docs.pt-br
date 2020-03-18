---
ms.openlocfilehash: 3bce796191e0ebe6dbe4650457abe5a20c383f02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147556"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="75a47-101">JsonFactoryConverter.CreateConverter assinatura alterada</span><span class="sxs-lookup"><span data-stu-id="75a47-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="75a47-102">Para facilitar a <xref:System.Text.Json.Serialization.JsonConverterFactory> composição <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> das classes, o método foi tornado <xref:System.Text.Json.JsonSerializerOptions>público e recebeu um segundo argumento de tipo .</span><span class="sxs-lookup"><span data-stu-id="75a47-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="75a47-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="75a47-103">Change description</span></span>

<span data-ttu-id="75a47-104">A assinatura `CreateConverter` do método no .NET Core antes da versão 3.0 Preview 8 foi:</span><span class="sxs-lookup"><span data-stu-id="75a47-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="75a47-105">Em .NET Core 3.0 Preview 8 e versões posteriores, é:</span><span class="sxs-lookup"><span data-stu-id="75a47-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="75a47-106">Antes dessa mudança, era difícil compor conversores de fábrica selados, já que não havia uma maneira fácil de obter a <xref:System.Text.Json.Serialization.JsonConverter%601> partir dele.</span><span class="sxs-lookup"><span data-stu-id="75a47-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="75a47-107">Tornar o método de fábrica <xref:System.Text.Json.JsonSerializerOptions> público e também passar a corrente permitem uma composição muito mais flexível.</span><span class="sxs-lookup"><span data-stu-id="75a47-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="75a47-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="75a47-108">Version introduced</span></span>

<span data-ttu-id="75a47-109">3.0 Visualização 8</span><span class="sxs-lookup"><span data-stu-id="75a47-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="75a47-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="75a47-110">Recommended action</span></span>

<span data-ttu-id="75a47-111">As classes derivadas precisam ser atualizadas e recompiladas.</span><span class="sxs-lookup"><span data-stu-id="75a47-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="75a47-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="75a47-112">Affected APIs</span></span>

- <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->

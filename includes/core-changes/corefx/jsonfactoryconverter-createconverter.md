---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117136"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="ac224-101">Assinatura de JsonFactoryConverter. Createconverter alterada</span><span class="sxs-lookup"><span data-stu-id="ac224-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="ac224-102">Para facilitar a composição de <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, o <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> método foi tornado público e recebeu um segundo argumento do tipo <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="ac224-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="details"></a><span data-ttu-id="ac224-103">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ac224-103">Details</span></span>

<span data-ttu-id="ac224-104">A assinatura do `CreateConverter` método no .NET Core anterior à versão 3,0 Preview 8 foi:</span><span class="sxs-lookup"><span data-stu-id="ac224-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span> 

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="ac224-105">No .NET Core 3,0 Preview 8 e versões posteriores, é:</span><span class="sxs-lookup"><span data-stu-id="ac224-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="ac224-106">Antes dessa alteração, era difícil compor conversores <xref:System.Text.Json.Serialization.JsonConverter%601> de fábrica lacrados, já que não havia uma maneira fácil de obtê-lo.</span><span class="sxs-lookup"><span data-stu-id="ac224-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="ac224-107">Tornando o método de fábrica público e também passando a <xref:System.Text.Json.JsonSerializerOptions> permissão atual para uma composição muito mais flexível.</span><span class="sxs-lookup"><span data-stu-id="ac224-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ac224-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ac224-108">Version introduced</span></span>

<span data-ttu-id="ac224-109">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="ac224-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ac224-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ac224-110">Recommended action</span></span>

<span data-ttu-id="ac224-111">As classes derivadas precisam ser atualizadas e recompiladas.</span><span class="sxs-lookup"><span data-stu-id="ac224-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ac224-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ac224-112">Affected APIs</span></span>

<span data-ttu-id="ac224-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac224-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->

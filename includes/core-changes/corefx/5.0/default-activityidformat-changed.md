---
ms.openlocfilehash: d75dc2caa3a002b9d34ac74f2c5c5e192281c0df
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281284"
---
### <a name="default-activityidformat-is-w3c"></a><span data-ttu-id="fc06a-101">O ActivityIdFormat padrão é W3C</span><span class="sxs-lookup"><span data-stu-id="fc06a-101">Default ActivityIdFormat is W3C</span></span>

<span data-ttu-id="fc06a-102">O formato de identificador padrão para atividade ( <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> ) agora é <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fc06a-102">The default identifier format for activity (<xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType>) is now <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fc06a-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="fc06a-103">Change description</span></span>

<span data-ttu-id="fc06a-104">O formato da ID da atividade W3C foi introduzido no .NET Core 3,0 como uma alternativa ao formato de ID hierárquica.</span><span class="sxs-lookup"><span data-stu-id="fc06a-104">The W3C activity ID format was introduced in .NET Core 3.0 as an alternative to the hierarchical ID format.</span></span> <span data-ttu-id="fc06a-105">No entanto, para preservar a compatibilidade, o formato W3C não foi tornado o padrão até o .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="fc06a-105">However, to preserve compatibility, the W3C format wasn't made the default until .NET 5.0.</span></span> <span data-ttu-id="fc06a-106">O padrão foi alterado no .NET 5,0 porque o [formato W3C foi ratificado](https://www.w3.org/TR/trace-context/) e ganhou força em várias implementações de idioma.</span><span class="sxs-lookup"><span data-stu-id="fc06a-106">The default was changed in .NET 5.0 because the [W3C format has been ratified](https://www.w3.org/TR/trace-context/) and gained traction across multiple language implementations.</span></span>

<span data-ttu-id="fc06a-107">Se seu aplicativo for destinado a uma plataforma diferente do .NET 5,0 ou posterior, ele passará pelo comportamento antigo, em que <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> é o formato padrão.</span><span class="sxs-lookup"><span data-stu-id="fc06a-107">If your app targets a platform other than .NET 5.0 or later, it will experience the old behavior, where <xref:System.Diagnostics.ActivityIdFormat.Hierarchical> is the default format.</span></span> <span data-ttu-id="fc06a-108">Esse padrão se aplica às plataformas Net45 +, netstandard 1.1 + e netcoreapp (1. x, 2. x e 3. x).</span><span class="sxs-lookup"><span data-stu-id="fc06a-108">This default applies to platforms net45+, netstandard1.1+, and netcoreapp (1.x, 2.x, and 3.x).</span></span> <span data-ttu-id="fc06a-109">No .NET 5,0 e posterior, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> é definido como <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fc06a-109">In .NET 5.0 and later, <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=nameWithType> is set to <xref:System.Diagnostics.ActivityIdFormat.W3C?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fc06a-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fc06a-110">Version introduced</span></span>

<span data-ttu-id="fc06a-111">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="fc06a-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fc06a-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fc06a-112">Recommended action</span></span>

<span data-ttu-id="fc06a-113">Se seu aplicativo for independente do identificador usado para o rastreamento distribuído, nenhuma ação será necessária.</span><span class="sxs-lookup"><span data-stu-id="fc06a-113">If your application is agnostic to the identifier that's used for distributed tracing, no action is needed.</span></span> <span data-ttu-id="fc06a-114">Bibliotecas como ASP.NET Core e <xref:System.Net.Http.HttpClient> podem consumir ou propagar ambas as versões do <xref:System.Diagnostics.ActivityIdFormat> .</span><span class="sxs-lookup"><span data-stu-id="fc06a-114">Libraries such as ASP.NET Core and <xref:System.Net.Http.HttpClient> can consume or propagate both versions of the <xref:System.Diagnostics.ActivityIdFormat>.</span></span>

<span data-ttu-id="fc06a-115">Se você precisar de interoperabilidade com sistemas existentes ou se os sistemas atuais dependem do formato do identificador, você pode preservar o comportamento antigo definindo <xref:System.Diagnostics.Activity.DefaultIdFormat> como <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fc06a-115">If you require interoperability with existing systems, or current systems rely on the format of the identifier, you can preserve the old behavior by setting <xref:System.Diagnostics.Activity.DefaultIdFormat> to <xref:System.Diagnostics.ActivityIdFormat.Hierarchical?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fc06a-116">Como alternativa, você pode definir uma opção AppContext de uma das três maneiras:</span><span class="sxs-lookup"><span data-stu-id="fc06a-116">Alternatively, you can set an AppContext switch in one of three ways:</span></span>

- <span data-ttu-id="fc06a-117">No arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="fc06a-117">In the project file.</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Diagnostics.DefaultActivityIdFormatIsHierarchial" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="fc06a-118">Na *runtimeconfig.jsno* arquivo.</span><span class="sxs-lookup"><span data-stu-id="fc06a-118">In the *runtimeconfig.json* file.</span></span>

  ```json
  {
      "runtimeOptions": {
          "configProperties": {
              "System.Diagnostics.DefaultActivityIdFormatIsHierarchial": true
          }
      }
  }
  ```

- <span data-ttu-id="fc06a-119">Por meio de uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="fc06a-119">Through an environment variable.</span></span>

  <span data-ttu-id="fc06a-120">Defina `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` como `true` ou 1.</span><span class="sxs-lookup"><span data-stu-id="fc06a-120">Set `DOTNET_SYSTEM_DIAGNOSTICS_DEFAULTACTIVITYIDFORMATISHIERARCHIAL` to `true` or 1.</span></span>

#### <a name="category"></a><span data-ttu-id="fc06a-121">Categoria</span><span class="sxs-lookup"><span data-stu-id="fc06a-121">Category</span></span>

<span data-ttu-id="fc06a-122">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="fc06a-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fc06a-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fc06a-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.DefaultIdFormat?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.DefaultIdFormat`

-->

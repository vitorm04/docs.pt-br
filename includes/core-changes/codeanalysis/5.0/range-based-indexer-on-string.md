---
ms.openlocfilehash: 4e937f56f6315ce2abf76dd56989f4d2c4059f22
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598056"
---
### <a name="ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a><span data-ttu-id="04284-101">CA1831: usar asspan em vez de indexadores baseados em intervalo para cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="04284-101">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>

<span data-ttu-id="04284-102">A regra do analisador de código .NET [CA1831](/visualstudio/code-quality/ca1831) está habilitada, por padrão, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="04284-102">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="04284-103">Ele produz um aviso de compilação para qualquer código em que um <xref:System.Range> indexador baseado em um é usado em uma cadeia de caracteres, mas nenhuma cópia foi pretendida.</span><span class="sxs-lookup"><span data-stu-id="04284-103">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

#### <a name="change-description"></a><span data-ttu-id="04284-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="04284-104">Change description</span></span>

<span data-ttu-id="04284-105">A partir do .NET 5,0, o SDK do .NET inclui [analisadores de código-fonte .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="04284-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="04284-106">Várias dessas regras estão habilitadas, por padrão, incluindo [CA1831](/visualstudio/code-quality/ca1831).</span><span class="sxs-lookup"><span data-stu-id="04284-106">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="04284-107">Se o seu projeto contiver código que viole essa regra e estiver configurado para tratar avisos como erros, essa alteração poderá interromper sua compilação.</span><span class="sxs-lookup"><span data-stu-id="04284-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="04284-108">A regra CA1831 localiza instâncias em que o <xref:System.Range> indexador baseado em um é usado em uma cadeia de caracteres, mas nenhuma cópia foi pretendida.</span><span class="sxs-lookup"><span data-stu-id="04284-108">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="04284-109">Se o <xref:System.Range> indexador baseado for usado diretamente em uma cadeia de caracteres para produzir uma conversão implícita, uma cópia desnecessária da parte solicitada da cadeia de caracteres será criada.</span><span class="sxs-lookup"><span data-stu-id="04284-109">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="04284-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="04284-110">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="04284-111">O CA1831 sugere o uso do <xref:System.Range> indexador baseado em um *intervalo* da cadeia de caracteres, em vez disso.</span><span class="sxs-lookup"><span data-stu-id="04284-111">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="04284-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="04284-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

#### <a name="version-introduced"></a><span data-ttu-id="04284-113">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="04284-113">Version introduced</span></span>

<span data-ttu-id="04284-114">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="04284-114">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="04284-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="04284-115">Recommended action</span></span>

- <span data-ttu-id="04284-116">Para corrigir seu código e evitar alocações desnecessárias, chame <xref:System.MemoryExtensions.AsSpan(System.String)> ou <xref:System.MemoryExtensions.AsMemory(System.String)> antes de usar o <xref:System.Range> indexador baseado em.</span><span class="sxs-lookup"><span data-stu-id="04284-116">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="04284-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="04284-117">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="04284-118">Se você não quiser alterar seu código, poderá desabilitar a regra definindo sua severidade como `suggestion` ou `none` .</span><span class="sxs-lookup"><span data-stu-id="04284-118">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="04284-119">Para obter mais informações, consulte [configurar regras de análise de código](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span><span class="sxs-lookup"><span data-stu-id="04284-119">For more information, see [Configure code analysis rules](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span></span>

- <span data-ttu-id="04284-120">Para desabilitar completamente a análise de código, defina `EnableNETAnalyzers` como `false` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="04284-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="04284-121">Para obter mais informações, consulte [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="04284-121">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="04284-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="04284-122">Category</span></span>

<span data-ttu-id="04284-123">Análise de código</span><span class="sxs-lookup"><span data-stu-id="04284-123">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="04284-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="04284-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Range`

-->

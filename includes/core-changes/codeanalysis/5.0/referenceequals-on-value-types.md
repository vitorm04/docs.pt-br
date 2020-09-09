---
ms.openlocfilehash: b01424c63d6e7956127bf889c53422b60ba2f219
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598047"
---
### <a name="ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="87cdb-101">CA2013: Não usar ReferenceEquals com tipos de valor</span><span class="sxs-lookup"><span data-stu-id="87cdb-101">CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="87cdb-102">A regra do analisador de código .NET [CA2013](/visualstudio/code-quality/ca2013) está habilitada, por padrão, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="87cdb-102">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="87cdb-103">Ele produz um aviso de compilação para qualquer código em que <xref:System.Object.ReferenceEquals(System.Object,System.Object)> é usado para comparar um ou mais tipos de valor para igualdade.</span><span class="sxs-lookup"><span data-stu-id="87cdb-103">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

#### <a name="change-description"></a><span data-ttu-id="87cdb-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="87cdb-104">Change description</span></span>

<span data-ttu-id="87cdb-105">A partir do .NET 5,0, o SDK do .NET inclui [analisadores de código-fonte .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="87cdb-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="87cdb-106">Várias dessas regras estão habilitadas, por padrão, incluindo [CA2013](/visualstudio/code-quality/ca2013).</span><span class="sxs-lookup"><span data-stu-id="87cdb-106">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="87cdb-107">Se o seu projeto contiver código que viole essa regra e estiver configurado para tratar avisos como erros, essa alteração poderá interromper sua compilação.</span><span class="sxs-lookup"><span data-stu-id="87cdb-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="87cdb-108">A regra CA2013 localiza instâncias em que <xref:System.Object.ReferenceEquals(System.Object,System.Object)> é usada para comparar um ou mais tipos de valor para igualdade.</span><span class="sxs-lookup"><span data-stu-id="87cdb-108">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="87cdb-109">Comparar tipos de valor para igualdade dessa maneira pode levar a resultados incorretos, porque os valores estão em caixa antes que eles sejam comparados.</span><span class="sxs-lookup"><span data-stu-id="87cdb-109">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="87cdb-110"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> retornará `false` mesmo se os valores comparados representarem a mesma instância de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="87cdb-110"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="87cdb-111">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="87cdb-111">Version introduced</span></span>

<span data-ttu-id="87cdb-112">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="87cdb-112">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="87cdb-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="87cdb-113">Recommended action</span></span>

- <span data-ttu-id="87cdb-114">Altere o código para usar um operador de igualdade apropriado, como `==` .</span><span class="sxs-lookup"><span data-stu-id="87cdb-114">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="87cdb-115">Você não deve suprimir este aviso.</span><span class="sxs-lookup"><span data-stu-id="87cdb-115">You should not suppress this warning.</span></span>

- <span data-ttu-id="87cdb-116">Para desabilitar completamente a análise de código, defina `EnableNETAnalyzers` como `false` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="87cdb-116">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="87cdb-117">Para obter mais informações, consulte [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="87cdb-117">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="87cdb-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="87cdb-118">Category</span></span>

<span data-ttu-id="87cdb-119">Análise de código</span><span class="sxs-lookup"><span data-stu-id="87cdb-119">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="87cdb-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="87cdb-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

-->

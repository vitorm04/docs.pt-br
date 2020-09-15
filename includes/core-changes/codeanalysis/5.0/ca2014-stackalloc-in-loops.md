---
ms.openlocfilehash: a51160a8ab5a4b437e51db31def577f8d8f50182
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065119"
---
### <a name="ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="af349-101">CA2014: Não usar stackalloc em loops</span><span class="sxs-lookup"><span data-stu-id="af349-101">CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="af349-102">A regra do analisador de código .NET [CA2014](/visualstudio/code-quality/ca2014) está habilitada, por padrão, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="af349-102">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="af349-103">Ele produz um aviso de compilação para qualquer código C# em que uma expressão [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) é usada dentro de um loop.</span><span class="sxs-lookup"><span data-stu-id="af349-103">It produces a build warning for any C# code where a [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

#### <a name="change-description"></a><span data-ttu-id="af349-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="af349-104">Change description</span></span>

<span data-ttu-id="af349-105">A partir do .NET 5,0, o SDK do .NET inclui [analisadores de código-fonte .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="af349-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="af349-106">Várias dessas regras estão habilitadas, por padrão, incluindo [CA2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="af349-106">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="af349-107">Se o seu projeto contiver código que viole essa regra e estiver configurado para tratar avisos como erros, essa alteração poderá interromper sua compilação.</span><span class="sxs-lookup"><span data-stu-id="af349-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="af349-108">A regra CA2014 procura código C# em que uma [expressão stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) é usada dentro de um loop.</span><span class="sxs-lookup"><span data-stu-id="af349-108">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../docs/csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="af349-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) aloca memória a partir do quadro de pilhas atual.</span><span class="sxs-lookup"><span data-stu-id="af349-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="af349-110">A memória não é liberada até que a chamada de método atual seja retornada, o que pode levar a estouros de pilha.</span><span class="sxs-lookup"><span data-stu-id="af349-110">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="af349-111">Como não é possível capturar exceções de estouro de pilha, o aplicativo será encerrado em caso de estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="af349-111">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="af349-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="af349-112">Version introduced</span></span>

<span data-ttu-id="af349-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="af349-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="af349-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="af349-114">Recommended action</span></span>

- <span data-ttu-id="af349-115">Evite usar loops [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="af349-115">Avoid using [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="af349-116">Aloque o bloco de memória fora do loop e reutilize-o dentro do loop.</span><span class="sxs-lookup"><span data-stu-id="af349-116">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="af349-117">Para obter mais informações, consulte [CA2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="af349-117">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="af349-118">Para desabilitar completamente a análise de código, defina `EnableNETAnalyzers` como `false` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="af349-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="af349-119">Para obter mais informações, consulte [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="af349-119">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="af349-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="af349-120">Category</span></span>

<span data-ttu-id="af349-121">Análise de código</span><span class="sxs-lookup"><span data-stu-id="af349-121">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="af349-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="af349-122">Affected APIs</span></span>

<span data-ttu-id="af349-123">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="af349-123">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

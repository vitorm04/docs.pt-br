---
ms.openlocfilehash: 6bb3b11ef4e4cb6f6a039c97911b0acca862fe6f
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465555"
---
### <a name="ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a><span data-ttu-id="ec89f-101">CA2247: o argumento para o Construtor TaskCompletionSource deve ser um valor TaskCreationOptions</span><span class="sxs-lookup"><span data-stu-id="ec89f-101">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>

<span data-ttu-id="ec89f-102">A regra do analisador de código .NET [CA2247](/visualstudio/code-quality/ca2247) está habilitada, por padrão, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="ec89f-102">.NET code analyzer rule [CA2247](/visualstudio/code-quality/ca2247) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="ec89f-103">Ele produz um aviso de compilação para chamadas para o <xref:System.Threading.Tasks.TaskCompletionSource%601> Construtor que passa um argumento do tipo <xref:System.Threading.Tasks.TaskContinuationOptions> .</span><span class="sxs-lookup"><span data-stu-id="ec89f-103">It produces a build warning for calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ec89f-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="ec89f-104">Change description</span></span>

<span data-ttu-id="ec89f-105">A partir do .NET 5,0, o SDK do .NET inclui [analisadores de código-fonte .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="ec89f-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="ec89f-106">Várias dessas regras estão habilitadas, por padrão, incluindo [CA2247](/visualstudio/code-quality/ca2247).</span><span class="sxs-lookup"><span data-stu-id="ec89f-106">Several of these rules are enabled, by default, including [CA2247](/visualstudio/code-quality/ca2247).</span></span> <span data-ttu-id="ec89f-107">Se o seu projeto contiver código que viole essa regra e estiver configurado para tratar avisos como erros, essa alteração poderá interromper sua compilação.</span><span class="sxs-lookup"><span data-stu-id="ec89f-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="ec89f-108">A regra CA2247 localiza chamadas para o <xref:System.Threading.Tasks.TaskCompletionSource%601> Construtor que passa um argumento do tipo <xref:System.Threading.Tasks.TaskContinuationOptions> .</span><span class="sxs-lookup"><span data-stu-id="ec89f-108">Rule CA2247 finds calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span> <span data-ttu-id="ec89f-109">O <xref:System.Threading.Tasks.TaskCompletionSource%601> tipo tem um construtor que aceita um <xref:System.Threading.Tasks.TaskCreationOptions> valor e outro construtor que aceita um <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="ec89f-109">The <xref:System.Threading.Tasks.TaskCompletionSource%601> type has a constructor that accepts a <xref:System.Threading.Tasks.TaskCreationOptions> value, and another constructor that accepts an <xref:System.Object>.</span></span> <span data-ttu-id="ec89f-110">Se você passar acidentalmente um <xref:System.Threading.Tasks.TaskContinuationOptions> valor em vez de um <xref:System.Threading.Tasks.TaskCreationOptions> valor, o construtor com o <xref:System.Object> parâmetro será chamado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ec89f-110">If you accidentally pass a <xref:System.Threading.Tasks.TaskContinuationOptions> value instead of a <xref:System.Threading.Tasks.TaskCreationOptions> value, the constructor with the <xref:System.Object> parameter is called at run time.</span></span> <span data-ttu-id="ec89f-111">Seu código será compilado e executado, mas não terá o comportamento pretendido.</span><span class="sxs-lookup"><span data-stu-id="ec89f-111">Your code will compile and run but won't have the intended behavior.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ec89f-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ec89f-112">Version introduced</span></span>

<span data-ttu-id="ec89f-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="ec89f-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ec89f-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ec89f-114">Recommended action</span></span>

- <span data-ttu-id="ec89f-115">Substitua o <xref:System.Threading.Tasks.TaskContinuationOptions> argumento pelo valor correspondente <xref:System.Threading.Tasks.TaskCreationOptions> .</span><span class="sxs-lookup"><span data-stu-id="ec89f-115">Replace the <xref:System.Threading.Tasks.TaskContinuationOptions> argument with the corresponding <xref:System.Threading.Tasks.TaskCreationOptions> value.</span></span> <span data-ttu-id="ec89f-116">Não suprimir este aviso, pois quase sempre realça um bug em seu código.</span><span class="sxs-lookup"><span data-stu-id="ec89f-116">Do not suppress this warning, since it almost always highlights a bug in your code.</span></span> <span data-ttu-id="ec89f-117">Para obter mais informações, consulte [CA2247](/visualstudio/code-quality/ca2247).</span><span class="sxs-lookup"><span data-stu-id="ec89f-117">For more information, see [CA2247](/visualstudio/code-quality/ca2247).</span></span>

- <span data-ttu-id="ec89f-118">Para desabilitar completamente a análise de código, defina `EnableNETAnalyzers` como `false` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ec89f-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="ec89f-119">Para obter mais informações, consulte [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="ec89f-119">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="ec89f-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="ec89f-120">Category</span></span>

<span data-ttu-id="ec89f-121">Análise de código</span><span class="sxs-lookup"><span data-stu-id="ec89f-121">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ec89f-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ec89f-122">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

#### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

-->

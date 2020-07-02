---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614275"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a><span data-ttu-id="96d23-101">Fluxo CurrentCulture e CurrentUICulture atravessam tarefas</span><span class="sxs-lookup"><span data-stu-id="96d23-101">CurrentCulture and CurrentUICulture flow across tasks</span></span>

#### <a name="details"></a><span data-ttu-id="96d23-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="96d23-102">Details</span></span>

<span data-ttu-id="96d23-103">A partir do .NET Framework 4.6, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> são armazenados no <xref:System.Threading.ExecutionContext?displayProperty=fullName> do thread, que atravessa operações assíncronas. Isso significa que as alterações em <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> serão refletidas em tarefas que posteriormente serão executadas de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="96d23-103">Beginning in the .NET Framework 4.6, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> are stored in the thread's <xref:System.Threading.ExecutionContext?displayProperty=fullName>, which flows across asynchronous operations.This means that changes to <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> will be reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="96d23-104">Isso é diferente do comportamento das versões anteriores do .NET Framework (que redefiniria <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> e <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> em todas as tarefas assíncronas).</span><span class="sxs-lookup"><span data-stu-id="96d23-104">This is different from the behavior of previous .NET Framework versions (which would reset <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> in all asynchronous tasks).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="96d23-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="96d23-105">Suggestion</span></span>

<span data-ttu-id="96d23-106">Aplicativos afetados por essa alteração podem contorná-la definindo explicitamente o <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> desejado como a primeira operação em uma Tarefa assíncrona.</span><span class="sxs-lookup"><span data-stu-id="96d23-106">Apps affected by this change may work around it by explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> as the first operation in an async Task.</span></span> <span data-ttu-id="96d23-107">Como alternativa, o comportamento antigo (de não atravessar <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) pode ser aceito definindo a seguinte opção de compatibilidade:</span><span class="sxs-lookup"><span data-stu-id="96d23-107">Alternatively, the old behavior (of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) may be opted into by setting the following compatibility switch:</span></span>

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

<span data-ttu-id="96d23-108">Esse problema foi corrigido pelo WPF no .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="96d23-108">This issue has been fixed by WPF in .NET Framework 4.6.2.</span></span> <span data-ttu-id="96d23-109">Ele também foi corrigido no .NET Framework 4.6 e 4.6.1 por meio de [KB 3139549](https://support.microsoft.com/kb/3139549).</span><span class="sxs-lookup"><span data-stu-id="96d23-109">It has also been fixed in .NET Frameworks 4.6, 4.6.1 through [KB 3139549](https://support.microsoft.com/kb/3139549).</span></span> <span data-ttu-id="96d23-110">Os aplicativos direcionados ao .NET Framework 4.6 ou posterior terão o comportamento correto automaticamente nos aplicativos WPF – <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>. Isso seria preservado entre as operações de Dispatcher.</span><span class="sxs-lookup"><span data-stu-id="96d23-110">Applications targeting .NET Framework 4.6 or later will automatically get the right behavior in WPF applications - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) would be preserved across Dispatcher operations.</span></span>

| <span data-ttu-id="96d23-111">Name</span><span class="sxs-lookup"><span data-stu-id="96d23-111">Name</span></span>    | <span data-ttu-id="96d23-112">Valor</span><span class="sxs-lookup"><span data-stu-id="96d23-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="96d23-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="96d23-113">Scope</span></span>   | <span data-ttu-id="96d23-114">Secundária</span><span class="sxs-lookup"><span data-stu-id="96d23-114">Minor</span></span>       |
| <span data-ttu-id="96d23-115">Versão</span><span class="sxs-lookup"><span data-stu-id="96d23-115">Version</span></span> | <span data-ttu-id="96d23-116">4.6</span><span class="sxs-lookup"><span data-stu-id="96d23-116">4.6</span></span>         |
| <span data-ttu-id="96d23-117">Type</span><span class="sxs-lookup"><span data-stu-id="96d23-117">Type</span></span>    | <span data-ttu-id="96d23-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="96d23-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="96d23-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="96d23-119">Affected APIs</span></span>

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>

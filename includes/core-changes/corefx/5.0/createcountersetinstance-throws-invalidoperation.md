---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144469"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="59398-101">CounterSet. CreateCounterSetInstance agora lança InvalidOperationException se a instância já existe</span><span class="sxs-lookup"><span data-stu-id="59398-101">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="59398-102">A partir do .NET 5,0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> o lançará um <xref:System.InvalidOperationException> em vez de um <xref:System.ArgumentException> se o conjunto de contadores já existir.</span><span class="sxs-lookup"><span data-stu-id="59398-102">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

#### <a name="change-description"></a><span data-ttu-id="59398-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="59398-103">Change description</span></span>

<span data-ttu-id="59398-104">No .NET Framework e no .NET Core 1,0 a 3,1, você pode criar uma instância do conjunto de contadores chamando <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> .</span><span class="sxs-lookup"><span data-stu-id="59398-104">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="59398-105">No entanto, se o conjunto de contadores já existir, o método lançará uma <xref:System.ArgumentException> exceção.</span><span class="sxs-lookup"><span data-stu-id="59398-105">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="59398-106">No .NET 5,0 e versões posteriores, quando você chama <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> e o conjunto de contadores existe, uma <xref:System.InvalidOperationException> exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="59398-106">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59398-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="59398-107">Version introduced</span></span>

<span data-ttu-id="59398-108">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="59398-108">5.0 Preview 5</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59398-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="59398-109">Recommended action</span></span>

<span data-ttu-id="59398-110">Se você capturar <xref:System.ArgumentException> exceções em seu aplicativo ao chamar <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> , considere também capturar <xref:System.InvalidOperationException> exceções.</span><span class="sxs-lookup"><span data-stu-id="59398-110">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="59398-111"><xref:System.ArgumentException>Não é recomendável capturar exceções.</span><span class="sxs-lookup"><span data-stu-id="59398-111">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

#### <a name="category"></a><span data-ttu-id="59398-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="59398-112">Category</span></span>

<span data-ttu-id="59398-113">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="59398-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59398-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="59398-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->

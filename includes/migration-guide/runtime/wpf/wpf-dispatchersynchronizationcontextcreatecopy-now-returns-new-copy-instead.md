---
ms.openlocfilehash: fc6066fd0b23d299158114cb397934041b99ba47
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619892"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a><span data-ttu-id="672d1-101">DispatcherSynchronizationContext.CreateCopy do WPF agora retorna uma nova cópia em vez da instância atual</span><span class="sxs-lookup"><span data-stu-id="672d1-101">WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance</span></span>

#### <a name="details"></a><span data-ttu-id="672d1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="672d1-102">Details</span></span>

<span data-ttu-id="672d1-103">No .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retornava uma referência à instância atual, basicamente como uma otimização de desempenho.</span><span class="sxs-lookup"><span data-stu-id="672d1-103">In the .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> returned a reference to the current instance, primarily as a performance optimization.</span></span> <span data-ttu-id="672d1-104">No .NET Framework 4.5, ele retorna uma nova instância que possibilita, pela primeira vez, concluir que referências iguais indicam que o thread em execução está no contexto de sincronização correto.</span><span class="sxs-lookup"><span data-stu-id="672d1-104">In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.</span></span>  <span data-ttu-id="672d1-105">É provável que o código que verifica a identidade dessas referências seja afetado, mas, por causa da alteração, o código que chama <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> deve ser testado como parte da migração para o .NET Framework 4.5 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="672d1-105">It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> should be tested as part of migration to the .NET Framework 4.5 or newer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="672d1-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="672d1-106">Suggestion</span></span>

<span data-ttu-id="672d1-107">Lembre-se de que <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> agora retornará um novo objeto <xref:System.Threading.SynchronizationContext?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="672d1-107">Be aware that <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> will now return a new <xref:System.Threading.SynchronizationContext?displayProperty=fullName> object.</span></span> <span data-ttu-id="672d1-108">Anteriormente, o código que usava a equivalência de referências gerada dessa maneira não estava de fato verificado se ela estava no contexto apropriado, mas isso foi corrigido no .NET Framework 4.5 ou posteriores.</span><span class="sxs-lookup"><span data-stu-id="672d1-108">Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET Framework 4.5 or later.</span></span>  <span data-ttu-id="672d1-109">Embora não haja probabilidade de causar problemas, praticar os caminhos de código afetados deve ser suficiente para determinar se isso impõe algum problema.</span><span class="sxs-lookup"><span data-stu-id="672d1-109">While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.</span></span>

| <span data-ttu-id="672d1-110">Name</span><span class="sxs-lookup"><span data-stu-id="672d1-110">Name</span></span>    | <span data-ttu-id="672d1-111">Valor</span><span class="sxs-lookup"><span data-stu-id="672d1-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="672d1-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="672d1-112">Scope</span></span>   |<span data-ttu-id="672d1-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="672d1-113">Minor</span></span>|
|<span data-ttu-id="672d1-114">Versão</span><span class="sxs-lookup"><span data-stu-id="672d1-114">Version</span></span>|<span data-ttu-id="672d1-115">4.5</span><span class="sxs-lookup"><span data-stu-id="672d1-115">4.5</span></span>|
|<span data-ttu-id="672d1-116">Type</span><span class="sxs-lookup"><span data-stu-id="672d1-116">Type</span></span>|<span data-ttu-id="672d1-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="672d1-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="672d1-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="672d1-118">Affected APIs</span></span>

-<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|

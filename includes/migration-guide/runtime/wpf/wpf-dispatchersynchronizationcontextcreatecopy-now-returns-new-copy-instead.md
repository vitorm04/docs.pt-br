---
ms.openlocfilehash: a806107456a65a4919592da9535a2617f677cfe0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497099"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a><span data-ttu-id="ab258-101">DispatcherSynchronizationContext.CreateCopy do WPF agora retorna uma nova cópia em vez da instância atual</span><span class="sxs-lookup"><span data-stu-id="ab258-101">WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance</span></span>

#### <a name="details"></a><span data-ttu-id="ab258-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ab258-102">Details</span></span>

<span data-ttu-id="ab258-103">No .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retornava uma referência à instância atual, basicamente como uma otimização de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ab258-103">In the .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> returned a reference to the current instance, primarily as a performance optimization.</span></span> <span data-ttu-id="ab258-104">No .NET Framework 4.5, ele retorna uma nova instância que possibilita, pela primeira vez, concluir que referências iguais indicam que o thread em execução está no contexto de sincronização correto.</span><span class="sxs-lookup"><span data-stu-id="ab258-104">In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.</span></span>  <span data-ttu-id="ab258-105">É provável que o código que verifica a identidade dessas referências seja afetado, mas, por causa da alteração, o código que chama <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> deve ser testado como parte da migração para o .NET Framework 4.5 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="ab258-105">It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> should be tested as part of migration to the .NET Framework 4.5 or newer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ab258-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ab258-106">Suggestion</span></span>

<span data-ttu-id="ab258-107">Lembre-se de que <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> agora retornará um novo objeto <xref:System.Threading.SynchronizationContext?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ab258-107">Be aware that <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> will now return a new <xref:System.Threading.SynchronizationContext?displayProperty=fullName> object.</span></span> <span data-ttu-id="ab258-108">Anteriormente, o código que usava a equivalência de referências gerada dessa maneira não estava de fato verificado se ela estava no contexto apropriado, mas isso foi corrigido no .NET Framework 4.5 ou posteriores.</span><span class="sxs-lookup"><span data-stu-id="ab258-108">Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET Framework 4.5 or later.</span></span>  <span data-ttu-id="ab258-109">Embora não haja probabilidade de causar problemas, praticar os caminhos de código afetados deve ser suficiente para determinar se isso impõe algum problema.</span><span class="sxs-lookup"><span data-stu-id="ab258-109">While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.</span></span>

| <span data-ttu-id="ab258-110">Nome</span><span class="sxs-lookup"><span data-stu-id="ab258-110">Name</span></span>    | <span data-ttu-id="ab258-111">Valor</span><span class="sxs-lookup"><span data-stu-id="ab258-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ab258-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="ab258-112">Scope</span></span>   |<span data-ttu-id="ab258-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="ab258-113">Minor</span></span>|
|<span data-ttu-id="ab258-114">Versão</span><span class="sxs-lookup"><span data-stu-id="ab258-114">Version</span></span>|<span data-ttu-id="ab258-115">4.5</span><span class="sxs-lookup"><span data-stu-id="ab258-115">4.5</span></span>|
|<span data-ttu-id="ab258-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="ab258-116">Type</span></span>|<span data-ttu-id="ab258-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="ab258-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ab258-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ab258-118">Affected APIs</span></span>

- <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy`

-->

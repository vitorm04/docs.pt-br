---
ms.openlocfilehash: dd7d3e445772e4b5ec148576ccd1374d56e251bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614294"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="c0a16-101">Uso de serviços Reentrantes pode resultar em deadlock</span><span class="sxs-lookup"><span data-stu-id="c0a16-101">Deadlock may result when using Reentrant services</span></span>

#### <a name="details"></a><span data-ttu-id="c0a16-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c0a16-102">Details</span></span>

<span data-ttu-id="c0a16-103">Um deadlock pode resultar em um serviço Reentrante, o que restringe as instâncias do serviço para um thread de execução de cada vez.</span><span class="sxs-lookup"><span data-stu-id="c0a16-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="c0a16-104">Os serviços que podem apresentar esse problema terão o <xref:System.ServiceModel.ServiceBehaviorAttribute> a seguir no código:</span><span class="sxs-lookup"><span data-stu-id="c0a16-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a><span data-ttu-id="c0a16-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c0a16-105">Suggestion</span></span>

<span data-ttu-id="c0a16-106">Para solucionar esse problema, você pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0a16-106">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="c0a16-107">Definir o modo de simultaneidade do serviço como <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> ou &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;.</span><span class="sxs-lookup"><span data-stu-id="c0a16-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;.</span></span> <span data-ttu-id="c0a16-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c0a16-108">For example:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- <span data-ttu-id="c0a16-109">Instalar a atualização mais recente do .NET Framework 4.6.2 ou atualizar para uma versão posterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0a16-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="c0a16-110">Isso desabilita o fluxo do <xref:System.Threading.ExecutionContext> em <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c0a16-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c0a16-111">Esse comportamento é configurável; é equivalente a adicionar a seguinte configuração de aplicativo ao arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="c0a16-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

<span data-ttu-id="c0a16-112">O valor de `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` nunca deve ser definido como `false` para serviços Reentrant.</span><span class="sxs-lookup"><span data-stu-id="c0a16-112">The value of `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` should never be set to `false` for Reentrant services.</span></span>

| <span data-ttu-id="c0a16-113">Name</span><span class="sxs-lookup"><span data-stu-id="c0a16-113">Name</span></span>    | <span data-ttu-id="c0a16-114">Valor</span><span class="sxs-lookup"><span data-stu-id="c0a16-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c0a16-115">Escopo</span><span class="sxs-lookup"><span data-stu-id="c0a16-115">Scope</span></span>   | <span data-ttu-id="c0a16-116">Secundária</span><span class="sxs-lookup"><span data-stu-id="c0a16-116">Minor</span></span>       |
| <span data-ttu-id="c0a16-117">Versão</span><span class="sxs-lookup"><span data-stu-id="c0a16-117">Version</span></span> | <span data-ttu-id="c0a16-118">4.6.2</span><span class="sxs-lookup"><span data-stu-id="c0a16-118">4.6.2</span></span>       |
| <span data-ttu-id="c0a16-119">Type</span><span class="sxs-lookup"><span data-stu-id="c0a16-119">Type</span></span>    | <span data-ttu-id="c0a16-120">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="c0a16-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c0a16-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c0a16-121">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>

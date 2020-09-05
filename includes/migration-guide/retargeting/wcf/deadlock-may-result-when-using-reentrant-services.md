---
ms.openlocfilehash: f61cf21f9f30662cc8e383bb3aeb5c642f1665b8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496224"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="7cb01-101">Uso de serviços Reentrantes pode resultar em deadlock</span><span class="sxs-lookup"><span data-stu-id="7cb01-101">Deadlock may result when using Reentrant services</span></span>

#### <a name="details"></a><span data-ttu-id="7cb01-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7cb01-102">Details</span></span>

<span data-ttu-id="7cb01-103">Um deadlock pode resultar em um serviço Reentrante, o que restringe as instâncias do serviço para um thread de execução de cada vez.</span><span class="sxs-lookup"><span data-stu-id="7cb01-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="7cb01-104">Os serviços que podem apresentar esse problema terão o <xref:System.ServiceModel.ServiceBehaviorAttribute> a seguir no código:</span><span class="sxs-lookup"><span data-stu-id="7cb01-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a><span data-ttu-id="7cb01-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7cb01-105">Suggestion</span></span>

<span data-ttu-id="7cb01-106">Para solucionar esse problema, você pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7cb01-106">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="7cb01-107">Defina o modo de simultaneidade do serviço como <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> ou <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7cb01-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7cb01-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7cb01-108">For example:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- <span data-ttu-id="7cb01-109">Instalar a atualização mais recente do .NET Framework 4.6.2 ou atualizar para uma versão posterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7cb01-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="7cb01-110">Isso desabilita o fluxo do <xref:System.Threading.ExecutionContext> em <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7cb01-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7cb01-111">Esse comportamento é configurável; é equivalente a adicionar a seguinte configuração de aplicativo ao arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="7cb01-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

<span data-ttu-id="7cb01-112">O valor de `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` nunca deve ser definido como `false` para serviços Reentrant.</span><span class="sxs-lookup"><span data-stu-id="7cb01-112">The value of `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` should never be set to `false` for Reentrant services.</span></span>

| <span data-ttu-id="7cb01-113">Nome</span><span class="sxs-lookup"><span data-stu-id="7cb01-113">Name</span></span>    | <span data-ttu-id="7cb01-114">Valor</span><span class="sxs-lookup"><span data-stu-id="7cb01-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7cb01-115">Escopo</span><span class="sxs-lookup"><span data-stu-id="7cb01-115">Scope</span></span>   | <span data-ttu-id="7cb01-116">Secundária</span><span class="sxs-lookup"><span data-stu-id="7cb01-116">Minor</span></span>       |
| <span data-ttu-id="7cb01-117">Versão</span><span class="sxs-lookup"><span data-stu-id="7cb01-117">Version</span></span> | <span data-ttu-id="7cb01-118">4.6.2</span><span class="sxs-lookup"><span data-stu-id="7cb01-118">4.6.2</span></span>       |
| <span data-ttu-id="7cb01-119">Tipo</span><span class="sxs-lookup"><span data-stu-id="7cb01-119">Type</span></span>    | <span data-ttu-id="7cb01-120">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="7cb01-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="7cb01-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="7cb01-121">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>

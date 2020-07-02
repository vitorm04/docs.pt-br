---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614293"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a><span data-ttu-id="2d353-101">ServiceBase não propaga exceções de OnStart</span><span class="sxs-lookup"><span data-stu-id="2d353-101">ServiceBase doesn't propagate OnStart exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="2d353-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2d353-102">Details</span></span>

<span data-ttu-id="2d353-103">No .NET Framework 4.7 e nas versões anteriores, as exceções geradas durante a inicialização do serviço não são propagadas para o chamador de <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d353-103">In the .NET Framework 4.7 and earlier versions, exceptions thrown on service startup are not propagated to the caller of <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.</span></span><br/><span data-ttu-id="2d353-104">Começando com os aplicativos direcionados ao .NET Framework 4.7.1, o runtime propaga exceções para <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> de serviços que falham ao iniciar.</span><span class="sxs-lookup"><span data-stu-id="2d353-104">Starting with applications that target the .NET Framework 4.7.1, the runtime propagates exceptions to <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> for services that fail to start.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2d353-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2d353-105">Suggestion</span></span>

<span data-ttu-id="2d353-106">Na inicialização do serviço, se houver uma exceção, essa exceção será propagada.</span><span class="sxs-lookup"><span data-stu-id="2d353-106">On service start, if there is an exception, that exception will be propagated.</span></span> <span data-ttu-id="2d353-107">Isso deve ajudar a diagnosticar casos em que os serviços falham ao iniciar.</span><span class="sxs-lookup"><span data-stu-id="2d353-107">This should help diagnose cases where services fail to start.</span></span> <br/><span data-ttu-id="2d353-108">Se esse comportamento não for desejado, você poderá recusá-lo, adicionando o seguinte elemento &lt;AppContextSwitchOverrides&gt; à seção &lt;runtime&gt; do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="2d353-108">If this behavior is undesirable, you can opt out of it by adding the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

<span data-ttu-id="2d353-109">Se seu aplicativo for destinado a uma versão anterior à 4.7.1, mas você desejar ter esse comportamento, adicione o seguinte elemento &lt;AppContextSwitchOverrides&gt; à seção &lt;runtime&gt; do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="2d353-109">If your application targets an earlier version than 4.7.1 but you want to have this behavior, add the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| <span data-ttu-id="2d353-110">Name</span><span class="sxs-lookup"><span data-stu-id="2d353-110">Name</span></span>    | <span data-ttu-id="2d353-111">Valor</span><span class="sxs-lookup"><span data-stu-id="2d353-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2d353-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="2d353-112">Scope</span></span>   | <span data-ttu-id="2d353-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="2d353-113">Minor</span></span>       |
| <span data-ttu-id="2d353-114">Versão</span><span class="sxs-lookup"><span data-stu-id="2d353-114">Version</span></span> | <span data-ttu-id="2d353-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="2d353-115">4.7.1</span></span>       |
| <span data-ttu-id="2d353-116">Type</span><span class="sxs-lookup"><span data-stu-id="2d353-116">Type</span></span>    | <span data-ttu-id="2d353-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="2d353-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2d353-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2d353-118">Affected APIs</span></span>

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>

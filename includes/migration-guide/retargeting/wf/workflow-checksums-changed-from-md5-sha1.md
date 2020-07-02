---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614302"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a><span data-ttu-id="e015c-101">Somas de verificação de fluxo de trabalho alteradas de MD5 para SHA1</span><span class="sxs-lookup"><span data-stu-id="e015c-101">Workflow checksums changed from MD5 to SHA1</span></span>

#### <a name="details"></a><span data-ttu-id="e015c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e015c-102">Details</span></span>

<span data-ttu-id="e015c-103">Para compatibilidade com a depuração com o Visual Studio, o runtime de fluxo de trabalho gera uma soma de verificação para uma instância de fluxo de trabalho usando um algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="e015c-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow instance using a hashing algorithm.</span></span> <span data-ttu-id="e015c-104">No .NET Framework 4.6.2 e versões anteriores, o hash de soma de verificação do fluxo de trabalho usava o algoritmo MD5, o que causou problemas em sistemas habilitados para FIPS.</span><span class="sxs-lookup"><span data-stu-id="e015c-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="e015c-105">A partir do .NET Framework 4.7, o algoritmo será o SHA1.</span><span class="sxs-lookup"><span data-stu-id="e015c-105">Starting with the .NET Framework 4.7, the algorithm is SHA1.</span></span> <span data-ttu-id="e015c-106">Se o código persistir a essas somas de verificação, eles serão incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="e015c-106">If your code has persisted these checksums, they will be incompatible.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e015c-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e015c-107">Suggestion</span></span>

<span data-ttu-id="e015c-108">Se o código for incapaz de carregar instâncias de fluxo de trabalho por causa de uma falha na soma de verificação, tente configurar a opção `AppContext`&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; com true. Em código:</span><span class="sxs-lookup"><span data-stu-id="e015c-108">If your code is unable to load workflow instances due to a checksum failure, try setting the `AppContext` switch &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; to true.In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

<span data-ttu-id="e015c-109">Ou em nossa configuração:</span><span class="sxs-lookup"><span data-stu-id="e015c-109">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="e015c-110">Name</span><span class="sxs-lookup"><span data-stu-id="e015c-110">Name</span></span>    | <span data-ttu-id="e015c-111">Valor</span><span class="sxs-lookup"><span data-stu-id="e015c-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e015c-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="e015c-112">Scope</span></span>   | <span data-ttu-id="e015c-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="e015c-113">Minor</span></span>       |
| <span data-ttu-id="e015c-114">Versão</span><span class="sxs-lookup"><span data-stu-id="e015c-114">Version</span></span> | <span data-ttu-id="e015c-115">4.7</span><span class="sxs-lookup"><span data-stu-id="e015c-115">4.7</span></span>         |
| <span data-ttu-id="e015c-116">Type</span><span class="sxs-lookup"><span data-stu-id="e015c-116">Type</span></span>    | <span data-ttu-id="e015c-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="e015c-117">Retargeting</span></span> |

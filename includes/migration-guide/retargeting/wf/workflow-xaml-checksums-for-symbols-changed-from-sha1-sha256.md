---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617778"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a><span data-ttu-id="50417-101">As somas de verificação XAML do Fluxo de Trabalho para símbolos mudaram de SHA1 para SHA256</span><span class="sxs-lookup"><span data-stu-id="50417-101">Workflow XAML checksums for symbols changed from SHA1 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="50417-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="50417-102">Details</span></span>

<span data-ttu-id="50417-103">Para compatibilidade com a depuração com o Visual Studio, o runtime de fluxo de trabalho gera uma soma de verificação para um arquivo XAML do fluxo de trabalho usando um algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="50417-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow XAML file using a hashing algorithm.</span></span> <span data-ttu-id="50417-104">No .NET Framework 4.6.2 e versões anteriores, o hash de soma de verificação do fluxo de trabalho usava o algoritmo MD5, o que causou problemas em sistemas habilitados para FIPS.</span><span class="sxs-lookup"><span data-stu-id="50417-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="50417-105">Começando com o .NET Framework 4.7, o algoritmo padrão mudou para SHA1.</span><span class="sxs-lookup"><span data-stu-id="50417-105">Starting with the .NET Framework 4.7, the default algorithm was changed to SHA1.</span></span> <span data-ttu-id="50417-106">Começando com o .NET Framework 4.8, o algoritmo padrão mudou para SHA256.</span><span class="sxs-lookup"><span data-stu-id="50417-106">Starting with the .NET Framework 4.8, the default algorithm was changed to SHA256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="50417-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="50417-107">Suggestion</span></span>

<span data-ttu-id="50417-108">Se o seu código não puder carregar instâncias de fluxo de trabalho ou encontrar os símbolos apropriados devido a uma falha de soma de verificação, tente definir a `AppContext` opção "Switch.System. Activities. UseSHA1HashForDebuggerSymbols "to `true` .</span><span class="sxs-lookup"><span data-stu-id="50417-108">If your code is unable to load workflow instances or to find appropriate symbols due to a checksum failure, try setting the `AppContext` switch "Switch.System.Activities.UseSHA1HashForDebuggerSymbols" to `true`.</span></span> <span data-ttu-id="50417-109">No código:</span><span class="sxs-lookup"><span data-stu-id="50417-109">In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

<span data-ttu-id="50417-110">Ou em nossa configuração:</span><span class="sxs-lookup"><span data-stu-id="50417-110">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="50417-111">Name</span><span class="sxs-lookup"><span data-stu-id="50417-111">Name</span></span>    | <span data-ttu-id="50417-112">Valor</span><span class="sxs-lookup"><span data-stu-id="50417-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="50417-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="50417-113">Scope</span></span>   | <span data-ttu-id="50417-114">Secundária</span><span class="sxs-lookup"><span data-stu-id="50417-114">Minor</span></span>       |
| <span data-ttu-id="50417-115">Versão</span><span class="sxs-lookup"><span data-stu-id="50417-115">Version</span></span> | <span data-ttu-id="50417-116">4.8</span><span class="sxs-lookup"><span data-stu-id="50417-116">4.8</span></span>         |
| <span data-ttu-id="50417-117">Type</span><span class="sxs-lookup"><span data-stu-id="50417-117">Type</span></span>    | <span data-ttu-id="50417-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="50417-118">Retargeting</span></span> |

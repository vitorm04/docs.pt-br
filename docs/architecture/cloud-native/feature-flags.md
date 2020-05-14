---
title: Sinalizadores de recurso
description: Implementar sinalizadores de recurso em aplicativos nativos de nuvem utilizando Azure App config
ms.date: 05/03/2020
ms.openlocfilehash: 72e1bfe777854a74fcac926811caf97e59986146
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83398305"
---
# <a name="feature-flags"></a><span data-ttu-id="6442e-103">Sinalizadores de recurso</span><span class="sxs-lookup"><span data-stu-id="6442e-103">Feature flags</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6442e-104">No capítulo 1, afirmamos que a nuvem nativa é muito sobre velocidade e agilidade.</span><span class="sxs-lookup"><span data-stu-id="6442e-104">In chapter 1, we affirmed that cloud native is much about speed and agility.</span></span> <span data-ttu-id="6442e-105">Os usuários esperam uma rápida capacidade de resposta, recursos inovadores e zero tempo de inatividade.</span><span class="sxs-lookup"><span data-stu-id="6442e-105">Users expect rapid responsiveness, innovative features, and zero downtime.</span></span> <span data-ttu-id="6442e-106">`Feature flags`é uma técnica de implantação moderna que ajuda a aumentar a agilidade para aplicativos nativos de nuvem.</span><span class="sxs-lookup"><span data-stu-id="6442e-106">`Feature flags` are a modern deployment technique that helps increase agility for cloud-native applications.</span></span> <span data-ttu-id="6442e-107">Eles permitem que você implante novos recursos em um ambiente de produção, mas restrinja sua disponibilidade.</span><span class="sxs-lookup"><span data-stu-id="6442e-107">They enable you to deploy new features into a production environment, but restrict their availability.</span></span> <span data-ttu-id="6442e-108">Com o movimento de um comutador, você pode ativar um novo recurso para usuários específicos sem reiniciar o aplicativo ou implantar um novo código.</span><span class="sxs-lookup"><span data-stu-id="6442e-108">With the flick of a switch, you can activate a new feature for specific users without restarting the app or deploying new code.</span></span> <span data-ttu-id="6442e-109">Eles separam o lançamento dos novos recursos da implantação de código.</span><span class="sxs-lookup"><span data-stu-id="6442e-109">They separate the release of new features from their code deployment.</span></span>

<span data-ttu-id="6442e-110">Os sinalizadores de recurso são criados sobre a lógica condicional que controla a visibilidade da funcionalidade para usuários em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6442e-110">Feature flags are built upon conditional logic that control visibility of functionality for users at runtime.</span></span> <span data-ttu-id="6442e-111">Em sistemas nativos de nuvem modernos, é comum implantar novos recursos no início da produção, mas testá-los com um público limitado.</span><span class="sxs-lookup"><span data-stu-id="6442e-111">In modern cloud-native systems, it's common to deploy new features into production early, but test them with a limited audience.</span></span> <span data-ttu-id="6442e-112">À medida que a confiança aumenta, o recurso pode ser distribuído incrementalmente para públicos mais largos.</span><span class="sxs-lookup"><span data-stu-id="6442e-112">As confidence increases, the feature can be incrementally rolled out to wider audiences.</span></span>

<span data-ttu-id="6442e-113">Outros casos de uso para sinalizadores de recurso incluem:</span><span class="sxs-lookup"><span data-stu-id="6442e-113">Other use cases for feature flags include:</span></span>

- <span data-ttu-id="6442e-114">Restrinja a funcionalidade premium a grupos de clientes específicos dispostos a pagar taxas de assinatura maiores.</span><span class="sxs-lookup"><span data-stu-id="6442e-114">Restrict premium functionality to specific customer groups willing to pay higher subscription fees.</span></span>
- <span data-ttu-id="6442e-115">Estabilizar um sistema ao desativar rapidamente um recurso de problema, evitando os riscos de uma reversão ou um hotfix imediato.</span><span class="sxs-lookup"><span data-stu-id="6442e-115">Stabilize a system by quickly deactivating a problem feature, avoiding the risks of a rollback or immediate hotfix.</span></span>
- <span data-ttu-id="6442e-116">Desabilite um recurso opcional com alto consumo de recursos durante períodos de pico de uso.</span><span class="sxs-lookup"><span data-stu-id="6442e-116">Disable an optional feature with high resource consumption during peak usage periods.</span></span>
- <span data-ttu-id="6442e-117">Conduza `experimental feature releases` a pequenos segmentos de usuário para validar a viabilidade e a popularidade.</span><span class="sxs-lookup"><span data-stu-id="6442e-117">Conduct `experimental feature releases` to small user segments to validate feasibility and popularity.</span></span>

<span data-ttu-id="6442e-118">Os sinalizadores de recurso também promovem o `trunk-based` desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="6442e-118">Feature flags also promote `trunk-based` development.</span></span> <span data-ttu-id="6442e-119">É um modelo de ramificação de controle de origem em que os desenvolvedores colaboram em recursos em uma única ramificação.</span><span class="sxs-lookup"><span data-stu-id="6442e-119">It's a source-control branching model where developers collaborate on features in a single branch.</span></span> <span data-ttu-id="6442e-120">A abordagem minimiza o risco e a complexidade de Mesclar grandes números de branches de recursos de longa execução.</span><span class="sxs-lookup"><span data-stu-id="6442e-120">The approach minimizes the risk and complexity of merging large numbers of long-running feature branches.</span></span> <span data-ttu-id="6442e-121">Os recursos ficam indisponíveis até serem ativados.</span><span class="sxs-lookup"><span data-stu-id="6442e-121">Features are unavailable until activated.</span></span>

## <a name="implementing-feature-flags"></a><span data-ttu-id="6442e-122">Implementando sinalizadores de recurso</span><span class="sxs-lookup"><span data-stu-id="6442e-122">Implementing feature flags</span></span>

<span data-ttu-id="6442e-123">Em seu núcleo, um sinalizador de recurso é uma referência a um simples `decision object` .</span><span class="sxs-lookup"><span data-stu-id="6442e-123">At its core, a feature flag is a reference to a simple `decision object`.</span></span> <span data-ttu-id="6442e-124">Ele retorna um estado booliano de `on` ou `off` .</span><span class="sxs-lookup"><span data-stu-id="6442e-124">It returns a Boolean state of `on` or `off`.</span></span> <span data-ttu-id="6442e-125">O sinalizador normalmente encapsula um bloco de código que encapsula uma funcionalidade de recurso.</span><span class="sxs-lookup"><span data-stu-id="6442e-125">The flag typically wraps a block of code that encapsulates a feature capability.</span></span> <span data-ttu-id="6442e-126">O estado do sinalizador determina se o bloco de código é executado para um determinado usuário.</span><span class="sxs-lookup"><span data-stu-id="6442e-126">The state of the flag determines whether that code block executes for a given user.</span></span> <span data-ttu-id="6442e-127">A Figura 10-11 mostra a implementação.</span><span class="sxs-lookup"><span data-stu-id="6442e-127">Figure 10-11 shows the implementation.</span></span>

```c#
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

<span data-ttu-id="6442e-128">**Figura 10-11** – implementação de sinalizador de recurso simples.</span><span class="sxs-lookup"><span data-stu-id="6442e-128">**Figure 10-11** - Simple feature flag implementation.</span></span>

<span data-ttu-id="6442e-129">Observe como essa abordagem separa a lógica de decisão do código de recurso.</span><span class="sxs-lookup"><span data-stu-id="6442e-129">Note how this approach separates the decision logic from the feature code.</span></span>

<span data-ttu-id="6442e-130">No capítulo 1, discutimos o `Twelve-Factor App` .</span><span class="sxs-lookup"><span data-stu-id="6442e-130">In chapter 1, we discussed the `Twelve-Factor App`.</span></span> <span data-ttu-id="6442e-131">As diretrizes recomendadas para manter as definições de configuração externas do código executável do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6442e-131">The guidance recommended keeping configuration settings external from application executable code.</span></span> <span data-ttu-id="6442e-132">Quando necessário, as configurações podem ser lidas na fonte externa.</span><span class="sxs-lookup"><span data-stu-id="6442e-132">When needed, settings can be read in from the external source.</span></span> <span data-ttu-id="6442e-133">Os valores de configuração do sinalizador de recurso também devem ser independentes da base de código.</span><span class="sxs-lookup"><span data-stu-id="6442e-133">Feature flag configuration values should also be independent from their codebase.</span></span> <span data-ttu-id="6442e-134">Ao externalizar a configuração do sinalizador em um repositório separado, você pode alterar o estado do sinalizador sem modificar e reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6442e-134">By externalizing flag configuration in a separate repository, you can change flag state without modifying and redeploying the application.</span></span>

<span data-ttu-id="6442e-135">[Azure app configuração](https://docs.microsoft.com/azure/azure-app-configuration/overview) fornece um repositório centralizado para sinalizadores de recursos.</span><span class="sxs-lookup"><span data-stu-id="6442e-135">[Azure App Configuration](https://docs.microsoft.com/azure/azure-app-configuration/overview) provides a centralized repository for feature flags.</span></span> <span data-ttu-id="6442e-136">Com ele, você define diferentes tipos de sinalizadores de recursos e manipula seus Estados de forma rápida e confiável.</span><span class="sxs-lookup"><span data-stu-id="6442e-136">With it, you define different kinds of feature flags and manipulate their states quickly and confidently.</span></span> <span data-ttu-id="6442e-137">Você adiciona as bibliotecas de cliente de configuração de aplicativo ao seu aplicativo para habilitar a funcionalidade de sinalizador de recurso.</span><span class="sxs-lookup"><span data-stu-id="6442e-137">You add the App Configuration client libraries to your application to enable feature flag functionality.</span></span> <span data-ttu-id="6442e-138">Há suporte para várias estruturas de linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="6442e-138">Various programming language frameworks are supported.</span></span>

<span data-ttu-id="6442e-139">Os sinalizadores de recurso podem ser facilmente implementados em um [serviço ASP.NET Core](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6442e-139">Feature flags can be easily implemented in an [ASP.NET Core service](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span></span> <span data-ttu-id="6442e-140">A instalação das bibliotecas de gerenciamento de recursos do .NET e do provedor de configuração de aplicativo permite que você adicione sinalizadores de recurso declarativamente ao seu código.</span><span class="sxs-lookup"><span data-stu-id="6442e-140">Installing the .NET Feature Management libraries and App Configuration provider enable you to declaratively add feature flags to your code.</span></span> <span data-ttu-id="6442e-141">Eles habilitam `FeatureGate` atributos para que você não precise gravar manualmente as instruções if na base de código.</span><span class="sxs-lookup"><span data-stu-id="6442e-141">They enable `FeatureGate` attributes so that you don't have to manually write if statements across your codebase.</span></span>

<span data-ttu-id="6442e-142">Uma vez configurado em sua classe de inicialização, você pode adicionar a funcionalidade de sinalizador de recurso no nível do controlador, da ação ou do middleware.</span><span class="sxs-lookup"><span data-stu-id="6442e-142">Once configured in your Startup class, you can add feature flag functionality at the controller, action, or middleware level.</span></span> <span data-ttu-id="6442e-143">A Figura 10-12 apresenta a implementação do controlador e da ação:</span><span class="sxs-lookup"><span data-stu-id="6442e-143">Figure 10-12 presents controller and action implementation:</span></span>

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

<span data-ttu-id="6442e-144">**Figura 10-12** -implementação do sinalizador de recurso em um controlador e uma ação.</span><span class="sxs-lookup"><span data-stu-id="6442e-144">**Figure 10-12** - Feature flag implementation in a controller and action.</span></span>

<span data-ttu-id="6442e-145">Se um sinalizador de recurso estiver desabilitado, o usuário receberá um código de status 404 (não encontrado) sem nenhum corpo de resposta.</span><span class="sxs-lookup"><span data-stu-id="6442e-145">If a feature flag is disabled, the user will receive a 404 (Not Found) status code with no response body.</span></span>

<span data-ttu-id="6442e-146">Os sinalizadores de recurso também podem ser injetados diretamente em classes C#.</span><span class="sxs-lookup"><span data-stu-id="6442e-146">Feature flags can also be injected directly into C# classes.</span></span> <span data-ttu-id="6442e-147">A Figura 10-13 mostra a injeção do sinalizador de recurso:</span><span class="sxs-lookup"><span data-stu-id="6442e-147">Figure 10-13 shows feature flag injection:</span></span>

```c#
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

<span data-ttu-id="6442e-148">**Figura 10-13** -injeção de sinalizador de recurso em uma classe.</span><span class="sxs-lookup"><span data-stu-id="6442e-148">**Figure 10-13** - Feature flag injection into a class.</span></span>

<span data-ttu-id="6442e-149">As bibliotecas de gerenciamento de recursos gerenciam o ciclo de vida do sinalizador de recursos em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="6442e-149">The Feature Management libraries manage the feature flag lifecycle behind the scenes.</span></span> <span data-ttu-id="6442e-150">Por exemplo, para minimizar um número alto de chamadas para o repositório de configuração, o sinalizador cache de bibliotecas indica uma duração especificada.</span><span class="sxs-lookup"><span data-stu-id="6442e-150">For example, to minimize high numbers of calls to the configuration store, the libraries cache flag states for a specified duration.</span></span> <span data-ttu-id="6442e-151">Eles podem garantir a imutabilidade dos Estados de sinalizador durante uma chamada de solicitação.</span><span class="sxs-lookup"><span data-stu-id="6442e-151">They can guarantee the immutability of flag states during a request call.</span></span> <span data-ttu-id="6442e-152">Eles também oferecem um `Point-in-time snapshot` .</span><span class="sxs-lookup"><span data-stu-id="6442e-152">They also offer a `Point-in-time snapshot`.</span></span> <span data-ttu-id="6442e-153">Você pode reconstruir o histórico de qualquer valor-chave e fornecer seu valor passado a qualquer momento nos sete dias anteriores.</span><span class="sxs-lookup"><span data-stu-id="6442e-153">You can reconstruct the history of any key-value and provide its past value at any moment within the previous seven days.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6442e-154">[Anterior](devops.md) 
> [Avançar](infrastructure-as-code.md)</span><span class="sxs-lookup"><span data-stu-id="6442e-154">[Previous](devops.md)
[Next](infrastructure-as-code.md)</span></span>

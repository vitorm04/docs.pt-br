---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614310"
---
### <a name="wpf-pointer-based-touch-stack"></a><span data-ttu-id="41913-101">Pilha de toque baseada em ponteiro do WPF</span><span class="sxs-lookup"><span data-stu-id="41913-101">WPF Pointer-Based Touch Stack</span></span>

#### <a name="details"></a><span data-ttu-id="41913-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="41913-102">Details</span></span>

<span data-ttu-id="41913-103">Essa alteração possibilita habilitar uma pilha de toque/caneta do WPF baseada em WM_POINTER opcional.</span><span class="sxs-lookup"><span data-stu-id="41913-103">This change adds the ability to enable an optional WM_POINTER based WPF touch/stylus stack.</span></span>  <span data-ttu-id="41913-104">Desenvolvedores que não habilitarem explicitamente essa opção não deverão ver alterações no comportamento de toque/caneta do WPF. Problemas conhecidos atuais com a pilha de toque/caneta baseada em WM_POINTER opcional:</span><span class="sxs-lookup"><span data-stu-id="41913-104">Developers that do not explicitly enable this should see no change in WPF touch/stylus behavior.Current Known Issues With optional WM_POINTER based touch/stylus stack:</span></span>

- <span data-ttu-id="41913-105">Não há suporte para escrita à tinta em tempo real.</span><span class="sxs-lookup"><span data-stu-id="41913-105">No support for real-time inking.</span></span>
- <span data-ttu-id="41913-106">Embora os plug-ins de caneta e escrita à tinta ainda funcionem, eles serão processados no thread da interface do usuário, o que pode levar a um desempenho ruim.</span><span class="sxs-lookup"><span data-stu-id="41913-106">While inking and StylusPlugins will still work, they will be processed on the UI Thread which can lead to poor performance.</span></span>
- <span data-ttu-id="41913-107">Alterações de comportamento devido a alterações na promoção de eventos de toque/caneta para eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="41913-107">Behavioral changes due to changes in promotion from touch/stylus events to mouse events</span></span>
- <span data-ttu-id="41913-108">A manipulação pode se comportar de maneira diferente</span><span class="sxs-lookup"><span data-stu-id="41913-108">Manipulation may behave differently</span></span>
- <span data-ttu-id="41913-109">Arrastar/soltar não mostrará comentários apropriados para entrada por toque</span><span class="sxs-lookup"><span data-stu-id="41913-109">Drag/Drop will not show appropriate feedback for touch input</span></span>
- <span data-ttu-id="41913-110">Isso não afeta entrada de caneta</span><span class="sxs-lookup"><span data-stu-id="41913-110">This does not affect stylus input</span></span>
- <span data-ttu-id="41913-111">Arrastar/soltar não pode mais ser iniciado em eventos de toque/caneta</span><span class="sxs-lookup"><span data-stu-id="41913-111">Drag/Drop can no longer be initiated on touch/stylus events</span></span>
- <span data-ttu-id="41913-112">Isso pode travar o aplicativo até que a entrada do mouse seja detectada.</span><span class="sxs-lookup"><span data-stu-id="41913-112">This can potentially hang the application until mouse input is detected.</span></span>
- <span data-ttu-id="41913-113">Em vez disso, os desenvolvedores devem iniciar a ação de arrastar e soltar usando eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="41913-113">Instead, developers should initiate drag and drop from mouse events.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="41913-114">Sugestão</span><span class="sxs-lookup"><span data-stu-id="41913-114">Suggestion</span></span>

<span data-ttu-id="41913-115">Desenvolvedores que desejam habilitar essa pilha podem adicionar/mesclar o seguinte ao arquivo app.config do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="41913-115">Developers who wish to enable this stack can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="41913-116">Remover isso ou definir o valor como false desabilita essa pilha opcional. Observe que essa pilha está disponível somente na Atualização do Windows 10 para Criadores e superiores.</span><span class="sxs-lookup"><span data-stu-id="41913-116">Removing this or setting the value to false will turn this optional stack off.Note that this stack is available only on Windows 10 Creators Update and above.</span></span>

| <span data-ttu-id="41913-117">Name</span><span class="sxs-lookup"><span data-stu-id="41913-117">Name</span></span>    | <span data-ttu-id="41913-118">Valor</span><span class="sxs-lookup"><span data-stu-id="41913-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="41913-119">Escopo</span><span class="sxs-lookup"><span data-stu-id="41913-119">Scope</span></span>   | <span data-ttu-id="41913-120">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="41913-120">Edge</span></span>        |
| <span data-ttu-id="41913-121">Versão</span><span class="sxs-lookup"><span data-stu-id="41913-121">Version</span></span> | <span data-ttu-id="41913-122">4.7</span><span class="sxs-lookup"><span data-stu-id="41913-122">4.7</span></span>         |
| <span data-ttu-id="41913-123">Type</span><span class="sxs-lookup"><span data-stu-id="41913-123">Type</span></span>    | <span data-ttu-id="41913-124">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="41913-124">Retargeting</span></span> |

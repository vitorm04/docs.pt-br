---
title: "Exemplo: solucionando problemas de programação dinâmica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fdf3f12b325282b048420f57befa752f3f3f6803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="69549-102">Exemplo: solucionando problemas de programação dinâmica</span><span class="sxs-lookup"><span data-stu-id="69549-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
>  <span data-ttu-id="69549-103">Este tópico refere-se ao Developer Preview do .NET Nativo, que é um software em pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="69549-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="69549-104">Você pode baixar a versão prévia do [site Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (registro obrigatório).</span><span class="sxs-lookup"><span data-stu-id="69549-104">You can download the preview from the [Microsoft Connect website](http://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="69549-105">Nem todas as falhas de pesquisa de metadados em aplicativos desenvolvidos com a cadeia de ferramentas [!INCLUDE[net_native](../../../includes/net-native-md.md)] resulta em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="69549-105">Not all metadata lookup failures in apps developed using the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain result in an exception.</span></span>  <span data-ttu-id="69549-106">Alguns podem manifestar-se de formas imprevisíveis em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="69549-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="69549-107">O exemplo a seguir mostra uma violação de acesso causada pela referência a um objeto nulo:</span><span class="sxs-lookup"><span data-stu-id="69549-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
```  
Access violation - code c0000005 (first chance)  
App!$3_App::Core::Util::NavigationArgs.Setup  
App!$3_App::Core::Util::NavigationArgs..ctor  
App!$0_App::Gibbon::Util::DesktopNavigationArgs..ctor  
App!$0_App::ViewModels::DesktopAppVM.NavigateToPage  
App!$3_App::Core::ViewModels::AppViewModel.NavigateToFirstPage  
App!$3_App::Core::ViewModels::AppViewModel::<HandleLaunch>d__a.MoveNext  
App!$43_System::Runtime::CompilerServices::AsyncMethodBuilderCore.CallMoveNext  
App!System::Action.InvokeClosedStaticThunk  
App!System::Action.Invoke  
App!$43_System::Threading::Tasks::AwaitTaskContinuation.InvokeAction  
App!$43_System::Threading::SendOrPostCallback.InvokeOpenStaticThunk  
[snip]  
```  
  
 <span data-ttu-id="69549-108">Vamos tentar solucionar essa exceção usando a abordagem de três etapas descrita na seção “Resolver manualmente os metadados ausentes” da [Introdução](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="69549-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="69549-109">O que o aplicativo estava fazendo?</span><span class="sxs-lookup"><span data-stu-id="69549-109">What was the app doing?</span></span>  
 <span data-ttu-id="69549-110">A primeira coisa a observar é o maquinário da palavra-chave do `async` na base da pilha.</span><span class="sxs-lookup"><span data-stu-id="69549-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="69549-111">Determinar o que o aplicativo fazia em método `async` pode ser problemático, porque a pilha perde o contexto da chamada de origem e executa o código `async` em um thread diferente.</span><span class="sxs-lookup"><span data-stu-id="69549-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="69549-112">No entanto, podemos deduzir que o aplicativo está tentando carregar sua primeira página.</span><span class="sxs-lookup"><span data-stu-id="69549-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="69549-113">Na implementação de `NavigationArgs.Setup`, o seguinte código causou a violação de acesso:</span><span class="sxs-lookup"><span data-stu-id="69549-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 <span data-ttu-id="69549-114">Nesta instância, a propriedade `LayoutVM` em `AppViewModel.Current` era **null**.</span><span class="sxs-lookup"><span data-stu-id="69549-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="69549-115">A ausência de metadados causou uma diferença de comportamento sutil e resultou em uma propriedade sendo não inicializada em vez do conjunto, como o aplicativo esperava.</span><span class="sxs-lookup"><span data-stu-id="69549-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="69549-116">Definir um ponto de interrupção no código onde `LayoutVM` deveria ter sido inicializado poderá esclarecer a situação.</span><span class="sxs-lookup"><span data-stu-id="69549-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="69549-117">No entanto, observe que o tipo do `LayoutVM` é `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span><span class="sxs-lookup"><span data-stu-id="69549-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="69549-118">A única diretiva de metadados presente até agora no arquivo rd.xml é:</span><span class="sxs-lookup"><span data-stu-id="69549-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="69549-119">O motivo mais provável da falha é que metadados estão faltando em `App.Core.ViewModels.Layout.LayoutApplicationVM` porque ela está em um namespace diferente.</span><span class="sxs-lookup"><span data-stu-id="69549-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="69549-120">Nesse caso, adicionar uma diretiva de tempo de execução para `App.Core.ViewModels` resolveu o problema.</span><span class="sxs-lookup"><span data-stu-id="69549-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="69549-121">A causa raiz foi uma chamada à API ao método <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> que retornou **null** e o aplicativo ignorou silenciosamente o problema até que ocorreu uma falha.</span><span class="sxs-lookup"><span data-stu-id="69549-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="69549-122">Na programação dinâmica, uma boa prática ao usar APIs de reflexão em [!INCLUDE[net_native](../../../includes/net-native-md.md)] é usar as sobrecargas <xref:System.Type.GetType%2A?displayProperty=nameWithType> que geram uma exceção em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="69549-122">In dynamic programming, a good practice when using reflection APIs under [!INCLUDE[net_native](../../../includes/net-native-md.md)] is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="69549-123">Esta é uma ocorrência isolada?</span><span class="sxs-lookup"><span data-stu-id="69549-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="69549-124">Outros problemas também podem surgir ao usar `App.Core.ViewModels`.</span><span class="sxs-lookup"><span data-stu-id="69549-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="69549-125">Você deve decidir se vale a pena identificar e corrigir cada exceção de metadados ausentes, ou economizar tempo e adicionar diretivas para uma classe maior de tipos.</span><span class="sxs-lookup"><span data-stu-id="69549-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="69549-126">Aqui, adicionar metadados `dynamic` a `App.Core.ViewModels` pode ser a melhor abordagem se o aumento de tamanho resultante do binário de saída não for um problema.</span><span class="sxs-lookup"><span data-stu-id="69549-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="69549-127">O código pode ser reescrito?</span><span class="sxs-lookup"><span data-stu-id="69549-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="69549-128">Se o aplicativo tivesse usado `typeof(LayoutApplicationVM)` em vez de `Type.GetType("LayoutApplicationVM")`, a cadeia de ferramentas poderia ter preservado os metadados `browse`.</span><span class="sxs-lookup"><span data-stu-id="69549-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="69549-129">No entanto, ele ainda não criaria os metadados de `invoke`, o que levaria a uma exceção [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ao instanciar o tipo.</span><span class="sxs-lookup"><span data-stu-id="69549-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="69549-130">Para evitar a exceção, ainda seria necessário adicionar uma diretiva de tempo de execução para o namespace ou o tipo que especifica a política `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="69549-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="69549-131">Para obter informações sobre as diretivas de tempo de execução, consulte a [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="69549-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69549-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69549-132">See Also</span></span>  
 [<span data-ttu-id="69549-133">Introdução</span><span class="sxs-lookup"><span data-stu-id="69549-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="69549-134">Exemplo: tratando exceções ao associar dados</span><span class="sxs-lookup"><span data-stu-id="69549-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)

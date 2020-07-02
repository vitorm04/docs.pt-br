---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617103"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a><span data-ttu-id="cef67-101">Sobrecargas novas (ambíguas) do Dispatcher.Invoke podem resultar em comportamento diferente</span><span class="sxs-lookup"><span data-stu-id="cef67-101">New (ambiguous) Dispatcher.Invoke overloads could result in different behavior</span></span>

#### <a name="details"></a><span data-ttu-id="cef67-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="cef67-102">Details</span></span>

<span data-ttu-id="cef67-103">O .NET Framework 4.5 adiciona novas sobrecargas ao <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> que incluem um parâmetro do tipo <xref:System.Action>.</span><span class="sxs-lookup"><span data-stu-id="cef67-103">The .NET Framework 4.5 adds new overloads to <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> that include a parameter of type <xref:System.Action>.</span></span> <span data-ttu-id="cef67-104">Quando um código existente é recompilado, os compiladores podem resolver as chamadas aos métodos Dispatcher.Invoke que têm um parâmetro <xref:System.Delegate> como chamadas aos métodos Dispatcher.Invoke com um parâmetro <xref:System.Action>.</span><span class="sxs-lookup"><span data-stu-id="cef67-104">When existing code is recompiled, compilers may resolve calls to Dispatcher.Invoke methods that have a <xref:System.Delegate> parameter as calls to Dispatcher.Invoke methods with an <xref:System.Action> parameter.</span></span> <span data-ttu-id="cef67-105">Se uma chamada à sobrecarga do Dispatcher.Invoke com um parâmetro <xref:System.Delegate> for resolvida como uma chamada à sobrecarga do Dispatcher.Invoke com um parâmetro <xref:System.Action>, poderão ocorrer as seguintes diferenças no comportamento:</span><span class="sxs-lookup"><span data-stu-id="cef67-105">If a call to a Dispatcher.Invoke overload with a  <xref:System.Delegate> parameter is resolved as a call to a Dispatcher.Invoke overload with an <xref:System.Action> parameter, the following differences in behavior may occur:</span></span>

- <span data-ttu-id="cef67-106">Se ocorrer uma exceção, os eventos <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> e <xref:System.Windows.Threading.Dispatcher.UnhandledException> não serão gerados.</span><span class="sxs-lookup"><span data-stu-id="cef67-106">If an exception occurs, the <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> and <xref:System.Windows.Threading.Dispatcher.UnhandledException> events are not raised.</span></span> <span data-ttu-id="cef67-107">Em vez disso, as exceções são tratadas pelo evento <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="cef67-107">Instead, exceptions are handled by the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> event.</span></span>
- <span data-ttu-id="cef67-108">Chamadas para alguns membros, como <xref:System.Windows.Threading.DispatcherOperation.Result>, são bloqueadas até que a operação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="cef67-108">Calls to some members, such as <xref:System.Windows.Threading.DispatcherOperation.Result>, block until the operation has completed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cef67-109">Sugestão</span><span class="sxs-lookup"><span data-stu-id="cef67-109">Suggestion</span></span>

<span data-ttu-id="cef67-110">Para evitar ambiguidade (e possíveis diferenças no tratamento de exceções ou nos comportamentos de bloqueio), o código que chama o Dispatcher.Invoke pode passar um object[] vazio como um segundo parâmetro à chamada de Invoke para garantir a resolução da sobrecarga do método no .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="cef67-110">To avoid ambiguity (and potential differences in exception handling or blocking behaviors), code calling Dispatcher.Invoke can pass an empty object[] as a second parameter to the Invoke call to be sure of resolving to the .NET Framework 4.0 method overload.</span></span>

| <span data-ttu-id="cef67-111">Name</span><span class="sxs-lookup"><span data-stu-id="cef67-111">Name</span></span>    | <span data-ttu-id="cef67-112">Valor</span><span class="sxs-lookup"><span data-stu-id="cef67-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cef67-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="cef67-113">Scope</span></span>   | <span data-ttu-id="cef67-114">Secundária</span><span class="sxs-lookup"><span data-stu-id="cef67-114">Minor</span></span>       |
| <span data-ttu-id="cef67-115">Versão</span><span class="sxs-lookup"><span data-stu-id="cef67-115">Version</span></span> | <span data-ttu-id="cef67-116">4.5</span><span class="sxs-lookup"><span data-stu-id="cef67-116">4.5</span></span>         |
| <span data-ttu-id="cef67-117">Type</span><span class="sxs-lookup"><span data-stu-id="cef67-117">Type</span></span>    | <span data-ttu-id="cef67-118">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="cef67-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="cef67-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="cef67-119">Affected APIs</span></span>

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>

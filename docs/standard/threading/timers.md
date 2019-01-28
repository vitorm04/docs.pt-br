---
title: Temporizadores
description: Saiba quais temporizadores .NET devem ser usados em um ambiente multi-threaded.
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 644ccf5951e9d2556fc697d2fd763f026fd0ebdb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617220"
---
# <a name="timers"></a><span data-ttu-id="92eba-103">Temporizadores</span><span class="sxs-lookup"><span data-stu-id="92eba-103">Timers</span></span>

<span data-ttu-id="92eba-104">O .NET fornece dois temporizadores a serem usados em um ambiente multi-threaded:</span><span class="sxs-lookup"><span data-stu-id="92eba-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="92eba-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, que executa um único método de retorno de chamada em um thread <xref:System.Threading.ThreadPool> em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="92eba-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="92eba-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, que por padrão gera um evento em um thread <xref:System.Threading.ThreadPool> em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="92eba-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="92eba-107">Algumas implementações do .NET podem incluir temporizadores adicionais:</span><span class="sxs-lookup"><span data-stu-id="92eba-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="92eba-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: um componente do Windows Forms que dispara um evento em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="92eba-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="92eba-109">O componente não tem nenhuma interface do usuário e é projetado para ser usado em um ambiente single-threaded.</span><span class="sxs-lookup"><span data-stu-id="92eba-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="92eba-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: um componente do ASP.NET que executa postbacks de página da Web assíncrona ou síncrona em intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="92eba-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="92eba-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: um temporizador que é integrado à fila <xref:System.Windows.Threading.Dispatcher> que é processada em um intervalo de tempo especificado e com uma prioridade especificada.</span><span class="sxs-lookup"><span data-stu-id="92eba-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="92eba-112">A classe System.Threading.Timer</span><span class="sxs-lookup"><span data-stu-id="92eba-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="92eba-113">A classe <xref:System.Threading.Timer?displayProperty=nameWithType> permite chamar um delegado continuamente em intervalos de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="92eba-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="92eba-114">Você também pode usar essa classe para agendar uma única chamada a um delegado em um intervalo de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="92eba-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="92eba-115">O delegado é executado em um thread <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="92eba-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="92eba-116">Ao criar um objeto <xref:System.Threading.Timer?displayProperty=nameWithType>, você especifica um delegado <xref:System.Threading.TimerCallback> que define o método de retorno de chamada, um objeto de estado opcional que é passado para o retorno de chamada, o período de atraso antes da primeira invocação do retorno de chamada e o intervalo de tempo entre as invocações do retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="92eba-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="92eba-117">Para cancelar um temporizador pendente, chame o método <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92eba-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="92eba-118">O exemplo a seguir cria um temporizador que chama o delegado fornecido pela primeira vez após um segundo (1000 milissegundos) e, em seguida, chama a cada dois segundos.</span><span class="sxs-lookup"><span data-stu-id="92eba-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="92eba-119">O objeto de estado no exemplo é usado para contar quantas vezes o delegado é chamado.</span><span class="sxs-lookup"><span data-stu-id="92eba-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="92eba-120">O temporizador é interrompido quando o delegado é chamado pelo menos 10 vezes.</span><span class="sxs-lookup"><span data-stu-id="92eba-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="92eba-121">Para obter mais informações e exemplos, consulte <xref:System.Threading.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92eba-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="92eba-122">A classe System.Timers.Timer</span><span class="sxs-lookup"><span data-stu-id="92eba-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="92eba-123">Outro temporizador que pode ser usado em um ambiente multi-threaded é o <xref:System.Timers.Timer?displayProperty=nameWithType> que, por padrão, gera um evento em um thread <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="92eba-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="92eba-124">Ao criar um objeto <xref:System.Timers.Timer?displayProperty=nameWithType>, você pode especificar o intervalo de tempo em que um evento <xref:System.Timers.Timer.Elapsed> deve ser gerado.</span><span class="sxs-lookup"><span data-stu-id="92eba-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="92eba-125">Use a propriedade <xref:System.Timers.Timer.Enabled%2A> para indicar se um temporizador deve gerar um evento <xref:System.Timers.Timer.Elapsed>.</span><span class="sxs-lookup"><span data-stu-id="92eba-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="92eba-126">Se você precisar que um evento <xref:System.Timers.Timer.Elapsed> seja gerado apenas uma vez depois que o intervalo especificado for decorrido, defina <xref:System.Timers.Timer.AutoReset%2A> para `false`.</span><span class="sxs-lookup"><span data-stu-id="92eba-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="92eba-127">O valor padrão da propriedade <xref:System.Timers.Timer.AutoReset%2A> é `true`, o que significa que um evento <xref:System.Timers.Timer.Elapsed> é gerado regularmente no intervalo definido pela propriedade <xref:System.Timers.Timer.Interval%2A>.</span><span class="sxs-lookup"><span data-stu-id="92eba-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="92eba-128">Para obter mais informações e exemplos, consulte <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92eba-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="92eba-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92eba-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="92eba-130">Objetos e recursos de threading</span><span class="sxs-lookup"><span data-stu-id="92eba-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)

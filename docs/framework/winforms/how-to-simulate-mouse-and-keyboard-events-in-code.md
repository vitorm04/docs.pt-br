---
title: Como simular eventos de mouse e teclado no código
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboards [Windows Forms], event simulation
- user input [Windows Forms], simulating
- SendKeys [Windows Forms], using
- mouse clicks [Windows Forms], simulating
- mouse [Windows Forms], event simulation
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
ms.openlocfilehash: 9fac74aacf6b902a25438151db247a1a4aee1f4c
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802473"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a><span data-ttu-id="c8a06-102">Como simular eventos de mouse e teclado no código</span><span class="sxs-lookup"><span data-stu-id="c8a06-102">How to: Simulate Mouse and Keyboard Events in Code</span></span>

<span data-ttu-id="c8a06-103">O Windows Forms fornece várias opções para simular programaticamente entradas do mouse e do teclado.</span><span class="sxs-lookup"><span data-stu-id="c8a06-103">Windows Forms provides several options for programmatically simulating mouse and keyboard input.</span></span> <span data-ttu-id="c8a06-104">Este tópico fornece uma visão geral dessas opções.</span><span class="sxs-lookup"><span data-stu-id="c8a06-104">This topic provides an overview of these options.</span></span>

## <a name="simulating-mouse-input"></a><span data-ttu-id="c8a06-105">Simulando entrada do mouse</span><span class="sxs-lookup"><span data-stu-id="c8a06-105">Simulating Mouse Input</span></span>

<span data-ttu-id="c8a06-106">A melhor maneira de simular eventos do mouse é chamar o método `On`*EventName* que gera o evento de mouse que você deseja simular.</span><span class="sxs-lookup"><span data-stu-id="c8a06-106">The best way to simulate mouse events is to call the `On`*EventName* method that raises the mouse event you want to simulate.</span></span> <span data-ttu-id="c8a06-107">Essa opção é possível apenas dentro de controles e formulários personalizados, pois os métodos que geram eventos são protegidos e não podem ser acessados fora do controle ou do formulário.</span><span class="sxs-lookup"><span data-stu-id="c8a06-107">This option is usually possible only within custom controls and forms, because the methods that raise events are protected and cannot be accessed outside the control or form.</span></span> <span data-ttu-id="c8a06-108">Por exemplo, as etapas a seguir ilustram como simular um clique no botão direito do mouse no código.</span><span class="sxs-lookup"><span data-stu-id="c8a06-108">For example, the following steps illustrate how to simulate clicking the right mouse button in code.</span></span>

#### <a name="to-programmatically-click-the-right-mouse-button"></a><span data-ttu-id="c8a06-109">Para clicar programaticamente no botão direito do mouse</span><span class="sxs-lookup"><span data-stu-id="c8a06-109">To programmatically click the right mouse button</span></span>

1. <span data-ttu-id="c8a06-110">Crie um <xref:System.Windows.Forms.MouseEventArgs> cuja propriedade <xref:System.Windows.Forms.MouseEventArgs.Button%2A> esteja definida como o valor <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8a06-110">Create a <xref:System.Windows.Forms.MouseEventArgs> whose <xref:System.Windows.Forms.MouseEventArgs.Button%2A> property is set to the <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> value.</span></span>

2. <span data-ttu-id="c8a06-111">Chame o método <xref:System.Windows.Forms.Control.OnMouseClick%2A> com este <xref:System.Windows.Forms.MouseEventArgs> como o argumento.</span><span class="sxs-lookup"><span data-stu-id="c8a06-111">Call the <xref:System.Windows.Forms.Control.OnMouseClick%2A> method with this <xref:System.Windows.Forms.MouseEventArgs> as the argument.</span></span>

<span data-ttu-id="c8a06-112">Para obter mais informações sobre controles personalizados, consulte [Desenvolvendo Controles dos Windows Forms no Tempo de Design](./controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c8a06-112">For more information on custom controls, see [Developing Windows Forms Controls at Design Time](./controls/developing-windows-forms-controls-at-design-time.md).</span></span>

<span data-ttu-id="c8a06-113">Existem outras maneiras de simular a entrada do mouse.</span><span class="sxs-lookup"><span data-stu-id="c8a06-113">There are other ways to simulate mouse input.</span></span> <span data-ttu-id="c8a06-114">Por exemplo, você pode definir programaticamente uma propriedade de controle que representa um estado que normalmente é definido por meio de entrada do mouse (como a propriedade <xref:System.Windows.Forms.CheckBox.Checked%2A> do controle <xref:System.Windows.Forms.CheckBox>), ou você pode chamar diretamente o delegado que está anexado ao evento que você deseja simular.</span><span class="sxs-lookup"><span data-stu-id="c8a06-114">For example, you can programmatically set a control property that represents a state that is typically set through mouse input (such as the <xref:System.Windows.Forms.CheckBox.Checked%2A> property of the <xref:System.Windows.Forms.CheckBox> control), or you can directly call the delegate that is attached to the event you want to simulate.</span></span>

## <a name="simulating-keyboard-input"></a><span data-ttu-id="c8a06-115">Simulando Entrada do Teclado</span><span class="sxs-lookup"><span data-stu-id="c8a06-115">Simulating Keyboard Input</span></span>

<span data-ttu-id="c8a06-116">Embora você possa simular a entrada do teclado usando as estratégias discutidas acima para entrada do mouse, Windows Forms também fornece a classe <xref:System.Windows.Forms.SendKeys> para enviar pressionamentos de teclas para o aplicativo ativo.</span><span class="sxs-lookup"><span data-stu-id="c8a06-116">Although you can simulate keyboard input by using the strategies discussed above for mouse input, Windows Forms also provides the <xref:System.Windows.Forms.SendKeys> class for sending keystrokes to the active application.</span></span>

> [!CAUTION]
> <span data-ttu-id="c8a06-117">Se seu aplicativo for destinado ao uso internacional com uma variedade de teclados, o uso de <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> poderá gerar resultados imprevisíveis e deve ser evitado.</span><span class="sxs-lookup"><span data-stu-id="c8a06-117">If your application is intended for international use with a variety of keyboards, the use of <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> could yield unpredictable results and should be avoided.</span></span>

> [!NOTE]
> <span data-ttu-id="c8a06-118">A classe <xref:System.Windows.Forms.SendKeys> foi atualizada para o .NET Framework 3,0 para habilitar seu uso em aplicativos executados no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="c8a06-118">The <xref:System.Windows.Forms.SendKeys> class has been updated for the .NET Framework 3.0 to enable its use in applications that run on Windows Vista.</span></span> <span data-ttu-id="c8a06-119">A segurança avançada do Windows Vista (conhecida como Controle de Conta de Usuário ou UAC) impede que a implementação anterior funcione conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="c8a06-119">The enhanced security of Windows Vista (known as User Account Control or UAC) prevents the previous implementation from working as expected.</span></span>
>
> <span data-ttu-id="c8a06-120">A classe <xref:System.Windows.Forms.SendKeys> é suscetível a problemas de tempo, que alguns desenvolvedores precisavam solucionar.</span><span class="sxs-lookup"><span data-stu-id="c8a06-120">The <xref:System.Windows.Forms.SendKeys> class is susceptible to timing issues, which some developers have had to work around.</span></span> <span data-ttu-id="c8a06-121">A implementação atualizada ainda está suscetível a problemas de atraso, mas é ligeiramente mais rápida e pode exigir alterações para as soluções alternativas.</span><span class="sxs-lookup"><span data-stu-id="c8a06-121">The updated implementation is still susceptible to timing issues, but is slightly faster and may require changes to the workarounds.</span></span> <span data-ttu-id="c8a06-122">A classe <xref:System.Windows.Forms.SendKeys> tenta usar a implementação anterior primeiro e, se isso falhar, usará a nova implementação.</span><span class="sxs-lookup"><span data-stu-id="c8a06-122">The <xref:System.Windows.Forms.SendKeys> class tries to use the previous implementation first, and if that fails, uses the new implementation.</span></span> <span data-ttu-id="c8a06-123">Como resultado, a classe <xref:System.Windows.Forms.SendKeys> pode se comportar de forma diferente em sistemas operacionais diferentes.</span><span class="sxs-lookup"><span data-stu-id="c8a06-123">As a result, the <xref:System.Windows.Forms.SendKeys> class may behave differently on different operating systems.</span></span> <span data-ttu-id="c8a06-124">Além disso, quando a classe <xref:System.Windows.Forms.SendKeys> usa a nova implementação, o método <xref:System.Windows.Forms.SendKeys.SendWait%2A> não aguardará que as mensagens sejam processadas quando forem enviadas a outro processo.</span><span class="sxs-lookup"><span data-stu-id="c8a06-124">Additionally, when the <xref:System.Windows.Forms.SendKeys> class uses the new implementation, the <xref:System.Windows.Forms.SendKeys.SendWait%2A> method will not wait for messages to be processed when they are sent to another process.</span></span>
>
> <span data-ttu-id="c8a06-125">Se seu aplicativo depender de um comportamento consistente independentemente do sistema operacional, você poderá forçar a classe de <xref:System.Windows.Forms.SendKeys> a usar a nova implementação adicionando a seguinte configuração de aplicativo ao seu arquivo app. config.</span><span class="sxs-lookup"><span data-stu-id="c8a06-125">If your application relies on consistent behavior regardless of the operating system, you can force the <xref:System.Windows.Forms.SendKeys> class to use the new implementation by adding the following application setting to your app.config file.</span></span>
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> <span data-ttu-id="c8a06-126">Para forçar a classe de <xref:System.Windows.Forms.SendKeys> a usar a implementação anterior, use o valor `"JournalHook"` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c8a06-126">To force the <xref:System.Windows.Forms.SendKeys> class to use the previous implementation, use the value `"JournalHook"` instead.</span></span>

#### <a name="to-send-a-keystroke-to-the-same-application"></a><span data-ttu-id="c8a06-127">Para enviar um pressionamento de tecla para o mesmo aplicativo</span><span class="sxs-lookup"><span data-stu-id="c8a06-127">To send a keystroke to the same application</span></span>

1. <span data-ttu-id="c8a06-128">Chame o método <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A> da classe <xref:System.Windows.Forms.SendKeys>.</span><span class="sxs-lookup"><span data-stu-id="c8a06-128">Call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method of the <xref:System.Windows.Forms.SendKeys> class.</span></span> <span data-ttu-id="c8a06-129">Os pressionamentos de teclas especificados serão recebidos pelo controle ativo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8a06-129">The specified keystrokes will be received by the active control of the application.</span></span> <span data-ttu-id="c8a06-130">O exemplo de código a seguir usa <xref:System.Windows.Forms.SendKeys.Send%2A> para simular o pressionamento da tecla ENTER quando o usuário clica duas vezes na superfície do formulário.</span><span class="sxs-lookup"><span data-stu-id="c8a06-130">The following code example uses <xref:System.Windows.Forms.SendKeys.Send%2A> to simulate pressing the ENTER key when the user double-clicks the surface of the form.</span></span> <span data-ttu-id="c8a06-131">Este exemplo pressupõe um <xref:System.Windows.Forms.Form> com um único controle de <xref:System.Windows.Forms.Button> que tem um índice de tabulação de 0.</span><span class="sxs-lookup"><span data-stu-id="c8a06-131">This example assumes a <xref:System.Windows.Forms.Form> with a single <xref:System.Windows.Forms.Button> control that has a tab index of 0.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a><span data-ttu-id="c8a06-132">Para enviar um pressionamento de tecla para um aplicativo diferente</span><span class="sxs-lookup"><span data-stu-id="c8a06-132">To send a keystroke to a different application</span></span>

1. <span data-ttu-id="c8a06-133">Ative a janela do aplicativo que receberá os pressionamentos de tecla e, em seguida, chame o método <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8a06-133">Activate the application window that will receive the keystrokes, and then call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method.</span></span> <span data-ttu-id="c8a06-134">Como não há nenhum método gerenciado para ativar outro aplicativo, você deve usar métodos nativos do Windows para forçar foco em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c8a06-134">Because there is no managed method to activate another application, you must use native Windows methods to force focus on other applications.</span></span> <span data-ttu-id="c8a06-135">O exemplo de código a seguir usa a invocação de plataforma para chamar os métodos `FindWindow` e `SetForegroundWindow` para ativar a janela do aplicativo de calculadora e, em seguida, chama <xref:System.Windows.Forms.SendKeys.SendWait%2A> para emitir uma série de cálculos para o aplicativo de calculadora.</span><span class="sxs-lookup"><span data-stu-id="c8a06-135">The following code example uses platform invoke to call the `FindWindow` and `SetForegroundWindow` methods to activate the Calculator application window, and then calls <xref:System.Windows.Forms.SendKeys.SendWait%2A> to issue a series of calculations to the Calculator application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c8a06-136">Os parâmetros corretos da chamada `FindWindow` que localiza o aplicativo Calculadora variam de acordo com sua versão do Windows.</span><span class="sxs-lookup"><span data-stu-id="c8a06-136">The correct parameters of the `FindWindow` call that locates the Calculator application vary based on your version of Windows.</span></span>  <span data-ttu-id="c8a06-137">O código a seguir encontra o aplicativo de calculadora no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="c8a06-137">The following code finds the Calculator application on Windows 7.</span></span> <span data-ttu-id="c8a06-138">Em [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], altere o primeiro parâmetro para "SciCalc".</span><span class="sxs-lookup"><span data-stu-id="c8a06-138">On [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], change the first parameter to "SciCalc".</span></span> <span data-ttu-id="c8a06-139">Você pode usar a ferramenta Spy++, incluída no Visual Studio, para determinar os parâmetros corretos.</span><span class="sxs-lookup"><span data-stu-id="c8a06-139">You can use the Spy++ tool, included with Visual Studio, to determine the correct parameters.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a><span data-ttu-id="c8a06-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8a06-140">Example</span></span>

<span data-ttu-id="c8a06-141">O exemplo de código a seguir é o aplicativo completo para os exemplos de código anteriores.</span><span class="sxs-lookup"><span data-stu-id="c8a06-141">The following code example is the complete application for the previous code examples.</span></span>

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="c8a06-142">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="c8a06-142">Compiling the Code</span></span>

<span data-ttu-id="c8a06-143">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c8a06-143">This example requires:</span></span>

- <span data-ttu-id="c8a06-144">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="c8a06-144">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8a06-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8a06-145">See also</span></span>

- [<span data-ttu-id="c8a06-146">Entrada do usuário nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8a06-146">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)

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
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Como simular eventos de mouse e teclado no código

O Windows Forms fornece várias opções para simular programaticamente entradas do mouse e do teclado. Este tópico fornece uma visão geral dessas opções.

## <a name="simulating-mouse-input"></a>Simulando entrada do mouse

A melhor maneira de simular eventos do mouse é chamar o método `On`*EventName* que gera o evento de mouse que você deseja simular. Essa opção é possível apenas dentro de controles e formulários personalizados, pois os métodos que geram eventos são protegidos e não podem ser acessados fora do controle ou do formulário. Por exemplo, as etapas a seguir ilustram como simular um clique no botão direito do mouse no código.

#### <a name="to-programmatically-click-the-right-mouse-button"></a>Para clicar programaticamente no botão direito do mouse

1. Crie um <xref:System.Windows.Forms.MouseEventArgs> cuja propriedade <xref:System.Windows.Forms.MouseEventArgs.Button%2A> esteja definida como o valor <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType>.

2. Chame o método <xref:System.Windows.Forms.Control.OnMouseClick%2A> com este <xref:System.Windows.Forms.MouseEventArgs> como o argumento.

Para obter mais informações sobre controles personalizados, consulte [Desenvolvendo Controles dos Windows Forms no Tempo de Design](./controls/developing-windows-forms-controls-at-design-time.md).

Existem outras maneiras de simular a entrada do mouse. Por exemplo, você pode definir programaticamente uma propriedade de controle que representa um estado que normalmente é definido por meio de entrada do mouse (como a propriedade <xref:System.Windows.Forms.CheckBox.Checked%2A> do controle <xref:System.Windows.Forms.CheckBox>), ou você pode chamar diretamente o delegado que está anexado ao evento que você deseja simular.

## <a name="simulating-keyboard-input"></a>Simulando Entrada do Teclado

Embora você possa simular a entrada do teclado usando as estratégias discutidas acima para entrada do mouse, Windows Forms também fornece a classe <xref:System.Windows.Forms.SendKeys> para enviar pressionamentos de teclas para o aplicativo ativo.

> [!CAUTION]
> Se seu aplicativo for destinado ao uso internacional com uma variedade de teclados, o uso de <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> poderá gerar resultados imprevisíveis e deve ser evitado.

> [!NOTE]
> A classe <xref:System.Windows.Forms.SendKeys> foi atualizada para o .NET Framework 3,0 para habilitar seu uso em aplicativos executados no Windows Vista. A segurança avançada do Windows Vista (conhecida como Controle de Conta de Usuário ou UAC) impede que a implementação anterior funcione conforme o esperado.
>
> A classe <xref:System.Windows.Forms.SendKeys> é suscetível a problemas de tempo, que alguns desenvolvedores precisavam solucionar. A implementação atualizada ainda está suscetível a problemas de atraso, mas é ligeiramente mais rápida e pode exigir alterações para as soluções alternativas. A classe <xref:System.Windows.Forms.SendKeys> tenta usar a implementação anterior primeiro e, se isso falhar, usará a nova implementação. Como resultado, a classe <xref:System.Windows.Forms.SendKeys> pode se comportar de forma diferente em sistemas operacionais diferentes. Além disso, quando a classe <xref:System.Windows.Forms.SendKeys> usa a nova implementação, o método <xref:System.Windows.Forms.SendKeys.SendWait%2A> não aguardará que as mensagens sejam processadas quando forem enviadas a outro processo.
>
> Se seu aplicativo depender de um comportamento consistente independentemente do sistema operacional, você poderá forçar a classe de <xref:System.Windows.Forms.SendKeys> a usar a nova implementação adicionando a seguinte configuração de aplicativo ao seu arquivo app. config.
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> Para forçar a classe de <xref:System.Windows.Forms.SendKeys> a usar a implementação anterior, use o valor `"JournalHook"` em vez disso.

#### <a name="to-send-a-keystroke-to-the-same-application"></a>Para enviar um pressionamento de tecla para o mesmo aplicativo

1. Chame o método <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A> da classe <xref:System.Windows.Forms.SendKeys>. Os pressionamentos de teclas especificados serão recebidos pelo controle ativo do aplicativo. O exemplo de código a seguir usa <xref:System.Windows.Forms.SendKeys.Send%2A> para simular o pressionamento da tecla ENTER quando o usuário clica duas vezes na superfície do formulário. Este exemplo pressupõe um <xref:System.Windows.Forms.Form> com um único controle de <xref:System.Windows.Forms.Button> que tem um índice de tabulação de 0.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a>Para enviar um pressionamento de tecla para um aplicativo diferente

1. Ative a janela do aplicativo que receberá os pressionamentos de tecla e, em seguida, chame o método <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A>. Como não há nenhum método gerenciado para ativar outro aplicativo, você deve usar métodos nativos do Windows para forçar foco em outros aplicativos. O exemplo de código a seguir usa a invocação de plataforma para chamar os métodos `FindWindow` e `SetForegroundWindow` para ativar a janela do aplicativo de calculadora e, em seguida, chama <xref:System.Windows.Forms.SendKeys.SendWait%2A> para emitir uma série de cálculos para o aplicativo de calculadora.

    > [!NOTE]
    > Os parâmetros corretos da chamada `FindWindow` que localiza o aplicativo Calculadora variam de acordo com sua versão do Windows.  O código a seguir encontra o aplicativo de calculadora no Windows 7. Em [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], altere o primeiro parâmetro para "SciCalc". Você pode usar a ferramenta Spy++, incluída no Visual Studio, para determinar os parâmetros corretos.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a>Exemplo

O exemplo de código a seguir é o aplicativo completo para os exemplos de código anteriores.

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a>Compilando o Código

Este exemplo requer:

- Referências aos assemblies System, System.Drawing e System.Windows.Forms.

## <a name="see-also"></a>Consulte também

- [Entrada do usuário nos Windows Forms](user-input-in-windows-forms.md)

---
title: 'Como: simular eventos de mouse e teclado no código'
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
ms.openlocfilehash: 1a7a0fa6295cd8332313a983ca78345bfbac393e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046392"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Como: simular eventos de mouse e teclado no código

O Windows Forms fornece várias opções para simular programaticamente entradas do mouse e do teclado. Este tópico fornece uma visão geral dessas opções.

## <a name="simulating-mouse-input"></a>Simulando entrada do mouse

A melhor maneira de simular eventos do mouse é chamar o método `On`*EventName* que gera o evento de mouse que você deseja simular. Essa opção é possível apenas dentro de controles e formulários personalizados, pois os métodos que geram eventos são protegidos e não podem ser acessados fora do controle ou do formulário. Por exemplo, as etapas a seguir ilustram como simular um clique no botão direito do mouse no código.

#### <a name="to-programmatically-click-the-right-mouse-button"></a>Para clicar programaticamente no botão direito do mouse

1. Crie uma <xref:System.Windows.Forms.MouseEventArgs> cuja <xref:System.Windows.Forms.MouseEventArgs.Button%2A> Propriedade seja definida como o <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> valor.

2. Chame o <xref:System.Windows.Forms.Control.OnMouseClick%2A> método com isso <xref:System.Windows.Forms.MouseEventArgs> como o argumento.

Para obter mais informações sobre controles personalizados, consulte [Desenvolvendo Controles dos Windows Forms no Tempo de Design](./controls/developing-windows-forms-controls-at-design-time.md).

Existem outras maneiras de simular a entrada do mouse. Por exemplo, você pode definir programaticamente uma propriedade <xref:System.Windows.Forms.CheckBox.Checked%2A> <xref:System.Windows.Forms.CheckBox> de controle que representa um estado que normalmente é definido por meio de entrada do mouse (como a propriedade do controle), ou você pode chamar diretamente o delegado que está anexado ao evento que você deseja simular.

## <a name="simulating-keyboard-input"></a>Simulando Entrada do Teclado

Embora você possa simular a entrada do teclado usando as estratégias discutidas acima para entrada do mouse, <xref:System.Windows.Forms.SendKeys> Windows Forms também fornece a classe para enviar pressionamentos de teclas para o aplicativo ativo.

> [!CAUTION]
> Se seu aplicativo for destinado ao uso internacional com uma variedade de teclados, o uso do <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> pode gerar resultados imprevisíveis e deve ser evitado.

> [!NOTE]
> A <xref:System.Windows.Forms.SendKeys> classe foi atualizada para o .NET Framework 3,0 para habilitar seu uso em aplicativos executados no Windows Vista. A segurança avançada do Windows Vista (conhecida como Controle de Conta de Usuário ou UAC) impede que a implementação anterior funcione conforme o esperado.
>
> A <xref:System.Windows.Forms.SendKeys> classe é suscetível a problemas de tempo, que alguns desenvolvedores precisavam solucionar. A implementação atualizada ainda está suscetível a problemas de atraso, mas é ligeiramente mais rápida e pode exigir alterações para as soluções alternativas. A <xref:System.Windows.Forms.SendKeys> classe tenta usar a implementação anterior primeiro e, se isso falhar, usará a nova implementação. Como resultado, a <xref:System.Windows.Forms.SendKeys> classe pode se comportar de forma diferente em sistemas operacionais diferentes. Além disso, quando <xref:System.Windows.Forms.SendKeys> a classe usa a nova implementação, <xref:System.Windows.Forms.SendKeys.SendWait%2A> o método não aguardará que as mensagens sejam processadas quando forem enviadas a outro processo.
>
> Se seu aplicativo depende de um comportamento consistente independentemente do sistema operacional, você pode forçar a <xref:System.Windows.Forms.SendKeys> classe a usar a nova implementação adicionando a seguinte configuração de aplicativo ao seu arquivo app. config.
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> Para forçar a <xref:System.Windows.Forms.SendKeys> aula a usar a implementação anterior, use o valor `"JournalHook"` em vez disso.

#### <a name="to-send-a-keystroke-to-the-same-application"></a>Para enviar um pressionamento de tecla para o mesmo aplicativo

1. Chame o <xref:System.Windows.Forms.SendKeys.Send%2A> método <xref:System.Windows.Forms.SendKeys.SendWait%2A> ou da <xref:System.Windows.Forms.SendKeys> classe. Os pressionamentos de teclas especificados serão recebidos pelo controle ativo do aplicativo. O exemplo de código a <xref:System.Windows.Forms.SendKeys.Send%2A> seguir usa para simular o pressionamento da tecla Enter quando o usuário clica duas vezes na superfície do formulário. Este exemplo pressupõe um <xref:System.Windows.Forms.Form> com um único <xref:System.Windows.Forms.Button> controle que tem um índice de tabulação de 0.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a>Para enviar um pressionamento de tecla para um aplicativo diferente

1. Ative a janela do aplicativo que receberá os pressionamentos de tecla e, em <xref:System.Windows.Forms.SendKeys.Send%2A> seguida <xref:System.Windows.Forms.SendKeys.SendWait%2A> , chame o método ou. Como não há nenhum método gerenciado para ativar outro aplicativo, você deve usar métodos nativos do Windows para forçar foco em outros aplicativos. O exemplo de código a seguir usa a invocação `FindWindow` de `SetForegroundWindow` plataforma para chamar os métodos e para ativar a janela do <xref:System.Windows.Forms.SendKeys.SendWait%2A> aplicativo de calculadora e, em seguida, chama para emitir uma série de cálculos para o aplicativo de calculadora.

    > [!NOTE]
    > Os parâmetros corretos da chamada `FindWindow` que localiza o aplicativo Calculadora variam de acordo com sua versão do Windows.  O código a seguir localiza o aplicativo Calculadora em [!INCLUDE[win7](../../../includes/win7-md.md)]. Em [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], altere o primeiro parâmetro para "SciCalc". Você pode usar a ferramenta Spy++, incluída no Visual Studio, para determinar os parâmetros corretos.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a>Exemplo

O exemplo de código a seguir é o aplicativo completo para os exemplos de código anteriores.

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

- Referências aos assemblies System, System.Drawing e System.Windows.Forms.

## <a name="see-also"></a>Consulte também

- [Entrada do usuário nos Windows Forms](user-input-in-windows-forms.md)

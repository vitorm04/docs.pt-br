---
title: Estendendo o modelo de aplicativo do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 02a964506d976cb10f3f28f83f0655fecc447e59
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582757"
---
# <a name="extending-the-visual-basic-application-model"></a>Estendendo o modelo de aplicativo do Visual Basic

Você pode adicionar funcionalidade ao modelo de aplicativo substituindo os membros de `Overridable` da classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Essa técnica permite que você personalize o comportamento do modelo de aplicativo e adicione chamadas para seus próprios métodos à medida que o aplicativo é iniciado e desligado.

## <a name="visual-overview-of-the-application-model"></a>Visão geral visual do modelo de aplicativo

Esta seção apresenta visualmente a sequência de chamadas de função no modelo de aplicativo Visual Basic. A próxima seção descreve a finalidade de cada função em detalhes.

O gráfico a seguir mostra a sequência de chamada de modelo de aplicativo em um aplicativo Visual Basic normal Windows Forms. A sequência é iniciada quando o procedimento de `Sub Main` chama o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.

![Diagrama mostrando a sequência de chamada de modelo de aplicativo.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)

O modelo de aplicativo Visual Basic também fornece os eventos <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> e <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>. Os gráficos a seguir mostram o mecanismo para gerar esses eventos.

![Diagrama que mostra o método OnStartupNextInstance que gera o evento StartupNextInstance.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)

![Diagrama que mostra o método OnUnhandledException que gera o evento UnhandledException.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)

## <a name="overriding-the-base-methods"></a>Substituindo os métodos base

O método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> define a ordem na qual os métodos de `Application` são executados. Por padrão, o procedimento de `Sub Main` para um aplicativo Windows Forms chama o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.

Se o aplicativo for um aplicativo normal (aplicativo de várias instâncias) ou a primeira instância de um aplicativo de instância única, o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> executará os métodos `Overridable` na seguinte ordem:

1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Por padrão, esse método define os estilos visuais, os estilos de exibição de texto e a entidade de segurança atual para o thread do aplicativo principal (se o aplicativo usa a autenticação do Windows) e chama `ShowSplashScreen` se nem `/nosplash` nem `-nosplash` é usado como um argumento de linha de comando.

     A sequência de inicialização do aplicativo será cancelada se essa função retornar `False`. Isso pode ser útil se houver circunstâncias em que o aplicativo não deve ser executado.

     O método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> chama os seguintes métodos:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Determina se o aplicativo tem uma tela inicial definida e, se tiver, exibe a tela inicial em um thread separado.

         O método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> contém o código que exibe a tela inicial de pelo menos o número de milissegundos especificado pela propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>. Para usar essa funcionalidade, você deve adicionar a tela inicial ao seu aplicativo usando o **Designer de projeto** (que define a propriedade `My.Application.MinimumSplashScreenDisplayTime` como dois segundos) ou definir a propriedade `My.Application.MinimumSplashScreenDisplayTime` em um método que substitui o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> ou <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> Permite que um designer Emita código que inicializa a tela inicial.

         Por padrão, esse método não faz nada. Se você selecionar uma tela inicial para seu aplicativo na Visual Basic **Designer de projeto**, o designer substituirá o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> por um método que define a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> como uma nova instância do formulário da tela inicial.

2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A> Fornece um ponto de extensibilidade para gerar o evento de `Startup`. A sequência de inicialização do aplicativo será interrompida se essa função retornar `False`.

     Por padrão, esse método gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>. Se o manipulador de eventos definir a propriedade <xref:System.ComponentModel.CancelEventArgs.Cancel> do argumento de evento como `True`, o método retornará `False` para cancelar a inicialização do aplicativo.

3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A> Fornece o ponto de partida para quando o aplicativo principal está pronto para começar a ser executado, após a inicialização ser feita.

     Por padrão, antes de entrar no loop de mensagem de Windows Forms, esse método chama o `OnCreateMainForm` (para criar o formulário principal do aplicativo) e `HideSplashScreen` (para fechar a tela inicial) métodos:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> Fornece uma maneira para um designer emitir código que inicializa o formulário principal.

         Por padrão, esse método não faz nada. No entanto, quando você seleciona um formulário principal para seu aplicativo na Visual Basic **Designer de projeto**, o designer substitui o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> por um método que define a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> como uma nova instância do formulário principal.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A> Se o aplicativo tiver uma tela inicial definida e estiver aberto, esse método fechará a tela inicial.

         Por padrão, esse método fecha a tela inicial.

4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> Fornece uma maneira de personalizar como um aplicativo de instância única se comporta quando outra instância do aplicativo é iniciada.

     Por padrão, esse método gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>.

5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A> Fornece um ponto de extensibilidade para gerar o evento de `Shutdown`. Esse método não será executado se ocorrer uma exceção sem tratamento no aplicativo principal.

     Por padrão, esse método gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>.

6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A> Executado se uma exceção sem tratamento ocorrer em qualquer um dos métodos listados acima.

     Por padrão, esse método gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>, desde que um depurador não esteja anexado e o aplicativo esteja manipulando o evento `UnhandledException`.

 Se o aplicativo for um aplicativo de instância única e o aplicativo já estiver em execução, a instância subsequente do aplicativo chamará o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> na instância original do aplicativo e, em seguida, será encerrada.

 O construtor de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> chama a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> para determinar qual mecanismo de renderização de texto a ser usado para os formulários do aplicativo. Por padrão, a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> retorna `False`, indicando que o mecanismo de renderização de texto GDI será usado, que é o padrão no Visual Basic 2005 e versões posteriores. Você pode substituir a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> para retornar `True`, que indica que o mecanismo de renderização de texto do GDI+ deve ser usado, que é o padrão em Visual Basic .NET 2002 e Visual Basic .NET 2003.

## <a name="configuring-the-application"></a>Configurando o aplicativo
 Como parte do modelo de aplicativo Visual Basic, a classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> fornece propriedades protegidas que configuram o aplicativo. Essas propriedades devem ser definidas no construtor da classe de implementação.

 Em um projeto de Windows Forms padrão, o **Designer de projeto** cria o código para definir as propriedades com as configurações de designer. As propriedades são usadas somente quando o aplicativo está sendo iniciado; configurá-los depois que o aplicativo é iniciado não tem nenhum efeito.

|propriedade|Verifica|Configuração no painel de aplicativo do designer de projeto|
|---|---|---|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Se o aplicativo é executado como um aplicativo de instância única ou de várias instâncias.|Caixa de seleção **criar aplicativo de instância única**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Se o aplicativo usar estilos visuais que correspondam ao Windows XP.|Caixa de seleção **Habilitar estilos visuais do XP**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Se o aplicativo salvar automaticamente as alterações de configurações de usuário do aplicativo quando o aplicativo for encerrado.|Caixa **de seleção Salvar My. Settings na desligamento**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|O que faz com que o aplicativo seja encerrado, como quando o formulário de inicialização é fechado ou quando o último formulário é fechado.|Lista de **modo de desligamento**|

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Visão geral do modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Página de Aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)

---
title: Estendendo o modelo de aplicativo do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 6ba3f29ad0ceef7f1ea9d102743df568a32c26c8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320139"
---
# <a name="extending-the-visual-basic-application-model"></a>Estendendo o modelo de aplicativo do Visual Basic
Você pode adicionar funcionalidade ao modelo de aplicativo, substituindo o `Overridable` os membros de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> classe. Essa técnica permite que você personalize o comportamento do modelo de aplicativo e adicionar chamadas para seus próprios métodos quando o aplicativo é inicializado e desligado.  
  
## <a name="visual-overview-of-the-application-model"></a>Visão geral do modelo de aplicativo  
 Esta seção apresenta visualmente a sequência de chamadas de função no modelo de aplicativo do Visual Basic. A próxima seção descreve a finalidade de cada função em detalhes.  
  
 O gráfico a seguir mostra a sequência de chamadas de modelo de aplicativo em um aplicativo de formulários do Windows Visual Basic normal. A sequência começa quando o `Sub Main` chamadas de procedimento o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> método.  
  
 ![Diagrama que mostra a sequência de chamadas de modelo de aplicativo.](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)  
  
 O modelo de aplicativo do Visual Basic também fornece o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> e <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> eventos. Os gráficos a seguir mostram o mecanismo para acionar esses eventos.  
  
 ![Diagrama que mostra o método OnStartupNextInstance acionar o evento StartupNextInstance.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)  
  
 ![Diagrama que mostra o método OnUnhandledException acionar o evento UnhandledException.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)  
  
## <a name="overriding-the-base-methods"></a>Substituindo os métodos Base  
 O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> método define a ordem na qual o `Application` métodos executados. Por padrão, o `Sub Main` chamadas de procedimento para um aplicativo Windows Forms a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> método.  
  
 Se o aplicativo é um aplicativo normal (aplicativo de várias instâncias) ou a primeira instância de um aplicativo de instância única, o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> método executa o `Overridable` métodos na seguinte ordem:  
  
1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Por padrão, esse método define os estilos visuais, estilos de exibição de texto e a entidade de segurança atual para o thread principal do aplicativo (se o aplicativo usa a autenticação do Windows) e chama `ShowSplashScreen` se nem `/nosplash` nem `-nosplash` é usado como um argumento de linha de comando.  
  
     A sequência de inicialização do aplicativo será cancelada se essa função retorna `False`. Isso pode ser útil se há circunstâncias em que o aplicativo não deve executar.  
  
     O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> método chama os métodos a seguir:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Determina se o aplicativo tem uma tela inicial definida e, em caso afirmativo, exibe a tela inicial em um thread separado.  
  
         O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> método contém o código que exibe na tela inicial de tela para pelo menos o número de milissegundos especificado pelo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> propriedade. Para usar essa funcionalidade, você deve adicionar a tela inicial para seu aplicativo usando o **Designer de projeto** (que define o `My.Application.MinimumSplashScreenDisplayTime` propriedade como dois segundos), ou defina o `My.Application.MinimumSplashScreenDisplayTime` propriedade em um método que substitui o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> ou <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> método. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Permite que um designer emita o código que inicializa a tela inicial.  
  
         Por padrão, esse método não fará nada. Se você selecionar uma tela inicial para seu aplicativo no Visual Basic **Designer de projeto**, o designer substitui o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> método com um método que define o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> propriedade para uma nova instância do formulário de tela inicial .  
  
2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Fornece um ponto de extensibilidade para disparar o `Startup` eventos. A sequência de inicialização do aplicativo para se essa função retorna `False`.  
  
     Por padrão, esse método dispara o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> eventos. Se o manipulador de eventos define o <xref:System.ComponentModel.CancelEventArgs.Cancel> propriedade do argumento do evento para `True`, o método retorna `False` para cancelar a inicialização do aplicativo.  
  
3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Fornece o ponto de partida para quando o aplicativo principal está pronto para começar a ser executado, após a inicialização ser feita.  
  
     Por padrão, antes de entrar no loop de mensagem do Windows Forms, este método chama o `OnCreateMainForm` (para criar o formulário principal do aplicativo) e `HideSplashScreen` (para fechar a tela inicial) métodos:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Fornece uma maneira para um designer emita o código que inicializa o formulário principal.  
  
         Por padrão, esse método não fará nada. No entanto, quando você seleciona um formulário principal para o seu aplicativo no Visual Basic **Designer de projeto**, o designer substitui o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> método com um método que define o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> propriedade para uma nova instância do formulário principal.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Se o aplicativo tem uma tela inicial definida e ele estiver aberto, esse método fecha a tela inicial.  
  
         Por padrão, esse método fecha a tela inicial.  
  
4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Fornece uma maneira de personalizar como um aplicativo de instância única se comporta quando outra instância do aplicativo é iniciado.  
  
     Por padrão, esse método dispara o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> eventos.  
  
5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Fornece um ponto de extensibilidade para disparar o `Shutdown` eventos. Esse método não será executado se ocorrer uma exceção sem tratamento no aplicativo principal.  
  
     Por padrão, esse método dispara o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> eventos.  
  
6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Executado se uma exceção não tratada ocorrer em qualquer um dos métodos listados acima.  
  
     Por padrão, esse método dispara a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> evento, desde que um depurador não está anexado e o aplicativo está manuseando o `UnhandledException` eventos.  
  
 Se o aplicativo é um aplicativo de instância única e o aplicativo já está em execução, a instância subsequente do aplicativo chama o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> método na instância original do aplicativo e, em seguida, sai.  
 
 O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> construtor chama o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> propriedade para determinar qual mecanismo de renderização de texto a ser usado para formulários do aplicativo. Por padrão, o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> propriedade retorna `False`, indicando que o mecanismo de renderização de texto GDI usados, que é o padrão em [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]. Você pode substituir a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> propriedade para retornar `True`, indicando que o mecanismo de renderização de texto GDI+ ser usada, que é o padrão no Visual Basic .NET 2002 e Visual Basic .NET 2003.  
  
## <a name="configuring-the-application"></a>Configurando o aplicativo  
 Como parte do modelo de aplicativo do Visual Basic, o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering> classe fornece propriedades protegidas que configuram o aplicativo. Essas propriedades devem ser definidas no construtor da classe de implementação.  
  
 Em um projeto do Windows Forms, o **Designer de projeto** cria código para definir as propriedades com as configurações de designer. As propriedades são usadas somente quando o aplicativo está sendo iniciado; defini-los depois que o aplicativo é iniciado não tem nenhum efeito.  
  
|Propriedade|Determina|Configuração no painel Application do Project Designer|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Se o aplicativo é executado como um aplicativo de instância única ou várias instâncias.|**Tornar o aplicativo de instância única** caixa de seleção|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Se o aplicativo usará estilos visuais que correspondem ao Windows XP.|**Habilitar estilos visuais XP** caixa de seleção|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Se o aplicativo salva automaticamente as alterações de configurações do usuário do aplicativo quando o aplicativo é encerrado.|**Salvar My. Settings no desligamento** caixa de seleção|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|O que faz com que o aplicativo seja finalizado, como quando fecha o formulário de inicialização ou quando o último formulário fecha.|**Modo de desligamento** lista|  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Visão geral do modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Página de Aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)

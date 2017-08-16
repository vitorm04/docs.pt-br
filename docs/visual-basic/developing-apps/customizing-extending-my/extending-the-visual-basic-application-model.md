---
title: Estendendo o modelo de aplicativo do Visual Basic | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9752cdfa79d3db4c8b07daa95aea2c842e06cc36
ms.lasthandoff: 03/13/2017

---
# <a name="extending-the-visual-basic-application-model"></a>Estendendo o modelo de aplicativo do Visual Basic
Você pode adicionar funcionalidade ao modelo de aplicativo, substituindo o `Overridable` membros de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>classe.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Essa técnica permite que você personalize o comportamento do modelo de aplicativo e adicionar chamadas para seus próprios métodos quando o aplicativo é iniciado e desligado.  
  
## <a name="visual-overview-of-the-application-model"></a>Visão geral do modelo de aplicativo  
 Esta seção visualmente apresenta a sequência de chamadas de função no modelo de aplicativo do Visual Basic. A próxima seção descreve a finalidade de cada função em detalhes.  
  
 O gráfico a seguir mostra a sequência de chamadas de modelo de aplicativo em um aplicativo Visual Basic Windows Forms normal. A sequência começa quando o `Sub Main` chamadas de procedimento o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>método.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>  
  
 ![Modelo de aplicativo do Visual Basic-- Executar](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelrun.gif "VB_ModelRun")  
  
 O modelo de aplicativo do Visual Basic também fornece o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>e <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>eventos.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> Os gráficos a seguir mostram o mecanismo para disparar esses eventos.  
  
 ![Modelo de aplicativo do Visual Basic-- Próxima instância](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelnext.gif "VB_ModelNext")  
  
 ![Exceção sem tratamento do modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_unhandex.gif "VB_UnhandEx")  
  
## <a name="overriding-the-base-methods"></a>Substituindo os métodos Base  
 O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>método define a ordem na qual o `Application` métodos executados.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Por padrão, o `Sub Main` procedimento para um aplicativo Windows Forms chama o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>método.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>  
  
 Se o aplicativo for um aplicativo normal (aplicativo de múltiplas instâncias), ou a primeira instância de um aplicativo de instância única, o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>método executa a `Overridable` métodos na seguinte ordem:</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>  
  
1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Por padrão, esse método define os estilos visuais, estilos de exibição de texto e a entidade de segurança atual para o segmento de aplicativo principal (se o aplicativo usa autenticação do Windows) e chama `ShowSplashScreen` se nem `/nosplash` nem `-nosplash` é usado como um argumento de linha de comando.  
  
     A sequência de inicialização do aplicativo será cancelada se esta função retornará `False`. Isso pode ser útil se houver circunstâncias em que o aplicativo não deve executar.  
  
     O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>método chama os métodos a seguir:</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Determina se o aplicativo tem um tela inicial definidas e se tiver, exibe a tela inicial em um thread separado.  
  
         O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>método contém o código que exibe na tela inicial da tela pelo menos o número de milissegundos especificado pelo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>propriedade.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Para usar essa funcionalidade, você deve adicionar a tela inicial para seu aplicativo usando o **Project Designer** (que define o `My.Application.MinimumSplashScreenDisplayTime` propriedade como dois segundos), ou defina o `My.Application.MinimumSplashScreenDisplayTime` propriedade em um método que substitui o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>ou <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>método.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> Permite que um designer emita código que inicializa a tela inicial.  
  
         Por padrão, esse método não fará nada. Se você selecionar uma tela inicial para seu aplicativo no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Project Designer**, o designer substitui o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>método com um método que define o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>propriedade para uma nova instância do formulário da tela inicial.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A> Fornece um ponto de extensibilidade para disparar o `Startup` evento. A sequência de inicialização do aplicativo para se essa função retornar `False`.  
  
     Por padrão, esse método dispara o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>evento.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> Se o manipulador de eventos define o @System.ComponentModel.CancelEventArgs.Cancel propriedade do argumento do evento para `True`, o método retorna `False` para cancelar a inicialização do aplicativo.  
  
3.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A> Fornece o ponto de partida para quando o aplicativo principal está pronto para começar a ser executado, após a inicialização ser feita.  
  
     Por padrão, antes de entrar no loop de mensagem do Windows Forms, este método chama o `OnCreateMainForm` (para criar o formulário principal do aplicativo) e `HideSplashScreen` (para fechar a tela inicial) métodos:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> Fornece uma maneira para um designer emitir código que inicializa o formulário principal.  
  
         Por padrão, esse método não fará nada. No entanto, quando você seleciona um formulário principal do aplicativo no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Project Designer**, o designer substitui o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>método com um método que define o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>propriedade para uma nova instância do formulário principal.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A> Se o aplicativo tem uma tela inicial definida e ela estiver aberta, este método fecha a tela inicial.  
  
         Por padrão, esse método fecha a tela inicial.  
  
4.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> Fornece uma maneira de personalizar como um aplicativo de instância única se comporta quando outra instância do aplicativo é iniciado.  
  
     Por padrão, esse método dispara o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>evento.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
  
5.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A> Fornece um ponto de extensibilidade para disparar o `Shutdown` evento. Esse método não é executado se uma exceção não tratada ocorrer no aplicativo principal.  
  
     Por padrão, esse método dispara o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>evento.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
  
6.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A> Executado se uma exceção não tratada ocorrer em qualquer um dos métodos listados acima.  
  
     Por padrão, esse método dispara o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>evento, desde que um depurador não está anexado e o aplicativo está manuseando o `UnhandledException` evento.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
  
 Se o aplicativo é um aplicativo de instância única, e o aplicativo já está em execução, a instância subsequente do aplicativo chama o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>método na instância original do aplicativo e, em seguida, sai.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>  
  
 O <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>construtor chama o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>para determinar qual mecanismo de renderização de texto a ser usado para formulários do aplicativo.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Por padrão, o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>propriedade retorna `False`, indicando que o mecanismo de renderização de texto GDI será usado, que é o padrão em [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)].</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> Você pode substituir o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>propriedade a retornar `True`, que indica que o mecanismo de renderização de texto GDI+ ser usado, que é o padrão no Visual Basic .NET 2002 e Visual Basic .NET 2003.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A>  
  
## <a name="configuring-the-application"></a>Configurando o aplicativo  
 Como parte do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modelo de aplicativo, o <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>classe fornece propriedades protegidas que configuram o aplicativo.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Essas propriedades devem ser definidas no construtor da classe de implementação.  
  
 Em um projeto do Windows Forms, o **Project Designer** cria código para definir as propriedades com as configurações de designer. As propriedades são usadas somente quando o aplicativo está sendo iniciado; defini-las depois de iniciar o aplicativo não tem nenhum efeito.  
  
|Propriedade|Determina|Configuração no painel Application do Project Designer|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Se o aplicativo é executado como um aplicativo de instância única ou várias instâncias.|**Tornar o aplicativo de instância única** caixa de seleção|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Se o aplicativo usará estilos visuais que coincidir com o Windows XP.|**Habilitar estilos visuais XP** caixa de seleção|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Se o aplicativo salva automaticamente as alterações de configurações do usuário do aplicativo quando o aplicativo é encerrado.|**Salvar My. Settings on Shutdown** caixa de seleção|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|O que faz com que o aplicativo seja finalizado, como quando fecha o formulário de inicialização ou quando o último formulário fecha.|**Modo de desligamento** lista|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Visão geral do modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)   
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)

---
title: "Estendendo o modelo de aplicativo do Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Modelo de Aplicativo do Visual Basic, estendendo"
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estendendo o modelo de aplicativo do Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode adicionar funcionalidades ao modelo de aplicativo, substituindo os membros `Overridable` da classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>.  Essa técnica permite que você personalize o comportamento do modelo de aplicativo e adicione chamadas para seus próprios métodos quando o aplicativo é iniciado e desligado.  
  
## Visão geral visual do modelo de aplicativo  
 Esta seção visualmente apresenta a seqüência de chamadas de função no modelo de aplicativo do Visual Basic.  A seção seguinte descreve a finalidade de cada função em detalhes.  
  
 O gráfico a seguir mostra a seqüência de chamadas do modelo de aplicativo em um aplicativo Visual Basic Windows Forms normal.  A seqüência é iniciada quando o procedimento `Sub Main` chama o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.  
  
 ![Modelo de aplicativo do Visual Basic&#45;&#45; executar](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelrun.png "VB\_ModelRun")  
  
 O modelo de aplicativo do Visual Basic também fornece os eventos de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> e de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> .  Os gráficos a seguir mostram o mecanismo para disparar esses eventos.  
  
 ![Modelo de aplicativo do Visual Basic&#45;&#45; Próxima instância](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelnext.png "VB\_ModelNext")  
  
 ![Exceção sem tratamento do modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_unhandex.png "VB\_UnhandEx")  
  
## Substituindo os métodos base  
 O método de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> define a ordem em que a execução dos métodos de `Application` .  Por padrão, o procedimento `Sub Main` de um aplicativo  Windows Forms chama o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.  
  
 Se o aplicativo é um aplicativo normal \(aplicativo de várias instâncias,\) ou a primeira instância de um aplicativo de instância única, o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> executa os métodos `Overridable` na seguinte ordem:  
  
1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>.  Por padrão, esse método define estilos visuais, estilos de exibição de texto, e o principal atual para o segmento principal do aplicativo \(se o aplicativo usa autenticação do windows\), e chama `ShowSplashScreen` se nem nem `/nosplash``-nosplash` são usados como um argumento de linha de comando.  
  
     A seqüência de inicialização do aplicativo será cancelada se esta função retornar `False`.  Isso pode ser útil se houver circunstâncias em que o aplicativo não deva executar.  
  
     O método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> chama os métodos a seguir:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>.  Determina se o aplicativo tem um tela inicial definidas e se isso, exibe a tela inicial em um segmento separado.  
  
         O método de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> contém o código que exibe a tela inicial no mínimo o número de milissegundos especificado pela propriedade de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> .  Para usar essa funcionalidade, você deve adicionar a tela inicial para seu aplicativo usando o **Project Designer** \(que define a propriedade `My.Application.MinimumSplashScreenDisplayTime` como dois segundos\), ou definir a propriedade `My.Application.MinimumSplashScreenDisplayTime` em um  método que sobrescreve os métodos<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> ou <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>.  Para obter mais informações, consulte <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>.  Permite que um designer emitir o código que inicializa a tela inicial.  
  
         Por padrão, esse método não fará nada.  Se você selecionar um tela inicial para seu aplicativo em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]**Designer de Projeto**, o designer substitui o método de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> com um método que define a propriedade de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> para uma nova instância do formulário da tela inicial.  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>.  Fornece um ponto de extensibilidade para disparar o evento de `Startup` .  A seqüência de inicialização do aplicativo pára se essa função retornar `False`.  
  
     Por padrão, esse método dispara o evento de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> .  Se o manipulador de eventos define a propriedade <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> do argumento do evento como `True` o método retornará `False` para cancelar a inicialização do aplicativo.  
  
3.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>.  Fornece o ponto de partida para quando o aplicativo principal está pronto para iniciar a execução, após a inicialização é feita.  
  
     Por padrão, antes de entrar no loop de mensagem do Windows Forms, este método chama os métodos `OnCreateMainForm` \(para criar o formulário principal do aplicativo\) e `HideSplashScreen` \(para fechar a tela inicial\).  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>.  Fornece uma maneira para um designer emitir o código que inicializa o formulário principal.  
  
         Por padrão, esse método não fará nada.  No entanto, quando você seleciona um principal formulário para o seu aplicativo no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]  **Project Designer** ,o designer substitui o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> com um método que define a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> para uma nova instância do formulário principal.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>.  Se o aplicativo tem um tela inicial definida e está aberto, este método fecha a tela inicial.  
  
         Por padrão, esse método fecha a tela inicial.  
  
4.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>.  Fornece uma maneira de personalizar como um aplicativo de instância única se comporta quando outra instância do aplicativo inicia.  
  
     Por padrão, esse método dispara o evento de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> .  
  
5.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>.  Fornece um ponto de extensibilidade para disparar o evento de `Shutdown` .  Este método não é executado se uma exceção não manipulada ocorrer no aplicativo principal.  
  
     Por padrão, esse método dispara o evento de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> .  
  
6.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>.  Executado se uma exceção não tratada ocorrer em qualquer um dos métodos listados acima.  
  
     Por padrão, esse método dispara o evento de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> como um depurador é anexado e o aplicativo está tratando o evento de `UnhandledException` .  
  
 Se o aplicativo é um aplicativo de instância única, e o aplicativo já está em execução, a instância subseqüente do aplicativo chama o método <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> na instância original do aplicativo e, em seguida, sai.  
  
 O construtor <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> chama a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> para determinar qual mecanismo de renderização de texto a ser usado para formulários do aplicativo.  Por padrão, a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> retornará `False`,indicando que o mecanismo de renderização de texto GDI ser usado, qual é o padrão no [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)].  Você pode substituir a propriedade <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> para retornar `True`,que indica que o mecanismo de renderização de texto GDI\+ a ser usado, o qual é o padrão no Visual Basic .NET 2002 e Visual Basic .NET 2003.  
  
## Configurando o aplicativo  
 Como parte do modelo de aplicativo [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], a classe <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> fornece propriedades protegidas que configuram o aplicativo.  Essas propriedades devem ser definida no construtor da classe que as implementam.  
  
 Em um projeto do Windows Formspadrão, o **Project Designer** cria código para definir as propriedades com as configurações de designer.  As propriedades são usadas somente quando o aplicativo está sendo iniciado; definí\-las após o início do aplicativo não terá efeito.  
  
||||  
|-|-|-|  
|Propriedade|Determina|Definir no painel do designer de projeto|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Se o aplicativo é executado como um aplicativo de instância única ou de múltiplas instâncias.|a caixa de seleção de**Faça o aplicativo de instância única**|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Se o aplicativo usará estilos visuais que correspondem Windows XP.|a caixa de seleção de**Ativar estilos visuais XP**|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Se o aplicativo salva automaticamente as alterações nas configurações de usuário do aplicativo, quando sai do aplicativo.|a caixa de seleção de**Em a finalização salvar My.Settings**|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|O que faz com que o aplicativo seja finalizado, como quando o formulário de inicialização fechar ou quando o último formulário fechar.|lista de**Modo de finalização**|  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Visão geral do modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)   
 [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)
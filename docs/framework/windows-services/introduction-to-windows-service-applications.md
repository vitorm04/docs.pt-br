---
title: "Introdução a aplicativos do Serviço Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ServiceController
helpviewer_keywords:
- Windows Service applications, deploying
- OnStop method
- OnPause method
- services, about services
- Service class, Windows Service applications
- framework services, creating services
- ServiceController components, about Windows services
- Win32OwnProcess service type
- services, lifetime
- OnContinue method
- Windows Service applications, about Windows Service applications
- services, states
- service states
- WaitForStatus method
- Win32ShareProcess service type
- Windows Service applications, lifetime
ms.assetid: 1b1b5e67-3ff3-40c0-8154-322cfd6ef0ae
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: d24daf5520c7bfe74c09abc24a4260266e5b9c1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-windows-service-applications"></a>Introdução a aplicativos do Serviço Windows
Serviços do Microsoft Windows, anteriormente conhecidos como serviços NT, permitem que você crie aplicativos executáveis de longa execução que são executados em suas próprias sessões do Windows. Esses serviços podem ser iniciados automaticamente quando o computador é inicializado, pode ser interrompido e reiniciado e não exibir nenhuma interface do usuário. Esses recursos tornam os serviços ideais para uso em um servidor ou sempre que você precisa de funcionalidade de longa execução que não interfere com outros usuários que trabalham no mesmo computador. Você também pode executar serviços no contexto de segurança de uma conta de usuário específica que é diferente do usuário conectado ou a conta de computador padrão. Para obter mais informações sobre serviços e sessões do Windows, consulte a documentação do SDK do Windows.  
  
 Você pode criar serviços facilmente, criando um aplicativo que é instalado como um serviço. Por exemplo, suponha que você queira monitorar dados do contador de desempenho e reagir aos valores de limite. Você pode escrever um aplicativo de serviço do Windows que escuta os dados do contador de desempenho, implante o aplicativo e começar a coleta e análise de dados.  
  
 Você cria seu serviço como um projeto do Microsoft Visual Studio, definindo dentro dele código que controla os comandos que pode ser enviado para o serviço e quais ações devem ser tomadas quando esses comandos são recebidos. Comandos que podem ser enviados para um serviço incluem iniciar, pausar, retomar e parar o serviço; Você também pode executar comandos personalizados.  
  
 Depois de criar e compilar o aplicativo, você pode instalá-lo executando o utilitário de linha de comando InstallUtil.exe e passando o caminho para o arquivo executável do serviço. Você pode usar o **Gerenciador de controle de serviços** para iniciar, parar, pausar, retomar e configurar seu serviço. Você também pode realizar muitas das mesmas tarefas no **serviços** nó **Server Explorer** ou usando o <xref:System.ServiceProcess.ServiceController> classe.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Aplicativos de serviço vs. Outros aplicativos do Visual Studio  
 Função de aplicativos de serviço diferente de muitos outros tipos de projeto de várias maneiras:  
  
-   O arquivo executável compilado que cria um projeto de aplicativo de serviço deve ser instalado no servidor antes que o projeto pode funcionar de forma significativa. Você não pode depurar ou executar um aplicativo de serviço pressionando F5 ou F11; Você não pode executar imediatamente um serviço ou a etapa em seu código. Em vez disso, você deve instalar e iniciar o serviço e, em seguida, anexar um depurador ao processo do serviço. Para obter mais informações, consulte [como: depurar aplicativos de serviço do Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md).  
  
-   Ao contrário de alguns tipos de projetos, você deve criar componentes de instalação para aplicativos de serviço. Os componentes de instalação instalar e registrar o serviço no servidor e criar uma entrada para o serviço com o Windows **Gerenciador de controle de serviços**. Para obter mais informações, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
-   O `Main` método para seu aplicativo de serviço deve emitir o comando Run para os serviços de seu projeto contém. O `Run` método carrega os serviços para o **Gerenciador de controle de serviços** no servidor apropriado. Se você usar o **Windows Services** modelo de projeto, esse método será escrito para você automaticamente. Observe que um serviço de carga não é a mesma coisa que iniciar o serviço. Consulte o "Serviço de tempo de vida" abaixo para obter mais informações.  
  
-   Aplicativos de serviço do Windows executado em uma estação de janela diferente da estação interativa do usuário conectado. Uma estação de janela é um objeto seguro que contém uma área de transferência, um conjunto de átomos globais e um grupo de objetos de área de trabalho. Como a estação de serviço do Windows não é uma estação interativa, caixas de diálogo gerada de uma janela de aplicativo de serviço não será visto e pode fazer com que seu programa pare de responder. Da mesma forma, as mensagens de erro devem ser registradas no log de eventos do Windows em vez de gerado na interface do usuário.  
  
     As classes de serviço do Windows com suporte do .NET Framework não dão suporte a interação com estações interativas, ou seja, o usuário conectado. O .NET Framework também não inclui classes que representam estações e áreas de trabalho. Se o serviço do Windows deve interagir com outras estações, você precisará acessar a API não gerenciada do Windows. Para obter mais informações, consulte a documentação do SDK do Windows.  
  
     A interação das janelas de serviço com o usuário ou outras estações deve ser projetado para incluir cenários tais quanto houver sendo nenhum usuário conectado, ou o usuário possui um conjunto inesperado de objetos de área de trabalho. Em alguns casos, pode ser mais apropriado gravar um aplicativo do Windows que é executado sob o controle do usuário.  
  
-   Aplicativos de serviço do Windows executado em seu próprio contexto de segurança e são iniciados antes do usuário fizer logon no Windows do computador no qual eles são instalados. Você deve planejar cuidadosamente qual conta de usuário para executar o serviço em; um serviço executado sob a conta do sistema tem mais permissões e privilégios que uma conta de usuário.  
  
## <a name="service-lifetime"></a>Tempo de vida do serviço  
 Um serviço passa por vários estados internos no seu tempo de vida. Primeiro, o serviço está instalado no sistema no qual ele será executado. Esse processo executa os instaladores para o projeto de serviço e carrega o serviço para o **Gerenciador de controle de serviços** para o computador. O **Gerenciador de controle de serviços** é o utilitário central fornecido pelo Windows para administrar serviços.  
  
 Depois que o serviço tiver sido carregado, ele deve ser iniciado. Iniciando o serviço permite que ele comece a funcionar. Você pode iniciar um serviço do **Gerenciador de controle de serviços**, de **Server Explorer**, ou de código chamando o <xref:System.ServiceProcess.ServiceController.Start%2A> método. O <xref:System.ServiceProcess.ServiceController.Start%2A> método passa o processamento para o aplicativo <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e processa qualquer código que você tenha definido ali.  
  
 Um serviço em execução pode existir nesse estado indefinidamente até que ele seja interrompido ou pausado, ou até que o computador é desligado. Um serviço pode existir em um de três estados básico: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, ou <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. O serviço também pode informar o estado de um comando pendente: <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>, ou <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Esses status indicam que um comando tiver sido emitido, como um comando para pausar um serviço em execução, mas não foi executado ainda. Você pode consultar o <xref:System.ServiceProcess.ServiceController.Status%2A> para determinar o estado de um serviço, ou usar o <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> executar uma ação quando algum desses estados ocorre.  
  
 Você pode pausar, interromper ou continuar um serviço do **Gerenciador de controle de serviços**, de **Server Explorer**, ou chamando métodos do código. Cada uma dessas ações pode chamar um procedimento associado no serviço (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, ou <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), no qual você pode definir o processamento adicional a ser executada quando o serviço de estado é alterado.  
  
## <a name="types-of-services"></a>Tipos de serviços  
 Há dois tipos de serviços que você pode criar no Visual Studio usando o .NET Framework. Serviços que são o único serviço em um processo são atribuídos ao tipo <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Serviços que compartilham um processo com outro serviço recebem o tipo <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>. Você pode recuperar o tipo do serviço consultando o <xref:System.ServiceProcess.ServiceController.ServiceType%2A> propriedade.  
  
 Ocasionalmente, você poderá ver outros tipos de serviço se você consultar serviços existentes que não foram criados no Visual Studio. Para obter mais informações sobre estas configurações, consulte o <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Serviços e o componente ServiceController  
 O <xref:System.ServiceProcess.ServiceController> componente é usado para se conectar a um serviço instalado e manipular o seu estado; usando um <xref:System.ServiceProcess.ServiceController> componente, você pode iniciar e parar um serviço, pausar e continuar o seu funcionamento e enviar comandos personalizados para um serviço. No entanto, você não precisa usar um <xref:System.ServiceProcess.ServiceController> quando você cria um aplicativo de serviço de componente. Na verdade, na maioria dos casos seu <xref:System.ServiceProcess.ServiceController> componente deve existir em um aplicativo separado do aplicativo de serviço do Windows que define seu serviço.  
  
 Para obter mais informações, consulte <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Requisitos  
  
-   Serviços devem ser criados em um **Windows Service** projeto de aplicativo ou outro projeto habilitado do .NET Framework que cria um arquivo .exe quando compilado e herda o <xref:System.ServiceProcess.ServiceBase> classe.  
  
-   Projetos que contêm serviços do Windows devem ter os componentes de instalação para o projeto e seus serviços. Isso pode ser facilmente conseguido a partir de **propriedades** janela. Para obter mais informações, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
## <a name="see-also"></a>Consulte também  
 [Aplicativos do Serviço Windows](../../../docs/framework/windows-services/index.md)  
 [Arquitetura de programação de aplicativo de serviço](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 [Como: criar serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Como: instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Como: iniciar serviços](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Como: depurar aplicativos de serviço do Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Passo a passo: Criando um aplicativo de serviço do Windows no Designer de componente](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 [Como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)

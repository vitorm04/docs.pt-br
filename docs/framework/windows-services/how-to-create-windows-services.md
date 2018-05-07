---
title: Como criar Serviços Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
manager: douge
ms.openlocfilehash: 7719af9393bee816665040d6e4ced191419d0855
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-windows-services"></a>Como criar Serviços Windows
Quando você cria um serviço, você pode usar um modelo de projeto do Visual Studio chamado **serviço Windows**. Esse modelo realiza automaticamente muito do trabalho para você referenciando as classes e namespaces apropriados, configurando a herança de classe base para serviços, e substituindo muitos dos métodos que você provavelmente desejará substituir.  
  
> [!WARNING]
>  O modelo de projeto do serviço Windows não está disponível na edição Express do Visual Studio.  
  
 Para criar um serviço funcional, você deve, no mínimo:  
  
-   Definir a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A>.  
  
-   Criar os instaladores necessários para seu aplicativo de serviço.  
  
-   Substituir e especificar código para os métodos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> para personalizar as formas nas quais o serviço funciona.  
  
### <a name="to-create-a-windows-service-application"></a>Para criar um aplicativo de serviço Windows  
  
1.  Criar um **Windows Service** projeto.  
  
    > [!NOTE]
    >  Para obter instruções sobre como escrever um serviço sem usar o modelo, consulte [como: escrever serviços programaticamente](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
2.  No **propriedades** janela, defina o <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> propriedade para o serviço.  
  
     ![Defina a propriedade ServiceName. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    >  O valor da propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> sempre deve corresponder ao nome registrado nas classes do instalador. Se você alterar essa propriedade, também deverá atualizar a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> das classes do instalador.  
  
3.  Defina qualquer uma das propriedades a seguir para determinar como seu serviço funcionará.  
  
    |Propriedade|Configuração|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True` para indicar que o serviço aceitará solicitações para parar a execução; `false` para impedir que o serviço seja interrompido.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True` para indicar que o serviço deseja receber uma notificação quando o computador no qual ele está for desligado, permitindo que a ele chamar o procedimento <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True` para indicar que o serviço aceitará solicitações para pausar ou continuar executando; `false` para impedir que o serviço seja pausado e retomado.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True` para indicar que o serviço pode manipular a notificação de alterações de status de energia do computador; `false` para impedir que o serviço seja notificado dessas alterações.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True` para gravar entradas informativas no log de eventos do aplicativo quando seu serviço executa uma ação; `false` para desabilitar essa funcionalidade. Para obter mais informações, consulte [como: obter informações sobre serviços de Log](../../../docs/framework/windows-services/how-to-log-information-about-services.md). **Observação:** por padrão, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> é definido como `true`.|  
  
    > [!NOTE]
    >  Quando <xref:System.ServiceProcess.ServiceBase.CanStop%2A> ou <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> são definidos como `false`, o **Service Control Manager** desabilitará as opções de menu correspondente para parar, pausar ou continuar o serviço.  
  
4.  Acesse o Editor de código e preencha o processamento que você deseja para os procedimentos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.  
  
5.  Substitua quaisquer outros métodos para os quais você deseja definir a funcionalidade.  
  
6.  Adicionar os instaladores necessários para seu aplicativo de serviço. Para obter mais informações, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
7.  Compilar o projeto selecionando **compilar solução** do **criar** menu.  
  
    > [!NOTE]
    >  Pressione F5 para executar seu projeto. Você não pode executar um projeto de serviço dessa maneira.  
  
8.  Instale o serviço. Para obter mais informações, consulte [como: instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Como escrever serviços programaticamente](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [Como adicionar instaladores no seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Como registrar informações sobre serviços](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [Como iniciar serviços](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Como especificar o contexto de segurança para serviços](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [Como instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

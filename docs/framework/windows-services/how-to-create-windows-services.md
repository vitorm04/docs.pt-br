---
title: 'Como: Criar serviços Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
author: ghogen
ms.openlocfilehash: 514675b3c3ce1f6701dff571361df672fb520c6a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053666"
---
# <a name="how-to-create-windows-services"></a>Como: Criar serviços Windows
Ao criar um serviço, você pode usar um modelo de projeto Visual Studio chamado **Serviço Windows**. Esse modelo realiza automaticamente muito do trabalho para você referenciando as classes e namespaces apropriados, configurando a herança de classe base para serviços, e substituindo muitos dos métodos que você provavelmente desejará substituir.  
  
> [!WARNING]
> O modelo de projeto do serviço Windows não está disponível na edição Express do Visual Studio.  
  
 Para criar um serviço funcional, você deve, no mínimo:  
  
- Definir a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A>.  
  
- Criar os instaladores necessários para seu aplicativo de serviço.  
  
- Substituir e especificar código para os métodos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> para personalizar as formas nas quais o serviço funciona.  
  
### <a name="to-create-a-windows-service-application"></a>Para criar um aplicativo de serviço Windows  
  
1. Crie um projeto de **Serviço Windows**.  
  
    > [!NOTE]
    > Para obter instruções sobre como escrever um serviço sem usar o modelo, confira [Como: Escrever serviços de forma programática](how-to-write-services-programmatically.md).  
  
2. Na janela **Propriedades**, configure a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> para seu serviço.  
  
     ![Defina a propriedade ServiceName.](./media/windowsservice-servicename.PNG "WindowsService_ServiceName")  
  
    > [!NOTE]
    > O valor da propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> sempre deve corresponder ao nome registrado nas classes do instalador. Se você alterar essa propriedade, também deverá atualizar a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> das classes do instalador.  
  
3. Defina qualquer uma das propriedades a seguir para determinar como seu serviço funcionará.  
  
    |Propriedade|Configuração|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|`True` para indicar que o serviço aceitará solicitações para parar a execução; `false` para impedir que o serviço seja interrompido.|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|`True` para indicar que o serviço deseja receber uma notificação quando o computador no qual ele está for desligado, permitindo que a ele chamar o procedimento <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>.|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|`True` para indicar que o serviço aceitará solicitações para pausar ou continuar executando; `false` para impedir que o serviço seja pausado e retomado.|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|`True` para indicar que o serviço pode manipular notificações de alterações de status de energia do computador; `false` para impedir que o serviço seja notificado sobre alterações.|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|`True` para gravar entradas informativas no log de eventos do aplicativo quando seu serviço executa uma ação; `false` para desabilitar essa funcionalidade. Para obter mais informações, confira [Como: Registrar em log informações sobre serviços](how-to-log-information-about-services.md). **Observação:**  Por padrão, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> é definido como `true`.|  
  
    > [!NOTE]
    > Quando <xref:System.ServiceProcess.ServiceBase.CanStop%2A> ou <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> forem definidos como `false`, o **Gerenciador de Controle de Serviço** desabilitará as opções de menu correspondentes para parar, pausar ou continuar o serviço.  
  
4. Acesse o Editor de código e preencha o processamento que você deseja para os procedimentos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.  
  
5. Substitua quaisquer outros métodos para os quais você deseja definir a funcionalidade.  
  
6. Adicionar os instaladores necessários para seu aplicativo de serviço. Para obter mais informações, confira [Como: Adicionar instaladores ao aplicativo de serviço](how-to-add-installers-to-your-service-application.md).  
  
7. Compile o projeto selecionando **Compilar Solução** no menu **Compilar**.  
  
    > [!NOTE]
    > Pressione F5 para executar seu projeto. Você não pode executar um projeto de serviço dessa maneira.  
  
8. Instale o serviço. Para obter mais informações, confira [Como: Instalar e desinstalar serviços](how-to-install-and-uninstall-services.md).  
  
## <a name="see-also"></a>Consulte também

- [Introdução aos Aplicativos de Serviço Windows](introduction-to-windows-service-applications.md)
- [Como: Escrever serviços de forma programática](how-to-write-services-programmatically.md)
- [Como: adicionar instaladores ao aplicativo de serviço](how-to-add-installers-to-your-service-application.md)
- [Como: Registrar em log informações sobre serviços](how-to-log-information-about-services.md)
- [Como: Iniciar serviços](how-to-start-services.md)
- [Como: Especificar o contexto de segurança para serviços](how-to-specify-the-security-context-for-services.md)
- [Como: Instalar e desinstalar serviços](how-to-install-and-uninstall-services.md)
- [Passo a passo: Criando um aplicativo de serviço Windows no Designer de Componentes](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

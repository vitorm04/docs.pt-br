---
title: "Como hospedar um serviço de fluxo de trabalho com o Windows Server App Fabric"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc7af813f7fff422a2513c58c9e3cba6376de060
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Como hospedar um serviço de fluxo de trabalho com o Windows Server App Fabric
Serviços de fluxo de trabalho na malha de aplicativos de hospedagem é semelhante à hospedagem no IIS / WAS. A única diferença é que as ferramentas de que malha de aplicativos fornece para implantação, monitoramento e gerenciamento de serviços de fluxo de trabalho. Este tópico usa o serviço de fluxo de trabalho criado na [criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Esse tópico orientará você durante a criação de um serviço de fluxo de trabalho. Este tópico explica como hospedar o serviço de fluxo de trabalho usando a malha de aplicativos. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Malha de aplicativos do Windows Server, consulte [documentação do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409). Antes de concluir as etapas abaixo, certifique-se de que ter o Windows Server App Fabric está instalado.  Para fazer essa abrir os serviços de informações da Internet (inetmgr.exe), clique no nome do servidor no **conexões** exibir, clique em Sites e clique em **Default Web Site**. O lado direito da tela, você verá uma seção chamada **App Fabric**. Se você não vir essa seção (ele estará na parte superior do painel à direita) não tem malha de aplicativos instalada. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Instalando o Windows Server App Fabric consulte [instalando o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193136).  
  
### <a name="creating-a-simple-workflow-service"></a>Criando um serviço de fluxo de trabalho simples  
  
1.  Abra [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e carregar a solução OrderProcessing criado na [criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) tópico.  
  
2.  Clique com botão direito do **OrderService** do projeto e selecione **propriedades** e selecione o **Web** guia.  
  
3.  No **iniciar ação** seção da página de propriedades selecione **página específica** e digite Service1.xamlx na caixa de edição.  
  
4.  No **servidores** seção da página de propriedades selecione **usar servidor Web do IIS Local** e digite a seguinte URL: `http://localhost/OrderService`.  
  
5.  Clique o **criar diretório Virtual** botão. Isso criará um novo diretório virtual e configurar o projeto para copiar os arquivos necessários para o diretório virtual quando o projeto é compilado.  Como alternativa você pode copiar manualmente o .xamlx, o Web. config e quaisquer DLLs necessários para o diretório virtual.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Configurar um serviço de fluxo de trabalho hospedado no Windows Server AppFabric  
  
1.  Abra o Gerenciador de serviços de informações da Internet (inetmgr.exe).  
  
2.  Navegue até o diretório virtual OrderService no **conexões** painel.  
  
3.  Clique com botão direito OrderService e selecione **serviços gerenciar WCF e WF**, **configurar...** . O **configurar WCF e WF do aplicativo** caixa de diálogo é exibida.  
  
4.  Selecione o **geral** guia para exibir informações gerais sobre o aplicativo, conforme mostrado na captura de tela a seguir.  
  
     ![Guia geral da caixa de diálogo Configuração de malha de aplicativos](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration-geral")  
  
5.  Selecione o **monitoramento** guia. Isso mostra várias configurações de monitoramentos, como mostrado na captura de tela a seguir.  
  
     ![Guia de monitoramento de malha de configuração de aplicativo](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration monitoramento")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Configurando o monitoramento de serviço de fluxo de trabalho na malha de aplicativos consulte [Configurando o monitoramento de malha de aplicativos](http://go.microsoft.com/fwlink/?LinkId=193153).  
  
6.  Selecione o **persistência de fluxo de trabalho** guia. Isso permite que você configure seu aplicativo para usar o provedor de persistência do padrão da malha de aplicativos como mostrado na captura de tela a seguir.  
  
     ![Configuração de malha de aplicativos &#45; Persistência](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration persistência")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como configurar persistência de fluxo de trabalho no Windows Server App Fabric consulte [Configurando a persistência de fluxo de trabalho na malha de aplicativos](http://go.microsoft.com/fwlink/?LinkId=193148).  
  
7.  Selecione o **gerenciamento de Host de fluxo de trabalho** guia. Isso permite que você especifique quando as instâncias de serviço de fluxo de trabalho ocioso devem ser descarregadas e persistentes conforme mostrado na captura de tela a seguir.  
  
     ![Gerenciamento de Host de fluxo de trabalho de configuração de malha de aplicativos](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration gerenciamento")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Consulte de configuração de gerenciamento de host de fluxo de trabalho [Configurando o gerenciamento de Host de fluxo de trabalho na malha de aplicativos](http://go.microsoft.com/fwlink/?LinkId=193151).  
  
8.  Selecione o **Auto-Start** guia. Isso permite que você especifique configurações de início automático para os serviços de fluxo de trabalho no aplicativo, conforme mostrado na captura de tela a seguir.  
  
     ![Automático da malha de aplicativo &#45; a configuração de início](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationautostart.gif "AppFabricConfigurationAutostart")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Configurando o início automático consulte [Configurando Auto-Start com a malha de aplicativos](http://go.microsoft.com/fwlink/?LinkId=193150).  
  
9. Selecione o **limitação** guia. Isso permite que você defina as configurações de limitação para o serviço de fluxo de trabalho, como mostrado na captura de tela a seguir.  
  
     ![Limitação da configuração da malha de aplicativos](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationthrottling.gif "AppFabricConfigurationThrottling")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como configurar a limitação consulte [configurar limitação com o App Fabric](http://go.microsoft.com/fwlink/?LinkId=193149).  
  
10. Selecione o **segurança** guia. Isso permite que você defina as configurações de segurança para o aplicativo, conforme mostrado na captura de tela a seguir.  
  
     ![Configuração de segurança de malha de aplicativos](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration-segurança")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Configurando a segurança com o Windows Server App Fabric consulte [Configurando a segurança com o App Fabric](http://go.microsoft.com/fwlink/?LinkId=193152).  
  
### <a name="using-windows-server-app-fabric"></a>Usando o Windows Server App Fabric  
  
1.  Compile a solução para copiar os arquivos necessários para o diretório virtual.  
  
2.  Clique com botão direito no projeto OrderClient e selecione **depurar**, **iniciar uma nova instância** para iniciar o aplicativo cliente.  
  
3.  O cliente será executado e o Visual Studio exibirá um **anexar aviso de segurança** caixa de diálogo, clique o **não anexar** botão. Isso informa ao Visual Studio para não anexar ao processo do IIS para depuração.  
  
4.  O aplicativo cliente será imediatamente chamar o serviço de fluxo de trabalho e, em seguida, aguarde. O serviço de fluxo de trabalho irá ocioso e ser persistente. Você pode verificar isso iniciando os serviços de informações da Internet (inetmgr.exe), navegando até o OrderService no painel conexões e selecioná-la. Em seguida, clique no ícone do painel de estrutura de aplicativo no painel direito. Em instâncias de WF persistentes, você verá uma instância de serviço de fluxo de trabalho persistentes conforme mostrado na captura de tela a seguir.  
  
     ![Painel da malha de aplicativos](../../../../docs/framework/wcf/feature-details/media/appfabricdashboard.gif "AppFabricDashboard")  
  
     O **histórico de instância do WF** lista informações sobre o serviço de fluxo de trabalho, como o número de ativações de serviço de fluxo de trabalho, o número de conclusões de instância do serviço de fluxo de trabalho e o número de instâncias de fluxo de trabalho com falhas. Em instâncias de ativo ou ocioso que será exibido um link, clicando no link exibirá mais informações sobre as instâncias de fluxo de trabalho ocioso, conforme mostrado na captura de tela a seguir.  
  
     ![Persistente detalhes da instância de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/media/persisteddetail.gif "PersistedDetail")  
  
     Para obter mais informações sobre o Windows Server App Fabric consulte os recursos e como usá-los [recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=193143&clcid=0x409)  
  
## <a name="see-also"></a>Consulte também  
 [Criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193143)  
 [Instalando o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193136)  
 [Documentação do Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)

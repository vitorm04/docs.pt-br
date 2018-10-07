---
title: Como hospedar um serviço de fluxo de trabalho com o Windows Server App Fabric
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: 2c1e4e8763ad9bd65099173c75d272965ac8caa8
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840611"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Como hospedar um serviço de fluxo de trabalho com o Windows Server App Fabric
Hospedagem de serviços de fluxo de trabalho na tela do aplicativo é semelhante ao hospedarmos no IIS / WAS. A única diferença é que as ferramentas que do App Fabric fornece para implantação, monitoramento e gerenciamento de serviços de fluxo de trabalho. Este tópico usa o serviço de fluxo de trabalho criado a [criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Esse tópico orientará você pela criação de um serviço de fluxo de trabalho. Este tópico explica como hospedar o serviço de fluxo de trabalho usando a malha de aplicativos. Para obter mais informações sobre o Windows Server AppFabric, consulte [documentação do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409). Antes de concluir as etapas a seguir, certifique-se de que ter o Windows Server App Fabric instalado.  Para fazer isso, abra os serviços de informações da Internet (inetmgr.exe), clique no nome de servidor na **conexões** exibir, clique em Sites e clique em **Default Web Site**. No lado direito da tela, você deve ver uma seção chamada **App Fabric**. Se você não vir essa seção (vai estar na parte superior do painel à direita) não tem malha de aplicativos instalada. Para obter mais informações sobre como instalar o Windows Server AppFabric, consulte [instalando o Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193136).  
  
### <a name="creating-a-simple-workflow-service"></a>Criando um serviço de fluxo de trabalho simples  
  
1.  Abra o Visual Studio 2012 e carregar a solução de OrderProcessing criado na [criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) tópico.  
  
2.  Clique com botão direito do **OrderService** do projeto e selecione **propriedades** e selecione o **Web** guia.  
  
3.  No **iniciar ação** selecione a seção da página de propriedades **página específica** e digite Service1.xamlx na caixa de edição.  
  
4.  No **servidores** selecione a seção da página de propriedades **usar servidor Web do IIS Local** e digite a seguinte URL: `http://localhost/OrderService`.  
  
5.  Clique o **criar diretório Virtual** botão. Isso criará um novo diretório virtual e configurar o projeto para copiar os arquivos necessários para o diretório virtual quando o projeto é compilado.  Como alternativa, você poderia copiar manualmente o. xamlx, Web. config e todas as DLLs necessárias para o diretório virtual.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Configurar um serviço de fluxo de trabalho hospedado no Windows Server App Fabric  
  
1.  Abra o Gerenciador de serviços de informações da Internet (inetmgr.exe).  
  
2.  Navegue até o diretório virtual de OrderService na **conexões** painel.  
  
3.  Clique com botão direito OrderService e selecione **gerenciar serviços WCF e WF**, **configurar...** . O **configurar WCF e WF do aplicativo** caixa de diálogo é exibida.  
  
4.  Selecione o **geral** guia para exibir informações gerais sobre o aplicativo, conforme mostrado na seguinte captura de tela.  
  
     ![Guia geral da caixa de diálogo Configuração de malha do aplicativo](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration-geral")  
  
5.  Selecione o **monitoramento** guia. Isso mostra várias configurações de monitoramento, conforme mostrado na seguinte captura de tela.  
  
     ![Guia do aplicativo de monitoramento da configuração de malha](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration-monitoramento")  
  
     Para obter mais informações sobre como configurar o serviço de fluxo de trabalho de monitoramento na tela do aplicativo ver [Configurando o monitoramento com o App Fabric](https://go.microsoft.com/fwlink/?LinkId=193153).  
  
6.  Selecione o **persistência de fluxo de trabalho** guia. Isso permite que você configure seu aplicativo para usar o provedor de persistência de padrão do App Fabric conforme mostrado na seguinte captura de tela.  
  
     ![Configuração de malha de aplicativos &#45; persistência](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration persistência")  
  
     Para obter mais informações sobre como configurar a persistência de fluxo de trabalho no Windows Server AppFabric, consulte [configurar a persistência de fluxo de trabalho na tela do aplicativo](https://go.microsoft.com/fwlink/?LinkId=193148).  
  
7.  Selecione o **gerenciamento de Host de fluxo de trabalho** guia. Isso permite que você especifique quando as instâncias de serviço de fluxo de trabalho ocioso devem ser descarregadas e persistente como mostrado na seguinte captura de tela.  
  
     ![Gerenciamento de Host de fluxo de trabalho de configuração de malha de aplicativos](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration-gerenciamento")  
  
     Para obter mais informações sobre a configuração de gerenciamento de host de fluxo de trabalho, consulte [Configurando o gerenciamento de Host de fluxo de trabalho na tela do aplicativo](https://go.microsoft.com/fwlink/?LinkId=193151).  
  
8.  Selecione o **Auto-Start** guia. Isso permite que você especifique configurações de inicialização automática para os serviços de fluxo de trabalho no aplicativo, conforme mostrado na seguinte captura de tela.  
  
     ![Automático da malha de aplicativo&#45;Iniciar configuração](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationautostart.gif "AppFabricConfigurationAutostart")  
  
     Para obter mais informações sobre como configurar o início automático, consulte [Configurando Auto-Start com App Fabric](https://go.microsoft.com/fwlink/?LinkId=193150).  
  
9. Selecione o **limitação** guia. Isso permite que você defina as configurações de limitação para o serviço de fluxo de trabalho, conforme mostrado na seguinte captura de tela.  
  
     ![Limitação da configuração da malha de aplicativos](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationthrottling.gif "AppFabricConfigurationThrottling")  
  
     Para obter mais informações sobre como configurar a limitação, consulte [Configurando a limitação com o App Fabric](https://go.microsoft.com/fwlink/?LinkId=193149).  
  
10. Selecione o **segurança** guia. Isso permite que você defina as configurações de segurança para o aplicativo, conforme mostrado na seguinte captura de tela.  
  
     ![Configuração de segurança da malha de aplicativos](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration-segurança")  
  
     Para obter mais informações sobre como configurar a segurança com o Windows Server AppFabric, consulte [Configurando a segurança com o App Fabric](https://go.microsoft.com/fwlink/?LinkId=193152).  
  
### <a name="using-windows-server-app-fabric"></a>Usando o Windows Server App Fabric  
  
1.  Compile a solução para copiar os arquivos necessários para o diretório virtual.  
  
2.  Com o botão direito do mouse no projeto OrderClient e selecione **Debug**, **iniciar nova instância** para iniciar o aplicativo cliente.  
  
3.  O cliente será executado e o Visual Studio exibirá um **anexar aviso de segurança** caixa de diálogo, clique o **não anexar** botão. Isso informa ao Visual Studio não anexar ao processo do IIS para depuração.  
  
4.  O aplicativo cliente será imediatamente chamar o serviço de fluxo de trabalho e, em seguida, aguarde. O serviço de fluxo de trabalho ficará ocioso e ser persistente. Você pode verificar isso iniciando o Internet Information Services (inetmgr.exe), navegando até o OrderService no painel de conexões e selecioná-la. Em seguida, clique no ícone do painel de aplicativo da malha no painel à direita. Em instâncias persistidas do WF, você verá há uma instância de serviço de fluxo de trabalho persistida como mostrado na seguinte captura de tela.  
  
     ![Painel da malha de aplicativos](../../../../docs/framework/wcf/feature-details/media/appfabricdashboard.gif "AppFabricDashboard")  
  
     O **histórico de instância de WF** lista informações sobre o serviço de fluxo de trabalho, como o número de ativações do serviço de fluxo de trabalho, o número de conclusões de instância de serviço de fluxo de trabalho e o número de instâncias de fluxo de trabalho com falhas. Em instâncias de ativo ou ocioso que será exibido um link, clicar no link exibirá mais informações sobre as instâncias de fluxo de trabalho ocioso, conforme mostrado na seguinte captura de tela.  
  
     ![Persistente detalhes da instância de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/media/persisteddetail.gif "PersistedDetail")  
  
     Para obter mais informações sobre o Windows Server App Fabric Consulte recursos e como usá-los [recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=193143&clcid=0x409)  
  
## <a name="see-also"></a>Consulte também  
 [Criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193143)  
 [Instalando o Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193136)  
 [Documentação do Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)

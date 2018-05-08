---
title: Como iniciar serviços
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
manager: douge
ms.openlocfilehash: 3c8382d2e425d11dc8aa8b22e361b3cc5637744f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-start-services"></a>Como iniciar serviços
Depois que um serviço é instalado, ele deve ser iniciado. Iniciando chamadas de <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método na classe de serviço. Normalmente, o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método define o trabalho útil que o serviço irá executar. Depois que um serviço é iniciado, ele permanece ativo até que seja pausado ou interrompido manualmente.  
  
 Services pode ser configurado para iniciar automaticamente ou manualmente. Um serviço que inicia automaticamente será iniciado quando o computador no qual ele está instalado é reinicializado ou é ligado pela primeira vez. Um usuário deve iniciar um serviço que inicia manualmente.  
  
> [!NOTE]
>  Por padrão, os serviços criados com o Visual Studio são definidos para iniciar manualmente.  
  
 Há várias maneiras que você pode iniciar manualmente um serviço — de **Server Explorer**, do **Gerenciador de controle de serviços**, ou do código usando um componente denominado o <xref:System.ServiceProcess.ServiceController>.  
  
 Definir o <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriedade o <xref:System.ServiceProcess.ServiceInstaller> classe para determinar se um serviço deve ser iniciado manualmente ou automaticamente.  
  
### <a name="to-specify-how-a-service-should-start"></a>Para especificar como um serviço deve ser iniciado  
  
1.  Depois de criar seu serviço, adicione os instaladores necessários para ele. Para obter mais informações, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  No designer, clique o instalador de serviço para o serviço que você está trabalhando.  
  
3.  No **propriedades** janela, defina o <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriedade para um dos seguintes:  
  
    |Para ter seu serviço instalado|Definir esse valor|  
    |----------------------------------|--------------------|  
    |Quando o computador é reiniciado|**Automático**|  
    |Quando uma ação explícita do usuário inicia o serviço|**Manual**|  
  
    > [!TIP]
    >  Para impedir que seu serviço seja iniciado, você pode definir o <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriedade **desabilitado**. Você pode fazer isso se você vai reiniciar um servidor várias vezes e deseja economizar tempo, impedindo que os serviços que normalmente seriam iniciados seja iniciado.  
  
    > [!NOTE]
    >  Essas e outras propriedades podem ser alteradas depois que o serviço está instalado.  
  
     Há várias maneiras que você pode iniciar um serviço que tem seu <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> processo definido como **Manual** — de **Server Explorer**, do **Gerenciador de controle de serviços do Windows**, ou de código. É importante observar que nem todos os métodos realmente iniciam o serviço no contexto do **Gerenciador de controle de serviços**; **Server Explorer** e métodos programáticos de iniciar o serviço realmente manipulam o controlador.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>Para iniciar manualmente um serviço do Gerenciador de servidores  
  
1.  Em **Server Explorer**, adicione o servidor que você deseja se ele não ainda esteja listado. Para obter mais informações, consulte como: acesso e inicializar o Gerenciador de banco de dados do Gerenciador de servidores.  
  
2.  Expanda o **serviços** nó e, em seguida, localize o serviço que você deseja iniciar.  
  
3.  Clique no nome do serviço e, em seguida, clique em **iniciar**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>Para iniciar manualmente um serviço do Gerenciador de controle de serviços  
  
1.  Abra o **Gerenciador de controle de serviços** seguindo um destes procedimentos:  
  
    -   No Windows XP e 2000 Professional, clique com botão direito **meu computador** na área de trabalho e, em seguida, clique **gerenciar**. Na caixa de diálogo que aparece, expanda o **serviços e aplicativos** nó.  
  
         \- ou -  
  
    -   No Windows Server 2003 e Windows 2000 Server, clique em **iniciar**, aponte para **programas**, clique em **ferramentas administrativas**e, em seguida, clique em **serviços**.  
  
        > [!NOTE]
        >  No Windows NT versão 4.0, você pode abrir essa caixa de diálogo de **painel de controle**.  
  
     Agora você deve ver seu serviço listado no **serviços** seção da janela.  
  
2.  Selecione o serviço na lista, clique duas vezes e, em seguida, clique em **iniciar**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Para iniciar manualmente um serviço de código  
  
1.  Criar uma instância do <xref:System.ServiceProcess.ServiceController> classe e configurá-lo para interagir com o serviço que você deseja administrar.  
  
2.  Chamar o <xref:System.ServiceProcess.ServiceController.Start%2A> método para iniciar o serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Como criar Serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Como adicionar instaladores no seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)

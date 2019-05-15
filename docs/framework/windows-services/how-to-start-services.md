---
title: 'Como: Iniciar serviços'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 8ad61eaa292ec4cce17ba029186caf1536afacdb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591453"
---
# <a name="how-to-start-services"></a>Como: Iniciar serviços
Depois que um serviço for instalado, ele precisará ser iniciado. O início chama o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> na classe de serviço. Normalmente, o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> define o trabalho útil que o serviço executará. Depois que um serviço é iniciado, ele permanece ativo até que ser colocado em pausa ou ser interrompido manualmente.  
  
 Os serviços podem ser configurados para serem iniciados automaticamente ou manualmente. Um serviço que é iniciado automaticamente será iniciado quando o computador no qual ele estiver instalado for reiniciado ou ligado pela primeira vez. Um serviço que é iniciado manualmente precisa ser iniciado por um usuário.  
  
> [!NOTE]
>  Por padrão, os serviços criados com o Visual Studio são definidos para serem iniciados manualmente.  
  
 Há várias maneiras de iniciar um serviço manualmente, por meio do **Gerenciador de Servidores**, do **Gerenciador de Controle de Serviços** ou do código usando um componente chamado <xref:System.ServiceProcess.ServiceController>.  
  
 Você define a propriedade <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> na classe <xref:System.ServiceProcess.ServiceInstaller> para determinar se um serviço deve ser iniciado manualmente ou automaticamente.  
  
### <a name="to-specify-how-a-service-should-start"></a>Para especificar como um serviço deve ser iniciado  
  
1. Depois de criar o serviço, adicione os instaladores necessários para ele. Para obter mais informações, confira [Como: Adicionar instaladores ao aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2. No designer, clique no instalador do serviço com o qual você está trabalhando.  
  
3. Na janela **Propriedades**, defina a propriedade <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> para uma das opções a seguir:  
  
    |Para que o serviço seja instalado|Defina esse valor|  
    |----------------------------------|--------------------|  
    |Quando o computador é reiniciado|**Automático**|  
    |Quando uma ação explícita do usuário inicia o serviço|**Manual**|  
  
    > [!TIP]
    >  Para impedir que o serviço seja iniciado, você pode definir a propriedade<xref:System.ServiceProcess.ServiceInstaller.StartType%2A> **Desabilitado**. Você poderá fazer isso quando pretender reiniciar um servidor várias vezes e desejar economizar tempo impedindo que sejam iniciados os serviços que normalmente seriam.  
  
    > [!NOTE]
    >  Essas e outras propriedades poderão ser alteradas depois que o serviço estiver instalado.  
  
     Há várias maneiras de iniciar um serviço que tenha o processo <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> definido como **Manual**, usando o **Gerenciador de Servidores**, o **Gerenciador de Controle de Serviços Windows** ou o código. É importante observar que nem todos esses métodos realmente iniciam o serviço no contexto do **Gerenciador de Controle de Serviços**. O **Gerenciador de Servidores** e os métodos programáticos de iniciar o serviço realmente manipulam o controlador.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>Para iniciar um serviço manualmente usando o Gerenciador de Servidores  
  
1. No **Gerenciador de Servidores**, adicione o servidor desejado caso ele ainda não esteja listado. Para obter mais informações, confira Como acessar e inicializar o Gerenciador de Servidores/Gerenciador de Banco de Dados.  
  
2. Expanda o nó **Serviços** e, em seguida, localize o serviço que você deseja iniciar.  
  
3. Clique com o botão direito do mouse no nome do serviço e, em seguida, clique em **Iniciar**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>Para iniciar um serviço manualmente usando o Gerenciador de Controle de Serviços  
  
1. Abra o **Gerenciador de Controle de Serviços** seguindo um destes procedimentos:  
  
    - No Windows XP e no 2000 Professional, clique com botão direito do mouse em **Meu Computador** na área de trabalho e, em seguida, clique em **Gerenciar**. Na caixa de diálogo que aparece, expanda o nó **Serviços e Aplicativos**.  
  
         \- ou -  
  
    - No Windows Server 2003 e no Windows 2000 Server, clique em **Iniciar**, aponte para **Programas**, clique em **Ferramentas Administrativas** e, em seguida, clique em **Serviços**.  
  
        > [!NOTE]
        >  No Windows NT versão 4.0, você pode abrir essa caixa de diálogo do **Painel de Controle**.  
  
     Agora o serviço deverá listado na seção **Serviços** da janela.  
  
2. Selecione o serviço na lista, clique nele com o botão direito do mouse e, em seguida, clique em **Iniciar**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Para iniciar um serviço manualmente usando código  
  
1. Crie uma instância da classe <xref:System.ServiceProcess.ServiceController> e configure-a para interagir com o serviço que você deseja administrar.  
  
2. Chame o método <xref:System.ServiceProcess.ServiceController.Start%2A> para iniciar o serviço.  
  
## <a name="see-also"></a>Consulte também

- [Introdução aos Aplicativos de Serviço Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Como: criar serviços do Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Como: adicionar instaladores ao aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)

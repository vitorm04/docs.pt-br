---
title: "Como iniciar serviços"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e4f93da8a2a5be00d798d64caba0f54bfd71ceb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-start-services"></a><span data-ttu-id="49248-102">Como iniciar serviços</span><span class="sxs-lookup"><span data-stu-id="49248-102">How to: Start Services</span></span>
<span data-ttu-id="49248-103">Depois que um serviço é instalado, ele deve ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="49248-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="49248-104">Iniciando chamadas de <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método na classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="49248-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="49248-105">Normalmente, o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método define o trabalho útil que o serviço irá executar.</span><span class="sxs-lookup"><span data-stu-id="49248-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="49248-106">Depois que um serviço é iniciado, ele permanece ativo até que seja pausado ou interrompido manualmente.</span><span class="sxs-lookup"><span data-stu-id="49248-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="49248-107">Services pode ser configurado para iniciar automaticamente ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="49248-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="49248-108">Um serviço que inicia automaticamente será iniciado quando o computador no qual ele está instalado é reinicializado ou é ligado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="49248-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="49248-109">Um usuário deve iniciar um serviço que inicia manualmente.</span><span class="sxs-lookup"><span data-stu-id="49248-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49248-110">Por padrão, os serviços criados com [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] estão definidos para iniciar manualmente.</span><span class="sxs-lookup"><span data-stu-id="49248-110">By default, services created with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] are set to start manually.</span></span>  
  
 <span data-ttu-id="49248-111">Há várias maneiras que você pode iniciar manualmente um serviço — de **Server Explorer**, do **Gerenciador de controle de serviços**, ou do código usando um componente denominado o <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="49248-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="49248-112">Definir o <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriedade o <xref:System.ServiceProcess.ServiceInstaller> classe para determinar se um serviço deve ser iniciado manualmente ou automaticamente.</span><span class="sxs-lookup"><span data-stu-id="49248-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="49248-113">Para especificar como um serviço deve ser iniciado</span><span class="sxs-lookup"><span data-stu-id="49248-113">To specify how a service should start</span></span>  
  
1.  <span data-ttu-id="49248-114">Depois de criar seu serviço, adicione os instaladores necessários para ele.</span><span class="sxs-lookup"><span data-stu-id="49248-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="49248-115">Para obter mais informações, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="49248-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="49248-116">No designer, clique o instalador de serviço para o serviço que você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="49248-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3.  <span data-ttu-id="49248-117">No **propriedades** janela, defina o <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriedade para um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="49248-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="49248-118">Para ter seu serviço instalado</span><span class="sxs-lookup"><span data-stu-id="49248-118">To have your service install</span></span>|<span data-ttu-id="49248-119">Definir esse valor</span><span class="sxs-lookup"><span data-stu-id="49248-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="49248-120">Quando o computador é reiniciado</span><span class="sxs-lookup"><span data-stu-id="49248-120">When the computer is restarted</span></span>|<span data-ttu-id="49248-121">**Automático**</span><span class="sxs-lookup"><span data-stu-id="49248-121">**Automatic**</span></span>|  
    |<span data-ttu-id="49248-122">Quando uma ação explícita do usuário inicia o serviço</span><span class="sxs-lookup"><span data-stu-id="49248-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="49248-123">**Manual**</span><span class="sxs-lookup"><span data-stu-id="49248-123">**Manual**</span></span>|  
  
    > [!TIP]
    >  <span data-ttu-id="49248-124">Para impedir que seu serviço seja iniciado, você pode definir o <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriedade **desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="49248-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="49248-125">Você pode fazer isso se você vai reiniciar um servidor várias vezes e deseja economizar tempo, impedindo que os serviços que normalmente seriam iniciados seja iniciado.</span><span class="sxs-lookup"><span data-stu-id="49248-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49248-126">Essas e outras propriedades podem ser alteradas depois que o serviço está instalado.</span><span class="sxs-lookup"><span data-stu-id="49248-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="49248-127">Há várias maneiras que você pode iniciar um serviço que tem seu <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> processo definido como **Manual** — de **Server Explorer**, do **Gerenciador de controle de serviços do Windows**, ou de código.</span><span class="sxs-lookup"><span data-stu-id="49248-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="49248-128">É importante observar que nem todos os métodos realmente iniciam o serviço no contexto do **Gerenciador de controle de serviços**; **Server Explorer** e métodos programáticos de iniciar o serviço realmente manipulam o controlador.</span><span class="sxs-lookup"><span data-stu-id="49248-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="49248-129">Para iniciar manualmente um serviço do Gerenciador de servidores</span><span class="sxs-lookup"><span data-stu-id="49248-129">To manually start a service from Server Explorer</span></span>  
  
1.  <span data-ttu-id="49248-130">Em **Server Explorer**, adicione o servidor que você deseja se ele não ainda esteja listado.</span><span class="sxs-lookup"><span data-stu-id="49248-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="49248-131">Para obter mais informações, consulte como: acesso e inicializar o Gerenciador de banco de dados do Gerenciador de servidores.</span><span class="sxs-lookup"><span data-stu-id="49248-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2.  <span data-ttu-id="49248-132">Expanda o **serviços** nó e, em seguida, localize o serviço que você deseja iniciar.</span><span class="sxs-lookup"><span data-stu-id="49248-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3.  <span data-ttu-id="49248-133">Clique no nome do serviço e, em seguida, clique em **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="49248-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="49248-134">Para iniciar manualmente um serviço do Gerenciador de controle de serviços</span><span class="sxs-lookup"><span data-stu-id="49248-134">To manually start a service from Services Control Manager</span></span>  
  
1.  <span data-ttu-id="49248-135">Abra o **Gerenciador de controle de serviços** seguindo um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="49248-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    -   <span data-ttu-id="49248-136">No Windows XP e 2000 Professional, clique com botão direito **meu computador** na área de trabalho e, em seguida, clique **gerenciar**.</span><span class="sxs-lookup"><span data-stu-id="49248-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="49248-137">Na caixa de diálogo que aparece, expanda o **serviços e aplicativos** nó.</span><span class="sxs-lookup"><span data-stu-id="49248-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="49248-138">\- ou -</span><span class="sxs-lookup"><span data-stu-id="49248-138">\- or -</span></span>  
  
    -   <span data-ttu-id="49248-139">No Windows Server 2003 e Windows 2000 Server, clique em **iniciar**, aponte para **programas**, clique em **ferramentas administrativas**e, em seguida, clique em **serviços**.</span><span class="sxs-lookup"><span data-stu-id="49248-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="49248-140">No Windows NT versão 4.0, você pode abrir essa caixa de diálogo de **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="49248-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="49248-141">Agora você deve ver seu serviço listado no **serviços** seção da janela.</span><span class="sxs-lookup"><span data-stu-id="49248-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2.  <span data-ttu-id="49248-142">Selecione o serviço na lista, clique duas vezes e, em seguida, clique em **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="49248-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="49248-143">Para iniciar manualmente um serviço de código</span><span class="sxs-lookup"><span data-stu-id="49248-143">To manually start a service from code</span></span>  
  
1.  <span data-ttu-id="49248-144">Criar uma instância do <xref:System.ServiceProcess.ServiceController> classe e configurá-lo para interagir com o serviço que você deseja administrar.</span><span class="sxs-lookup"><span data-stu-id="49248-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2.  <span data-ttu-id="49248-145">Chamar o <xref:System.ServiceProcess.ServiceController.Start%2A> método para iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="49248-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49248-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49248-146">See Also</span></span>  
 [<span data-ttu-id="49248-147">Introdução aos aplicativos de serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="49248-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="49248-148">Como: criar serviços do Windows</span><span class="sxs-lookup"><span data-stu-id="49248-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="49248-149">Como: adicionar instaladores ao seu aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="49248-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)

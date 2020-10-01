---
title: 'Como: Iniciar serviços'
description: Conheça várias maneiras de iniciar os serviços. Depois que um serviço for instalado, ele precisará ser iniciado. Iniciar chama o método OnStart na classe de serviço.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
ms.openlocfilehash: 1ca597379ab2a8fdae19fcfc5351c29d716753dc
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608407"
---
# <a name="how-to-start-services"></a><span data-ttu-id="d214c-105">Como: Iniciar serviços</span><span class="sxs-lookup"><span data-stu-id="d214c-105">How to: Start Services</span></span>

<span data-ttu-id="d214c-106">Depois que um serviço for instalado, ele precisará ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="d214c-106">After a service is installed, it must be started.</span></span> <span data-ttu-id="d214c-107">O início chama o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> na classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="d214c-107">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="d214c-108">Normalmente, o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> define o trabalho útil que o serviço executará.</span><span class="sxs-lookup"><span data-stu-id="d214c-108">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="d214c-109">Depois que um serviço é iniciado, ele permanece ativo até que ser colocado em pausa ou ser interrompido manualmente.</span><span class="sxs-lookup"><span data-stu-id="d214c-109">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="d214c-110">Os serviços podem ser configurados para serem iniciados automaticamente ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="d214c-110">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="d214c-111">Um serviço que é iniciado automaticamente será iniciado quando o computador no qual ele estiver instalado for reiniciado ou ligado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="d214c-111">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="d214c-112">Um serviço que é iniciado manualmente precisa ser iniciado por um usuário.</span><span class="sxs-lookup"><span data-stu-id="d214c-112">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="d214c-113">Por padrão, os serviços criados com o Visual Studio são definidos para serem iniciados manualmente.</span><span class="sxs-lookup"><span data-stu-id="d214c-113">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="d214c-114">Há várias maneiras de iniciar um serviço manualmente, por meio do **Gerenciador de Servidores**, do **Gerenciador de Controle de Serviços** ou do código usando um componente chamado <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="d214c-114">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="d214c-115">Você define a propriedade <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> na classe <xref:System.ServiceProcess.ServiceInstaller> para determinar se um serviço deve ser iniciado manualmente ou automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d214c-115">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="d214c-116">Para especificar como um serviço deve ser iniciado</span><span class="sxs-lookup"><span data-stu-id="d214c-116">To specify how a service should start</span></span>

1. <span data-ttu-id="d214c-117">Depois de criar o serviço, adicione os instaladores necessários para ele.</span><span class="sxs-lookup"><span data-stu-id="d214c-117">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="d214c-118">Para obter mais informações, confira [Como adicionar instaladores no seu aplicativo de serviço](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="d214c-118">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="d214c-119">No designer, clique no instalador do serviço com o qual você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="d214c-119">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="d214c-120">Na janela **Propriedades**, defina a propriedade <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> para uma das opções a seguir:</span><span class="sxs-lookup"><span data-stu-id="d214c-120">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="d214c-121">Para que o serviço seja instalado</span><span class="sxs-lookup"><span data-stu-id="d214c-121">To have your service install</span></span>|<span data-ttu-id="d214c-122">Defina esse valor</span><span class="sxs-lookup"><span data-stu-id="d214c-122">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="d214c-123">Quando o computador é reiniciado</span><span class="sxs-lookup"><span data-stu-id="d214c-123">When the computer is restarted</span></span>|<span data-ttu-id="d214c-124">**Automática**</span><span class="sxs-lookup"><span data-stu-id="d214c-124">**Automatic**</span></span>|
    |<span data-ttu-id="d214c-125">Quando uma ação explícita do usuário inicia o serviço</span><span class="sxs-lookup"><span data-stu-id="d214c-125">When an explicit user action starts the service</span></span>|<span data-ttu-id="d214c-126">**Manual**</span><span class="sxs-lookup"><span data-stu-id="d214c-126">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="d214c-127">Para impedir que o serviço seja iniciado, você pode definir a propriedade<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>**Desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="d214c-127">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="d214c-128">Você poderá fazer isso quando pretender reiniciar um servidor várias vezes e desejar economizar tempo impedindo que sejam iniciados os serviços que normalmente seriam.</span><span class="sxs-lookup"><span data-stu-id="d214c-128">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d214c-129">Essas e outras propriedades poderão ser alteradas depois que o serviço estiver instalado.</span><span class="sxs-lookup"><span data-stu-id="d214c-129">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="d214c-130">Há várias maneiras de iniciar um serviço que tenha o processo <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> definido como **Manual**, usando o **Gerenciador de Servidores**, o **Gerenciador de Controle de Serviços Windows** ou o código.</span><span class="sxs-lookup"><span data-stu-id="d214c-130">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="d214c-131">É importante observar que nem todos esses métodos realmente iniciam o serviço no contexto do **Gerenciador de Controle de Serviços**. O **Gerenciador de Servidores** e os métodos programáticos de iniciar o serviço realmente manipulam o controlador.</span><span class="sxs-lookup"><span data-stu-id="d214c-131">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="d214c-132">Para iniciar um serviço manualmente usando o Gerenciador de Servidores</span><span class="sxs-lookup"><span data-stu-id="d214c-132">To manually start a service from Server Explorer</span></span>

1. <span data-ttu-id="d214c-133">No **Gerenciador de Servidores**, adicione o servidor desejado caso ele ainda não esteja listado.</span><span class="sxs-lookup"><span data-stu-id="d214c-133">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="d214c-134">Para obter mais informações, consulte Como acessar e inicializar o Gerenciador de Servidores/Gerenciador de Banco de Dados.</span><span class="sxs-lookup"><span data-stu-id="d214c-134">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="d214c-135">Expanda o nó **Serviços** e, em seguida, localize o serviço que você deseja iniciar.</span><span class="sxs-lookup"><span data-stu-id="d214c-135">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="d214c-136">Clique com o botão direito do mouse no nome do serviço e, em seguida, clique em **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="d214c-136">Right-click the name of the service, and click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="d214c-137">Para iniciar um serviço manualmente usando o Gerenciador de Controle de Serviços</span><span class="sxs-lookup"><span data-stu-id="d214c-137">To manually start a service from Services Control Manager</span></span>

1. <span data-ttu-id="d214c-138">Abra o **Gerenciador de Controle de Serviços** seguindo um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="d214c-138">Open the **Services Control Manager** by doing one of the following:</span></span>

    - <span data-ttu-id="d214c-139">No Windows XP e no 2000 Professional, clique com botão direito do mouse em **Meu Computador** na área de trabalho e, em seguida, clique em **Gerenciar**.</span><span class="sxs-lookup"><span data-stu-id="d214c-139">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="d214c-140">Na caixa de diálogo que aparece, expanda o nó **Serviços e Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="d214c-140">In the dialog box that appears, expand the **Services and Applications** node.</span></span>

      <span data-ttu-id="d214c-141">\- ou –</span><span class="sxs-lookup"><span data-stu-id="d214c-141">\- or -</span></span>

    - <span data-ttu-id="d214c-142">No Windows Server 2003 e no Windows 2000 Server, clique em **Iniciar**, aponte para **Programas**, clique em **Ferramentas Administrativas** e, em seguida, clique em **Serviços**.</span><span class="sxs-lookup"><span data-stu-id="d214c-142">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="d214c-143">No Windows NT versão 4.0, você pode abrir essa caixa de diálogo do **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="d214c-143">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>

    <span data-ttu-id="d214c-144">Agora o serviço deverá listado na seção **Serviços** da janela.</span><span class="sxs-lookup"><span data-stu-id="d214c-144">You should now see your service listed in the **Services** section of the window.</span></span>

2. <span data-ttu-id="d214c-145">Selecione o serviço na lista, clique nele com o botão direito do mouse e, em seguida, clique em **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="d214c-145">Select your service in the list, right-click it, and then click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="d214c-146">Para iniciar um serviço manualmente usando código</span><span class="sxs-lookup"><span data-stu-id="d214c-146">To manually start a service from code</span></span>

1. <span data-ttu-id="d214c-147">Crie uma instância da classe <xref:System.ServiceProcess.ServiceController> e configure-a para interagir com o serviço que você deseja administrar.</span><span class="sxs-lookup"><span data-stu-id="d214c-147">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="d214c-148">Chame o método <xref:System.ServiceProcess.ServiceController.Start%2A> para iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="d214c-148">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="d214c-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="d214c-149">See also</span></span>

- [<span data-ttu-id="d214c-150">Introdução a aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="d214c-150">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="d214c-151">Como: Criar serviços Windows</span><span class="sxs-lookup"><span data-stu-id="d214c-151">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="d214c-152">Como: Adicionar instaladores ao aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="d214c-152">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)

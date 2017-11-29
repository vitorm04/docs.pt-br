---
title: "Como adicionar instaladores ao aplicativo de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 8137e41f92335849916dfc9e9ce72afeb186e73c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-installers-to-your-service-application"></a><span data-ttu-id="12ce8-102">Como adicionar instaladores ao aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="12ce8-102">How to: Add Installers to Your Service Application</span></span>
<span data-ttu-id="12ce8-103">O Visual Studio possui componentes de instalação que podem instalar recursos associados com seus aplicativos de serviço.</span><span class="sxs-lookup"><span data-stu-id="12ce8-103">Visual Studio ships installation components that can install resources associated with your service applications.</span></span> <span data-ttu-id="12ce8-104">Componentes de instalação registram um serviço individual no sistema ao qual ele está sendo instalado e informe o Gerenciador de controle de serviços que o serviço existe.</span><span class="sxs-lookup"><span data-stu-id="12ce8-104">Installation components register an individual service on the system to which it is being installed and let the Services Control Manager know that the service exists.</span></span> <span data-ttu-id="12ce8-105">Quando você trabalha com um aplicativo de serviço, você pode selecionar um link na janela Propriedades para adicionar automaticamente os instaladores apropriados ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="12ce8-105">When you work with a service application, you can select a link in the Properties window to automatically add the appropriate installers to your project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12ce8-106">Valores de propriedade para o serviço são copiados da classe de serviço para a classe de instalador.</span><span class="sxs-lookup"><span data-stu-id="12ce8-106">Property values for your service are copied from the service class to the installer class.</span></span> <span data-ttu-id="12ce8-107">Se você atualizar os valores de propriedade na classe de serviço, eles não são atualizados automaticamente no instalador.</span><span class="sxs-lookup"><span data-stu-id="12ce8-107">If you update the property values on the service class, they are not automatically updated in the installer.</span></span>  
  
 <span data-ttu-id="12ce8-108">Quando você adiciona um instalador para seu projeto, uma nova classe (que, por padrão, é chamado `ProjectInstaller`) é criado no projeto e instâncias da instalação apropriada componentes são criados dentro dele.</span><span class="sxs-lookup"><span data-stu-id="12ce8-108">When you add an installer to your project, a new class (which, by default, is named `ProjectInstaller`) is created in the project, and instances of the appropriate installation components are created within it.</span></span> <span data-ttu-id="12ce8-109">Esta classe age como um ponto central para todos os componentes de instalação precisa de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="12ce8-109">This class acts as a central point for all of the installation components your project needs.</span></span> <span data-ttu-id="12ce8-110">Por exemplo, se você adicionar um segundo serviço para seu aplicativo e clique no link Adicionar instalador, uma segunda classe de instalador não é criada; em vez disso, o componente de instalação adicional necessário para o segundo serviço é adicionado à classe existente.</span><span class="sxs-lookup"><span data-stu-id="12ce8-110">For example, if you add a second service to your application and click the Add Installer link, a second installer class is not created; instead, the necessary additional installation component for the second service is added to the existing class.</span></span>  
  
 <span data-ttu-id="12ce8-111">Você não precisa fazer qualquer codificação especial dentro dos instaladores para fazer seus serviços instalarem corretamente.</span><span class="sxs-lookup"><span data-stu-id="12ce8-111">You do not need to do any special coding within the installers to make your services install correctly.</span></span> <span data-ttu-id="12ce8-112">No entanto, ocasionalmente, convém modificar o conteúdo dos instaladores se você precisa adicionar uma funcionalidade especial para o processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="12ce8-112">However, you may occasionally need to modify the contents of the installers if you need to add special functionality to the installation process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12ce8-113">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="12ce8-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="12ce8-114">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="12ce8-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="12ce8-115">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="12ce8-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-installers-to-your-service-application"></a><span data-ttu-id="12ce8-116">Para adicionar instaladores ao seu aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="12ce8-116">To add installers to your service application</span></span>  
  
1.  <span data-ttu-id="12ce8-117">Em **Solution Explorer**, acesso **Design** exibição para o serviço para o qual você deseja adicionar um componente de instalação.</span><span class="sxs-lookup"><span data-stu-id="12ce8-117">In **Solution Explorer**, access **Design** view for the service for which you want to add an installation component.</span></span>  
  
2.  <span data-ttu-id="12ce8-118">Clique em plano de fundo do designer para selecionar o serviço propriamente dito, em vez de um de seus conteúdos.</span><span class="sxs-lookup"><span data-stu-id="12ce8-118">Click the background of the designer to select the service itself, rather than any of its contents.</span></span>  
  
3.  <span data-ttu-id="12ce8-119">Com o designer em foco, o botão direito do mouse e clique **adicionar instalador**.</span><span class="sxs-lookup"><span data-stu-id="12ce8-119">With the designer in focus, right-click, and then click **Add Installer**.</span></span>  
  
     <span data-ttu-id="12ce8-120">Uma nova classe, `ProjectInstaller`e dois componentes de instalação, <xref:System.ServiceProcess.ServiceProcessInstaller> e <xref:System.ServiceProcess.ServiceInstaller>, são adicionados ao seu projeto e valores de propriedade para o serviço são copiados para os componentes.</span><span class="sxs-lookup"><span data-stu-id="12ce8-120">A new class, `ProjectInstaller`, and two installation components, <xref:System.ServiceProcess.ServiceProcessInstaller> and <xref:System.ServiceProcess.ServiceInstaller>, are added to your project, and property values for the service are copied to the components.</span></span>  
  
4.  <span data-ttu-id="12ce8-121">Clique o <xref:System.ServiceProcess.ServiceInstaller> componente e verificar se o valor da <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> propriedade é definida como o mesmo valor que o <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> propriedade no próprio serviço.</span><span class="sxs-lookup"><span data-stu-id="12ce8-121">Click the <xref:System.ServiceProcess.ServiceInstaller> component and verify that the value of the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to the same value as the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property on the service itself.</span></span>  
  
5.  <span data-ttu-id="12ce8-122">Para determinar como seu serviço será iniciado, clique o <xref:System.ServiceProcess.ServiceInstaller> componente e defina o <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriedade para o valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="12ce8-122">To determine how your service will be started, click the <xref:System.ServiceProcess.ServiceInstaller> component and set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to the appropriate value.</span></span>  
  
    |<span data-ttu-id="12ce8-123">Valor</span><span class="sxs-lookup"><span data-stu-id="12ce8-123">Value</span></span>|<span data-ttu-id="12ce8-124">Resultado</span><span class="sxs-lookup"><span data-stu-id="12ce8-124">Result</span></span>|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|<span data-ttu-id="12ce8-125">O serviço deve ser iniciado manualmente após a instalação.</span><span class="sxs-lookup"><span data-stu-id="12ce8-125">The service must be manually started after installation.</span></span> <span data-ttu-id="12ce8-126">Para obter mais informações, consulte [como: iniciar os serviços](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="12ce8-126">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|<span data-ttu-id="12ce8-127">O serviço será iniciado por si só, sempre que o computador é reinicializado.</span><span class="sxs-lookup"><span data-stu-id="12ce8-127">The service will start by itself whenever the computer reboots.</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|<span data-ttu-id="12ce8-128">O serviço não pode ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="12ce8-128">The service cannot be started.</span></span>|  
  
6.  <span data-ttu-id="12ce8-129">Para determinar o contexto de segurança no qual seu serviço será executado, clique o <xref:System.ServiceProcess.ServiceProcessInstaller> componente e defina os valores de propriedade apropriada.</span><span class="sxs-lookup"><span data-stu-id="12ce8-129">To determine the security context in which your service will run, click the <xref:System.ServiceProcess.ServiceProcessInstaller> component and set the appropriate property values.</span></span> <span data-ttu-id="12ce8-130">Para obter mais informações, consulte [como: especificar o contexto de segurança para serviços](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).</span><span class="sxs-lookup"><span data-stu-id="12ce8-130">For more information, see [How to: Specify the Security Context for Services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).</span></span>  
  
7.  <span data-ttu-id="12ce8-131">Substitua todos os métodos para os quais você precisa realizar processamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="12ce8-131">Override any methods for which you need to perform custom processing.</span></span>  
  
8.  <span data-ttu-id="12ce8-132">Execute as etapas 1 a 7 para cada serviço adicional em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="12ce8-132">Perform steps 1 through 7 for each additional service in your project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12ce8-133">Para cada serviço adicional em seu projeto, você deve adicionar adicional <xref:System.ServiceProcess.ServiceInstaller> componente para o projeto `ProjectInstaller` classe.</span><span class="sxs-lookup"><span data-stu-id="12ce8-133">For each additional service in your project, you must add an additional <xref:System.ServiceProcess.ServiceInstaller> component to the project's `ProjectInstaller` class.</span></span> <span data-ttu-id="12ce8-134">O <xref:System.ServiceProcess.ServiceProcessInstaller> componente adicionado na etapa três funciona com todos os instaladores de serviço individuais no projeto.</span><span class="sxs-lookup"><span data-stu-id="12ce8-134">The <xref:System.ServiceProcess.ServiceProcessInstaller> component added in step three works with all of the individual service installers in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ce8-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12ce8-135">See Also</span></span>  
 [<span data-ttu-id="12ce8-136">Introdução aos aplicativos de serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="12ce8-136">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="12ce8-137">Como: instalar e desinstalar serviços</span><span class="sxs-lookup"><span data-stu-id="12ce8-137">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="12ce8-138">Como: iniciar serviços</span><span class="sxs-lookup"><span data-stu-id="12ce8-138">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="12ce8-139">Como: especificar o contexto de segurança para serviços</span><span class="sxs-lookup"><span data-stu-id="12ce8-139">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)

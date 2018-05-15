---
title: Como escrever serviços de forma programática
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
manager: douge
ms.openlocfilehash: 99fd44723bba21127e2a5e0ba3e9bfc4b90b52d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="f6aff-102">Como escrever serviços de forma programática</span><span class="sxs-lookup"><span data-stu-id="f6aff-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="f6aff-103">Se você optar por não usar o modelo de projeto de serviço do Windows, você pode escrever seus próprios serviços, configurando a herança e outros elementos de infraestrutura por conta própria.</span><span class="sxs-lookup"><span data-stu-id="f6aff-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="f6aff-104">Quando você cria um serviço programaticamente, você deve executar várias etapas que o modelo trataria para você:</span><span class="sxs-lookup"><span data-stu-id="f6aff-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
-   <span data-ttu-id="f6aff-105">Você deve configurar sua classe de serviço herde o <xref:System.ServiceProcess.ServiceBase> classe.</span><span class="sxs-lookup"><span data-stu-id="f6aff-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
-   <span data-ttu-id="f6aff-106">Você deve criar um `Main` método para seu projeto de serviço que define os serviços a executar e chama o <xref:System.ServiceProcess.ServiceBase.Run%2A> método neles.</span><span class="sxs-lookup"><span data-stu-id="f6aff-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
-   <span data-ttu-id="f6aff-107">Você deve substituir o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedimentos e preencha qualquer código que você deseja executá-los.</span><span class="sxs-lookup"><span data-stu-id="f6aff-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="f6aff-108">Escrever um serviço por meio de programação</span><span class="sxs-lookup"><span data-stu-id="f6aff-108">To write a service programmatically</span></span>  
  
1.  <span data-ttu-id="f6aff-109">Criar um projeto vazio e criar uma referência aos namespaces necessários seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="f6aff-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1.  <span data-ttu-id="f6aff-110">Em **Solution Explorer**, com o botão direito do **referências** nó e clique em **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="f6aff-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="f6aff-111">Sobre o **do .NET Framework** guia, role até **System.dll** e clique em **selecione**.</span><span class="sxs-lookup"><span data-stu-id="f6aff-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3.  <span data-ttu-id="f6aff-112">Role até **System.ServiceProcess.dll** e clique em **selecione**.</span><span class="sxs-lookup"><span data-stu-id="f6aff-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4.  <span data-ttu-id="f6aff-113">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="f6aff-113">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="f6aff-114">Adicionar uma classe e configurá-lo para herdar de <xref:System.ServiceProcess.ServiceBase>:</span><span class="sxs-lookup"><span data-stu-id="f6aff-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  <span data-ttu-id="f6aff-115">Adicione o código a seguir para configurar sua classe de serviço:</span><span class="sxs-lookup"><span data-stu-id="f6aff-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  <span data-ttu-id="f6aff-116">Criar um `Main` método para sua classe e usá-lo para definir o serviço que sua classe irá conter; `userService1` é o nome da classe:</span><span class="sxs-lookup"><span data-stu-id="f6aff-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  <span data-ttu-id="f6aff-117">Substituir o <xref:System.ServiceProcess.ServiceBase.OnStart%2A> método e defina qualquer processamento que deve ocorrer quando o serviço é iniciado.</span><span class="sxs-lookup"><span data-stu-id="f6aff-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  <span data-ttu-id="f6aff-118">Substitua quaisquer outros métodos que você deseja definir processamento personalizado e escrever código para determinar as ações que o serviço deve tomar em cada caso.</span><span class="sxs-lookup"><span data-stu-id="f6aff-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7.  <span data-ttu-id="f6aff-119">Adicionar os instaladores necessários para seu aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="f6aff-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="f6aff-120">Para obter mais informações, consulte [como: adicionar instaladores ao seu aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="f6aff-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8.  <span data-ttu-id="f6aff-121">Compilar o projeto selecionando **compilar solução** do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="f6aff-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f6aff-122">Pressione F5 para executar seu projeto. Você não pode executar um projeto de serviço dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="f6aff-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="f6aff-123">Crie um projeto de instalação e as ações personalizadas para instalar o serviço.</span><span class="sxs-lookup"><span data-stu-id="f6aff-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="f6aff-124">Para obter um exemplo, consulte [passo a passo: Criando um aplicativo de serviço do Windows no Designer de componente](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="f6aff-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="f6aff-125">Instale o serviço.</span><span class="sxs-lookup"><span data-stu-id="f6aff-125">Install the service.</span></span> <span data-ttu-id="f6aff-126">Para obter mais informações, consulte [como: instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="f6aff-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6aff-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6aff-127">See Also</span></span>  
 [<span data-ttu-id="f6aff-128">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="f6aff-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="f6aff-129">Como criar Serviços do Windows</span><span class="sxs-lookup"><span data-stu-id="f6aff-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="f6aff-130">Como adicionar instaladores no seu aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="f6aff-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="f6aff-131">Como registrar informações sobre serviços</span><span class="sxs-lookup"><span data-stu-id="f6aff-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="f6aff-132">Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes</span><span class="sxs-lookup"><span data-stu-id="f6aff-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

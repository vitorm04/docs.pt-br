---
title: 'Como: Escrever serviços de forma programática'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: e709db257c839dc7e583412a87af6d25b80de969
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591426"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="ae0e3-102">Como: Escrever serviços de forma programática</span><span class="sxs-lookup"><span data-stu-id="ae0e3-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="ae0e3-103">Quando você opta por não usar o modelo de projeto de Serviço Windows, é possível escrever seus próprios serviços configurando a herança e outros elementos de infraestrutura por conta própria.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="ae0e3-104">Ao criar um serviço de forma programática, você precisa executar várias etapas que o modelo executaria para você:</span><span class="sxs-lookup"><span data-stu-id="ae0e3-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="ae0e3-105">Você precisa configurar a classe de serviço para ser herdada da classe <xref:System.ServiceProcess.ServiceBase>.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="ae0e3-106">Você precisa criar um método `Main` para seu projeto de serviço que defina os serviços a serem executados e chame o método <xref:System.ServiceProcess.ServiceBase.Run%2A>neles.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="ae0e3-107">Você precisa substituir os procedimentos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A> e preencher os códigos que desejar que eles executem.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="ae0e3-108">Para escrever um serviço de forma programático</span><span class="sxs-lookup"><span data-stu-id="ae0e3-108">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="ae0e3-109">Criar um projeto vazio e crie uma referência aos namespaces necessários seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="ae0e3-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="ae0e3-110">Em **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** e clique em **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="ae0e3-111">Na guia **.NET Framework**, role até **System.dll** e clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="ae0e3-112">Role até **System.ServiceProcess.dll** e clique em **Selecionar**.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="ae0e3-113">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-113">Click **OK**.</span></span>  
  
2. <span data-ttu-id="ae0e3-114">Adicione uma classe e configure-a para ser herdada de <xref:System.ServiceProcess.ServiceBase>:</span><span class="sxs-lookup"><span data-stu-id="ae0e3-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="ae0e3-115">Adicione o código a seguir para configurar sua classe de serviço:</span><span class="sxs-lookup"><span data-stu-id="ae0e3-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="ae0e3-116">Crie um método `Main` para sua classe e use-o para definir o serviço que a classe conterá. `userService1` é o nome da classe:</span><span class="sxs-lookup"><span data-stu-id="ae0e3-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="ae0e3-117">Substitua o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e defina o processamento que deverá ocorrer quando o serviço for iniciado.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="ae0e3-118">Substitua quaisquer outros métodos para os quais deseje definir um processamento personalizado e escreva o código para determinar as ações que o serviço deve executar em cada caso.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="ae0e3-119">Adicionar os instaladores necessários para seu aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="ae0e3-120">Para obter mais informações, confira [Como: Adicionar instaladores ao aplicativo de serviço](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="ae0e3-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="ae0e3-121">Compile o projeto selecionando **Compilar Solução** no menu **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ae0e3-122">Pressione F5 para executar seu projeto. Você não pode executar um projeto de serviço dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="ae0e3-123">Crie um projeto de instalação e as ações personalizadas para instalar o serviço.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="ae0e3-124">Para obter um exemplo, confira [Passo a passo: criando um aplicativo de serviço Windows no Designer de Componentes](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="ae0e3-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="ae0e3-125">Instale o serviço.</span><span class="sxs-lookup"><span data-stu-id="ae0e3-125">Install the service.</span></span> <span data-ttu-id="ae0e3-126">Para obter mais informações, confira [Como: Instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="ae0e3-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0e3-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae0e3-127">See also</span></span>

- [<span data-ttu-id="ae0e3-128">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="ae0e3-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="ae0e3-129">Como: criar serviços do Windows</span><span class="sxs-lookup"><span data-stu-id="ae0e3-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="ae0e3-130">Como: adicionar instaladores ao aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="ae0e3-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="ae0e3-131">Como: Registrar em log informações sobre serviços</span><span class="sxs-lookup"><span data-stu-id="ae0e3-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [<span data-ttu-id="ae0e3-132">Passo a passo: Criando um aplicativo de serviço Windows no Designer de Componentes</span><span class="sxs-lookup"><span data-stu-id="ae0e3-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

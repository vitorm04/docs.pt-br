---
title: Desenvolvendo aplicativos do Serviço Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: 18
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cc01c836daa73b1a39ceab0b523791b6a520dc70
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="18094-102">Desenvolvendo aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="18094-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="18094-103">Usando o Microsoft Visual Studio ou o Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, você pode criar serviços facilmente, criando um aplicativo que é instalado como um serviço.</span><span class="sxs-lookup"><span data-stu-id="18094-103">Using Microsoft Visual Studio or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="18094-104">Esse tipo de aplicativo é chamado um serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="18094-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="18094-105">Com recursos de estrutura, você pode criar serviços, instalá-los, iniciar, interromper e controlar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="18094-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="18094-106">O modelo de serviço do Windows para C++ não foi incluído no Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="18094-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="18094-107">Para criar um serviço do Windows, você pode criar um serviço em código gerenciado em Visual c# ou Visual Basic, que pode interagir com o código C++ existente se necessário, ou você pode criar um serviço do Windows em C++ nativo usando o [Assistente de projeto de ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="18094-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18094-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="18094-108">In This Section</span></span>  
 [<span data-ttu-id="18094-109">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="18094-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="18094-110">Fornece uma visão geral de aplicativos de serviço do Windows, o tempo de vida de um serviço e como aplicativos de serviço diferem de outros tipos de projeto comum.</span><span class="sxs-lookup"><span data-stu-id="18094-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="18094-111">Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes</span><span class="sxs-lookup"><span data-stu-id="18094-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="18094-112">Fornece um exemplo de como criar um serviço no Visual Basic e Visual c#.</span><span class="sxs-lookup"><span data-stu-id="18094-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>  
  
 [<span data-ttu-id="18094-113">Arquitetura de programação de aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="18094-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="18094-114">Explica os elementos de linguagem usados em programação de serviço.</span><span class="sxs-lookup"><span data-stu-id="18094-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="18094-115">Como criar Serviços do Windows</span><span class="sxs-lookup"><span data-stu-id="18094-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="18094-116">Descreve o processo de criação e configuração de serviços do Windows usando o modelo de projeto de serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="18094-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="18094-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="18094-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="18094-118">Descreve os principais recursos da <xref:System.ServiceProcess.ServiceBase> classe, que é usada para criar serviços.</span><span class="sxs-lookup"><span data-stu-id="18094-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="18094-119">Descreve os recursos do <xref:System.ServiceProcess.ServiceProcessInstaller> classe, que é usada junto com o <xref:System.ServiceProcess.ServiceInstaller> classe para instalar e desinstalar seus serviços.</span><span class="sxs-lookup"><span data-stu-id="18094-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="18094-120">Descreve os recursos do <xref:System.ServiceProcess.ServiceInstaller> classe, que é usada junto com o <xref:System.ServiceProcess.ServiceProcessInstaller> classe para instalar e desinstalar o serviço.</span><span class="sxs-lookup"><span data-stu-id="18094-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="18094-121">NIB criar projetos de modelos</span><span class="sxs-lookup"><span data-stu-id="18094-121">NIB Creating Projects from Templates</span></span>](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="18094-122">Descreve os projetos de tipos usados neste capítulo e como escolher entre eles.</span><span class="sxs-lookup"><span data-stu-id="18094-122">Describes the projects types used in this chapter and how to choose between them.</span></span>

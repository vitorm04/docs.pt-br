---
title: Desenvolvendo aplicativos do Serviço Windows
description: Consulte links para artigos que explicam como desenvolver aplicativos de serviço do Windows usando o Visual Studio ou o SDK do .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
ms.openlocfilehash: 2aea73267f05340930a9591f430de59677c1cb11
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609571"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="3280e-103">Desenvolver aplicativos de serviço Windows</span><span class="sxs-lookup"><span data-stu-id="3280e-103">Develop Windows service apps</span></span>

<span data-ttu-id="3280e-104">Usando o Visual Studio ou o SDK do .NET Framework, você pode criar serviços facilmente criando um aplicativo que é instalado como um serviço.</span><span class="sxs-lookup"><span data-stu-id="3280e-104">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="3280e-105">Esse tipo de aplicativo é chamado de um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="3280e-105">This type of application is called a Windows service.</span></span> <span data-ttu-id="3280e-106">Com recursos de estrutura, você pode criar serviços, instalá-los, iniciar, interromper e controlar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="3280e-106">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="3280e-107">No Visual Studio, você pode criar um serviço em código gerenciado em Visual C# ou Visual Basic, que podem interoperar com o código C++ existente se necessário.</span><span class="sxs-lookup"><span data-stu-id="3280e-107">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="3280e-108">Ou você pode criar um serviço Windows em C++ nativo usando o [Assistente de Projeto ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="3280e-108">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3280e-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3280e-109">In this section</span></span>

[<span data-ttu-id="3280e-110">Introdução a aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="3280e-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="3280e-111">Fornece uma visão geral de aplicativos de serviço Windows, o tempo de vida de um serviço e como aplicativos de serviço diferem de outros tipos de projeto comum.</span><span class="sxs-lookup"><span data-stu-id="3280e-111">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="3280e-112">Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes</span><span class="sxs-lookup"><span data-stu-id="3280e-112">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="3280e-113">Fornece um exemplo de como criar um serviço no Visual Basic e Visual C#.</span><span class="sxs-lookup"><span data-stu-id="3280e-113">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="3280e-114">Arquitetura de programação do aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="3280e-114">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="3280e-115">Explica os elementos de linguagem usados na programação de serviço.</span><span class="sxs-lookup"><span data-stu-id="3280e-115">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="3280e-116">Como: Criar serviços Windows</span><span class="sxs-lookup"><span data-stu-id="3280e-116">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="3280e-117">Descreve o processo de criação e configuração de serviços Windows usando o modelo de projeto de serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="3280e-117">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="3280e-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="3280e-118">Related sections</span></span>

<span data-ttu-id="3280e-119"><xref:System.ServiceProcess.ServiceBase> – Descreve os principais recursos da classe <xref:System.ServiceProcess.ServiceBase>, que é usada para criar serviços.</span><span class="sxs-lookup"><span data-stu-id="3280e-119"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="3280e-120"><xref:System.ServiceProcess.ServiceProcessInstaller> – Descreve os recursos da classe <xref:System.ServiceProcess.ServiceProcessInstaller>, que é usada junto com a classe <xref:System.ServiceProcess.ServiceInstaller> para instalar e desinstalar o serviço.</span><span class="sxs-lookup"><span data-stu-id="3280e-120"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="3280e-121"><xref:System.ServiceProcess.ServiceInstaller> – Descreve os recursos da classe <xref:System.ServiceProcess.ServiceInstaller>, que é usada junto com a classe <xref:System.ServiceProcess.ServiceProcessInstaller> para instalar e desinstalar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="3280e-121"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="3280e-122">[Criar projetos de modelos](/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) – descreve os projetos de tipos usados neste capítulo e como escolher entre eles.</span><span class="sxs-lookup"><span data-stu-id="3280e-122">[Create Projects from Templates](/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>

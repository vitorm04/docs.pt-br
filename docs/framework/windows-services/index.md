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
author: ghogen
ms.openlocfilehash: ed02d523c21c51df2ed886843fdb71c075c93c30
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925690"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="4952d-103">Desenvolver aplicativos de serviço Windows</span><span class="sxs-lookup"><span data-stu-id="4952d-103">Develop Windows service apps</span></span>

<span data-ttu-id="4952d-104">Usando o Visual Studio ou o SDK do .NET Framework, você pode criar serviços facilmente criando um aplicativo que é instalado como um serviço.</span><span class="sxs-lookup"><span data-stu-id="4952d-104">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="4952d-105">Esse tipo de aplicativo é chamado de um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="4952d-105">This type of application is called a Windows service.</span></span> <span data-ttu-id="4952d-106">Com recursos de estrutura, você pode criar serviços, instalá-los, iniciar, interromper e controlar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="4952d-106">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="4952d-107">No Visual Studio, você pode criar um serviço em código gerenciado em Visual C# ou Visual Basic, que podem interoperar com o código C++ existente se necessário.</span><span class="sxs-lookup"><span data-stu-id="4952d-107">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="4952d-108">Ou você pode criar um serviço Windows em C++ nativo usando o [Assistente de Projeto ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="4952d-108">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4952d-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4952d-109">In this section</span></span>

[<span data-ttu-id="4952d-110">Introdução a aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="4952d-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="4952d-111">Fornece uma visão geral de aplicativos de serviço Windows, o tempo de vida de um serviço e como aplicativos de serviço diferem de outros tipos de projeto comum.</span><span class="sxs-lookup"><span data-stu-id="4952d-111">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="4952d-112">Passo a passo: criando um aplicativo de Serviço Windows no Designer de componentes</span><span class="sxs-lookup"><span data-stu-id="4952d-112">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="4952d-113">Fornece um exemplo de como criar um serviço no Visual Basic e Visual C#.</span><span class="sxs-lookup"><span data-stu-id="4952d-113">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="4952d-114">Arquitetura de programação do aplicativo de serviço</span><span class="sxs-lookup"><span data-stu-id="4952d-114">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="4952d-115">Explica os elementos de linguagem usados na programação de serviço.</span><span class="sxs-lookup"><span data-stu-id="4952d-115">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="4952d-116">Como: Criar serviços Windows</span><span class="sxs-lookup"><span data-stu-id="4952d-116">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="4952d-117">Descreve o processo de criação e configuração de serviços Windows usando o modelo de projeto de serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="4952d-117">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4952d-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="4952d-118">Related sections</span></span>

<span data-ttu-id="4952d-119"><xref:System.ServiceProcess.ServiceBase> – Descreve os principais recursos da classe <xref:System.ServiceProcess.ServiceBase>, que é usada para criar serviços.</span><span class="sxs-lookup"><span data-stu-id="4952d-119"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="4952d-120"><xref:System.ServiceProcess.ServiceProcessInstaller> – Descreve os recursos da classe <xref:System.ServiceProcess.ServiceProcessInstaller>, que é usada junto com a classe <xref:System.ServiceProcess.ServiceInstaller> para instalar e desinstalar o serviço.</span><span class="sxs-lookup"><span data-stu-id="4952d-120"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="4952d-121"><xref:System.ServiceProcess.ServiceInstaller> – Descreve os recursos da classe <xref:System.ServiceProcess.ServiceInstaller>, que é usada junto com a classe <xref:System.ServiceProcess.ServiceProcessInstaller> para instalar e desinstalar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="4952d-121"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="4952d-122">[Criar projetos de modelos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) – descreve os projetos de tipos usados neste capítulo e como escolher entre eles.</span><span class="sxs-lookup"><span data-stu-id="4952d-122">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>

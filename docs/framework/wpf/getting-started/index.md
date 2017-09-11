---
title: "Introdução (WPF) | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF, getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
caps.latest.revision: 60
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 83c9c6fc754bcee3bb3a893ca21be21d169226cf
ms.contentlocale: pt-br
ms.lasthandoff: 05/02/2017

---
# <a name="getting-started-wpf"></a><span data-ttu-id="7dfe5-102">Introdução (WPF)</span><span class="sxs-lookup"><span data-stu-id="7dfe5-102">Getting Started (WPF)</span></span>
<span data-ttu-id="7dfe5-103">O Windows Presentation Foundation (WPF) é uma estrutura de interface do usuário que cria aplicativos cliente da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="7dfe5-104">A plataforma de desenvolvimento WPF dá suporte a um amplo conjunto de funcionalidades de desenvolvimento de aplicativos, incluindo um modelo de aplicativo, funcionalidades, controles, elementos gráficos, layout, vinculação de dados, documentos e segurança.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="7dfe5-105">Ele é um subconjunto do .NET Framework, portanto, se você tiver criado anteriormente aplicativos com o .NET Framework usando ASP.NET ou Windows Forms, a experiência de programação deverá ser familiar.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="7dfe5-106">O WPF usa a linguagem XAML para fornecer um modelo declarativo para programação de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="7dfe5-107">Esta seção apresenta tópicos que servem como introdução e lhe ajudarão a começar a usar o WPF.</span><span class="sxs-lookup"><span data-stu-id="7dfe5-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="7dfe5-108">Onde devo começar?</span><span class="sxs-lookup"><span data-stu-id="7dfe5-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7dfe5-109">Desejo ir diretamente para…</span><span class="sxs-lookup"><span data-stu-id="7dfe5-109">I want to jump right in…</span></span>|[<span data-ttu-id="7dfe5-110">Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF</span><span class="sxs-lookup"><span data-stu-id="7dfe5-110">Walkthrough: My First WPF Desktop Application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="7dfe5-111">Como criar a interface do usuário do aplicativo?</span><span class="sxs-lookup"><span data-stu-id="7dfe5-111">How do I design the application UI?</span></span>|[<span data-ttu-id="7dfe5-112">Criando o XAML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7dfe5-112">Designing XAML in Visual Studio</span></span>](http://msdn.microsoft.com/library/288e2415-9fcf-408e-bc35-9848315e14fd)|  
|<span data-ttu-id="7dfe5-113">Novo no .NET?</span><span class="sxs-lookup"><span data-stu-id="7dfe5-113">New to .NET?</span></span>|<span data-ttu-id="7dfe5-114">[Visão geral do .NET Framework](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7dfe5-114">[Overview of the .NET Framework](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span></span><br /><br /> [<span data-ttu-id="7dfe5-115">Fundamentos do aplicativo .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7dfe5-115">.NET Framework Application Essentials</span></span>](../../../../docs/standard/application-essentials.md)<br /><br /> <span data-ttu-id="7dfe5-116">[Introdução ao Visual C# e ao Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7dfe5-116">[Getting Started with Visual C# and Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span></span>|  
|<span data-ttu-id="7dfe5-117">Quero saber mais sobre o WPF…</span><span class="sxs-lookup"><span data-stu-id="7dfe5-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="7dfe5-118">Introdução ao WPF no Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="7dfe5-118">Introduction to WPF in Visual Studio 2015</span></span>](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="7dfe5-119">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="7dfe5-119">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="7dfe5-120">Controles</span><span class="sxs-lookup"><span data-stu-id="7dfe5-120">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)<br /><br /> [<span data-ttu-id="7dfe5-121">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="7dfe5-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="7dfe5-122">Você é um desenvolvedor de Windows Forms?</span><span class="sxs-lookup"><span data-stu-id="7dfe5-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="7dfe5-123">Controles dos Windows Forms e controles WPF equivalentes</span><span class="sxs-lookup"><span data-stu-id="7dfe5-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="7dfe5-124">Interoperação do WPF e do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7dfe5-124">WPF and Windows Forms Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="7dfe5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7dfe5-125">See Also</span></span>  
 <span data-ttu-id="7dfe5-126">[Biblioteca de classes](../../../../docs/framework/wpf/class-library-wpf.md) </span><span class="sxs-lookup"><span data-stu-id="7dfe5-126">[Class Library](../../../../docs/framework/wpf/class-library-wpf.md) </span></span>  
<span data-ttu-id="7dfe5-127"> [Desenvolvimento do aplicativo](../../../../docs/framework/wpf/app-development/index.md) </span><span class="sxs-lookup"><span data-stu-id="7dfe5-127"> [Application Development](../../../../docs/framework/wpf/app-development/index.md) </span></span>  
<span data-ttu-id="7dfe5-128"> [Central de desenvolvedores do .NET Framework](http://go.microsoft.com/fwlink/?LinkId=187437)</span><span class="sxs-lookup"><span data-stu-id="7dfe5-128"> [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=187437)</span></span>

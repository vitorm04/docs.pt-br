---
title: Implementando aplicativos cliente com o .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client application services
- applications [Windows Forms]
- Windows Presentation Foundation, in Visual Studio
- WPF, in Visual Studio
- Windows applications
- rich client applications
- .NET applications, Windows applications
- Visual Basic code, creating applications
- Visual C#, creating applications
- client/server applications, Windows applications
ms.assetid: 2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: daf09f94b4c0854365274773f8c426cc07e8c6dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="6354a-102">Implementando aplicativos cliente com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6354a-102">Developing Client Applications with the .NET Framework</span></span>
<span data-ttu-id="6354a-103">Há várias maneiras de desenvolver aplicativos baseados no Windows com o .NET Framework que são executados localmente nos computadores ou dispositivos dos usuários.</span><span class="sxs-lookup"><span data-stu-id="6354a-103">There are multiple ways to develop Windows-based applications with the .NET framework that run locally on users' computers or devices.</span></span> <span data-ttu-id="6354a-104">Esta seção contém tópicos que descrevem como criar aplicativos baseados no Windows usando o WPF (Windows Presentation Foundation) ou o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6354a-104">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation (WPF) or by using Windows Forms.</span></span> <span data-ttu-id="6354a-105">No entanto, você pode também usar o .NET Framework para criar aplicativos Web e aplicativos cliente para computadores ou dispositivos que depois pode disponibilizar pela Windows Store e pela Loja do Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="6354a-105">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Windows Store or Windows Phone Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6354a-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6354a-106">In This Section</span></span>  
 [<span data-ttu-id="6354a-107">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="6354a-107">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
 <span data-ttu-id="6354a-108">Fornece informações sobre como desenvolver aplicativos usando o WPF.</span><span class="sxs-lookup"><span data-stu-id="6354a-108">Provides information about developing applications by using WPF.</span></span>  
  
 [<span data-ttu-id="6354a-109">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6354a-109">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
 <span data-ttu-id="6354a-110">Fornece informações sobre como desenvolver aplicativos usando o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6354a-110">Provides information about developing applications by using Windows Forms.</span></span>  
  
 [<span data-ttu-id="6354a-111">Tecnologias comuns de cliente</span><span class="sxs-lookup"><span data-stu-id="6354a-111">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
 <span data-ttu-id="6354a-112">Fornece informações sobre tecnologias adicionais que podem ser usadas durante o desenvolvimento de aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="6354a-112">Provides information about additional technologies that can be used when developing client applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6354a-113">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="6354a-113">Related Sections</span></span>  
 [<span data-ttu-id="6354a-114">Aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="6354a-114">Windows Store apps</span></span>](http://msdn.microsoft.com/windows/apps/)  
 <span data-ttu-id="6354a-115">Descreve como criar aplicativos que você pode disponibilizar aos usuários pela Windows Store</span><span class="sxs-lookup"><span data-stu-id="6354a-115">Describes how to create apps that you can make available to users through the Windows Store</span></span>  
  
 [<span data-ttu-id="6354a-116">.NET para aplicativos da Store</span><span class="sxs-lookup"><span data-stu-id="6354a-116">.NET for Store apps</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 <span data-ttu-id="6354a-117">Descreve o suporte do .NET Framework para aplicativos da Store, que podem ser implantados em computadores e dispositivos com Windows.</span><span class="sxs-lookup"><span data-stu-id="6354a-117">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>  
  
 <span data-ttu-id="6354a-118">[API do .NET para Windows Phone Silverlight](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="6354a-118">[.NET API for Windows Phone Silverlight](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span></span>  
 <span data-ttu-id="6354a-119">Lista as APIs do .NET Framework que você pode usar para criar aplicativos com o Windows Phone Silverlight</span><span class="sxs-lookup"><span data-stu-id="6354a-119">List the .NET Framework APIs you can use for building apps with Windows Phone Silverlight</span></span>  
  
 [<span data-ttu-id="6354a-120">Desenvolvimento para várias plataformas</span><span class="sxs-lookup"><span data-stu-id="6354a-120">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="6354a-121">Descreve os diferentes métodos que você pode usar o .NET Framework para visar vários tipos de aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="6354a-121">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>  
  
 [<span data-ttu-id="6354a-122">Introdução aos sites ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6354a-122">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
 <span data-ttu-id="6354a-123">Descreve de que maneiras você pode desenvolver aplicativos Web usando ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6354a-123">Describes the ways you can develop web apps using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6354a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6354a-124">See Also</span></span>  
 [<span data-ttu-id="6354a-125">Biblioteca de classes portátil</span><span class="sxs-lookup"><span data-stu-id="6354a-125">Portable Class Library</span></span>](../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)  
 [<span data-ttu-id="6354a-126">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="6354a-126">Overview</span></span>](../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="6354a-127">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="6354a-127">Development Guide</span></span>](../../docs/framework/development-guide.md)  
 [<span data-ttu-id="6354a-128">Como: criar um aplicativo de área de trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="6354a-128">How to: Create a Windows Desktop Application</span></span>](http://msdn.microsoft.com/library/47021403-eaca-4c34-946a-a26c42a64148)  
 [<span data-ttu-id="6354a-129">Aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="6354a-129">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)

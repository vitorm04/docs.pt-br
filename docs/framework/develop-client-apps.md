---
title: Desenvolvendo aplicativos cliente baseados em Windows com o .NET Framework
ms.date: 01/09/2018
ms.prod: .net-framework
ms.technology:
- dotnet-clr
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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cfc8a0f176e3732e7fe6f088c9973bfbcdaf89a
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="289a7-102">Desenvolvendo aplicativos cliente com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="289a7-102">Developing client applications with the .NET Framework</span></span>

<span data-ttu-id="289a7-103">Há várias maneiras para desenvolver aplicativos baseados em Windows com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="289a7-103">There are several ways to develop Windows-based applications with the .NET Framework.</span></span> <span data-ttu-id="289a7-104">Você pode usar qualquer uma destas ferramentas e estruturas:</span><span class="sxs-lookup"><span data-stu-id="289a7-104">You can use any of these tools and frameworks:</span></span> 

* [<span data-ttu-id="289a7-105">UWP (Plataforma Universal do Windows)</span><span class="sxs-lookup"><span data-stu-id="289a7-105">Universal Windows Platform (UWP)</span></span>](https://developer.microsoft.com/windows/apps)
* [<span data-ttu-id="289a7-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="289a7-106">Windows Presentation Foundation (WPF)</span></span>](../../docs/framework/wpf/index.md)
* [<span data-ttu-id="289a7-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="289a7-107">Windows Forms</span></span>](../../docs/framework/winforms/index.md)

<span data-ttu-id="289a7-108">Esta seção contém tópicos que descrevem como criar aplicativos baseados no Windows usando o Windows Presentation Foundation ou o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="289a7-108">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation or by using Windows Forms.</span></span> <span data-ttu-id="289a7-109">No entanto, você pode também usar o .NET Framework para criar aplicativos Web e aplicativos cliente para computadores ou dispositivos que depois pode disponibilizar pela Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="289a7-109">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Microsoft Store.</span></span>
 
## <a name="in-this-section"></a><span data-ttu-id="289a7-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="289a7-110">In this section</span></span>

[<span data-ttu-id="289a7-111">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="289a7-111">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
<span data-ttu-id="289a7-112">Fornece informações sobre como desenvolver aplicativos usando o WPF.</span><span class="sxs-lookup"><span data-stu-id="289a7-112">Provides information about developing applications by using WPF.</span></span>

[<span data-ttu-id="289a7-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="289a7-113">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
<span data-ttu-id="289a7-114">Fornece informações sobre como desenvolver aplicativos usando o Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="289a7-114">Provides information about developing applications by using Windows Forms.</span></span>

[<span data-ttu-id="289a7-115">Tecnologias comuns de cliente</span><span class="sxs-lookup"><span data-stu-id="289a7-115">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
<span data-ttu-id="289a7-116">Fornece informações sobre tecnologias adicionais que podem ser usadas durante o desenvolvimento de aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="289a7-116">Provides information about additional technologies that can be used when developing client applications.</span></span>

## <a name="related-sections"></a><span data-ttu-id="289a7-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="289a7-117">Related sections</span></span>

[<span data-ttu-id="289a7-118">Plataforma Universal do Windows</span><span class="sxs-lookup"><span data-stu-id="289a7-118">Universal Windows Platform</span></span>](https://developer.microsoft.com/windows/apps)  
<span data-ttu-id="289a7-119">Descreve como criar aplicativos para Windows 10 que você pode disponibilizar aos usuários pela Windows Store.</span><span class="sxs-lookup"><span data-stu-id="289a7-119">Describes how to create applications for Windows 10 that you can make available to users through the Windows Store.</span></span>

[<span data-ttu-id="289a7-120">.NET para aplicativos UWP</span><span class="sxs-lookup"><span data-stu-id="289a7-120">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)  
<span data-ttu-id="289a7-121">Descreve o suporte do .NET Framework para aplicativos da Store, que podem ser implantados em computadores e dispositivos com Windows.</span><span class="sxs-lookup"><span data-stu-id="289a7-121">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>

<span data-ttu-id="289a7-122">[API do .NET para Windows Phone Silverlight](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="289a7-122">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>  
<span data-ttu-id="289a7-123">Lista as APIs do .NET Framework que você pode usar para criar aplicativos com o Windows Phone Silverlight.</span><span class="sxs-lookup"><span data-stu-id="289a7-123">Lists the .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>
  
[<span data-ttu-id="289a7-124">Desenvolvimento para várias plataformas</span><span class="sxs-lookup"><span data-stu-id="289a7-124">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
<span data-ttu-id="289a7-125">Descreve os diferentes métodos que você pode usar o .NET Framework para visar vários tipos de aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="289a7-125">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>

[<span data-ttu-id="289a7-126">Introdução aos sites ASP.NET</span><span class="sxs-lookup"><span data-stu-id="289a7-126">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
<span data-ttu-id="289a7-127">Descreve de que maneiras você pode desenvolver aplicativos Web usando ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="289a7-127">Describes the ways you can develop web apps using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="289a7-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="289a7-128">See also</span></span>

[<span data-ttu-id="289a7-129">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="289a7-129">.NET Standard</span></span>](../../docs/standard/net-standard.md)  
[<span data-ttu-id="289a7-130">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="289a7-130">Overview</span></span>](../../docs/framework/get-started/overview.md)  
[<span data-ttu-id="289a7-131">Guia de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="289a7-131">Development Guide</span></span>](../../docs/framework/development-guide.md)  
[<span data-ttu-id="289a7-132">Aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="289a7-132">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  

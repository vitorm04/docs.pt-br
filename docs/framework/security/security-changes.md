---
title: Alterações na segurança do .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61f9e68bcc554dc3e4a4878e575d3f046a8ef9f5
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378599"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="fa446-102">Alterações na segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fa446-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="fa446-103">A alteração mais importante para a segurança no .NET Framework 4.5 é de nomenclatura forte.</span><span class="sxs-lookup"><span data-stu-id="fa446-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="fa446-104">Consulte [Nomenclatura forte aprimorada](../../../docs/framework/app-domains/enhanced-strong-naming.md) para obter uma descrição dessas alterações.</span><span class="sxs-lookup"><span data-stu-id="fa446-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="fa446-105">O .NET Framework fornece um modelo de duas camadas de segurança para aplicativos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="fa446-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> <span data-ttu-id="fa446-106">Aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] executados em um contêiner de segurança do Windows que limita o acesso aos recursos.</span><span class="sxs-lookup"><span data-stu-id="fa446-106">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="fa446-107">Dentro desse contêiner, os aplicativos gerenciados são executados de modo totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="fa446-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="fa446-108">De uma perspectiva de CAS (segurança de acesso de código), não há nada que um desenvolvedor possa fazer para elevar privilégios.</span><span class="sxs-lookup"><span data-stu-id="fa446-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="fa446-109">Para obter informações sobre os privilégios concedidos pelo Windows, consulte [Declarações de funcionalidades do aplicativo (Aplicativos da Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) no Centro de Desenvolvimento do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa446-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="fa446-110">Para obter informações sobre como criar um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo, consulte [Criar seu primeiro aplicativo da Windows Store usando C# ou Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="fa446-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>

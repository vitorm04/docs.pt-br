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
ms.openlocfilehash: f4cf91924e762495df6787a187e4295b69f2cd96
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045371"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="23c24-102">Alterações na segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="23c24-102">Security Changes in the .NET Framework</span></span>

<span data-ttu-id="23c24-103">A alteração mais importante na segurança no .NET Framework 4,5 está na nomeação forte.</span><span class="sxs-lookup"><span data-stu-id="23c24-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="23c24-104">Consulte [Nomenclatura forte aprimorada](../../standard/assembly/enhanced-strong-naming.md) para obter uma descrição dessas alterações.</span><span class="sxs-lookup"><span data-stu-id="23c24-104">See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
<span data-ttu-id="23c24-105">O .NET Framework fornece um modelo de duas camadas de segurança para aplicativos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="23c24-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> <span data-ttu-id="23c24-106">Aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] executados em um contêiner de segurança do Windows que limita o acesso aos recursos.</span><span class="sxs-lookup"><span data-stu-id="23c24-106">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="23c24-107">Dentro desse contêiner, os aplicativos gerenciados são executados de modo totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="23c24-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="23c24-108">De uma perspectiva de CAS (segurança de acesso de código), não há nada que um desenvolvedor possa fazer para elevar privilégios.</span><span class="sxs-lookup"><span data-stu-id="23c24-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="23c24-109">Para obter informações sobre os privilégios concedidos pelo Windows, consulte [Declarações de funcionalidades do aplicativo (Aplicativos da Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) no Centro de Desenvolvimento do Windows.</span><span class="sxs-lookup"><span data-stu-id="23c24-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="23c24-110">Para obter informações sobre como criar um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo, consulte [Criar seu primeiro aplicativo da Windows Store usando C# ou Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="23c24-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>

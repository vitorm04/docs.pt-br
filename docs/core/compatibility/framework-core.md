---
title: Alterações significativas, .NET Framework no .NET Core 3,0-.NET Core
description: Lista as alterações significativas de .NET Framework para o .NET Core 3,0 para Windows Forms e Windows Presentation Foundation.
ms.date: 09/10/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c658c5bce7a2554bba83f2779a73d9d6af01a342
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71151528"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core-30"></a><span data-ttu-id="d2cd4-103">Alterações recentes de migração do .NET Framework para o .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="d2cd4-103">Breaking changes for migration from .NET Framework to .NET Core 3.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2cd4-104">Este artigo está em construção.</span><span class="sxs-lookup"><span data-stu-id="d2cd4-104">This article is under construction.</span></span> <span data-ttu-id="d2cd4-105">Esta não é uma lista completa de alterações significativas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2cd4-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="d2cd4-106">Para obter mais informações sobre as alterações significativas no .NET Core, você pode examinar os problemas individuais de [alterações significativas](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) no repositório dotnet/docs no github.</span><span class="sxs-lookup"><span data-stu-id="d2cd4-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span> 

<span data-ttu-id="d2cd4-107">Se você estiver migrando um aplicativo Windows Forms ou Windows Presentation Foundation do .NET Framework para o .NET Core 3,0, examine os seguintes tópicos para obter alterações significativas que possam afetar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="d2cd4-107">If you are migrating a Windows Forms or Windows Presentation Foundation application from .NET Framework to .NET Core 3.0, review the following topics for breaking changes that may affect your app:</span></span>

## <a name="windows-forms"></a><span data-ttu-id="d2cd4-108">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d2cd4-108">Windows Forms</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyimages.md)]

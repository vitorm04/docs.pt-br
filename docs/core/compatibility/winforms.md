---
title: Windows Forms alterações significativas-.NET Core
description: Lista as alterações significativas no Windows Forms para .NET Core.
ms.date: 09/20/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ca02e41039fa5c7a6f7f6a9e303ea25be55977a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003009"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="7bc30-103">Alterações recentes no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7bc30-103">Breaking changes in Windows Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7bc30-104">Este artigo está em construção.</span><span class="sxs-lookup"><span data-stu-id="7bc30-104">This article is under construction.</span></span> <span data-ttu-id="7bc30-105">Esta não é uma lista completa de alterações significativas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7bc30-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="7bc30-106">Para obter mais informações sobre as alterações significativas no .NET Core, você pode examinar os problemas individuais de [alterações significativas](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) no repositório dotnet/docs no github.</span><span class="sxs-lookup"><span data-stu-id="7bc30-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span>

<span data-ttu-id="7bc30-107">Veja a seguir uma lista de alterações significativas no Windows Forms pela versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7bc30-107">The following is a list of breaking changes in Windows Forms by .NET Core version.</span></span>

## <a name="net-core-30-preview-9"></a><span data-ttu-id="7bc30-108">.NET Core 3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="7bc30-108">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyimages.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/remove-serializationattribute.md)]

## <a name="net-core-30-rc1"></a><span data-ttu-id="7bc30-109">.NET Core 3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="7bc30-109">.NET Core 3.0 RC1</span></span>

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/remove-duplicated-apis.md)]

## <a name="net-core-30"></a><span data-ttu-id="7bc30-110">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7bc30-110">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/modernized-folderbrowserdialog.md)]

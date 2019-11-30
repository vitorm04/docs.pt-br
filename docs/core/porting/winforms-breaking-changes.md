---
title: Alterações recentes para WinForms-.NET Framework para o .NET Core
description: Lista as alterações significativas do .NET Framework para o .NET Core para aplicativos Windows Forms.
ms.date: 11/27/2019
ms.openlocfilehash: cc1f319dcc83a633c81c49195d743784fe5916d9
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643973"
---
# <a name="breaking-changes-in-windows-forms-net-framework-to-net-core"></a><span data-ttu-id="4a5e8-103">Alterações recentes no Windows Forms (.NET Framework para .NET Core)</span><span class="sxs-lookup"><span data-stu-id="4a5e8-103">Breaking changes in Windows Forms (.NET Framework to .NET Core)</span></span>

<span data-ttu-id="4a5e8-104">O suporte ao WPF e ao Windows Forms foi adicionado ao .NET Core na versão 3,0.</span><span class="sxs-lookup"><span data-stu-id="4a5e8-104">WPF and Windows Forms support were added to .NET Core in version 3.0.</span></span> <span data-ttu-id="4a5e8-105">Se você estiver migrando um aplicativo Windows Forms ou Windows Presentation Foundation do .NET Framework para o .NET Core, as alterações significativas listadas neste artigo poderão afetar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a5e8-105">If you're migrating a Windows Forms or Windows Presentation Foundation app from .NET Framework to .NET Core, the breaking changes listed in this article may affect your app.</span></span>

<span data-ttu-id="4a5e8-106">Alterações significativas são agrupadas pela versão do .NET Core na qual foram introduzidas.</span><span class="sxs-lookup"><span data-stu-id="4a5e8-106">Breaking changes are grouped by the .NET Core version in which they were introduced.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="4a5e8-107">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="4a5e8-107">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

## <a name="net-core-30"></a><span data-ttu-id="4a5e8-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4a5e8-108">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

## <a name="see-also"></a><span data-ttu-id="4a5e8-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a5e8-109">See also</span></span>

- [<span data-ttu-id="4a5e8-110">Avaliar alterações da falha no .NET Core</span><span class="sxs-lookup"><span data-stu-id="4a5e8-110">Evaluate breaking changes in .NET Core</span></span>](../compatibility/index.md)
- [<span data-ttu-id="4a5e8-111">Alterações recentes no Windows Forms (.NET Core para .NET Core)</span><span class="sxs-lookup"><span data-stu-id="4a5e8-111">Breaking changes in Windows Forms (.NET Core to .NET Core)</span></span>](../compatibility/winforms.md)

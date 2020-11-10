---
title: Windows Forms alterações significativas
description: Lista as alterações significativas em Windows Forms para .NET Core e .NET 5.
ms.date: 09/08/2020
ms.openlocfilehash: c79fd28b5c3b81ae7ddf1ef3f470601108b87705
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440784"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="d3df8-103">Alterações recentes no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3df8-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="d3df8-104">Windows Forms suporte foi adicionado ao .NET Core na versão 3,0.</span><span class="sxs-lookup"><span data-stu-id="d3df8-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="d3df8-105">Este artigo lista as alterações significativas para Windows Forms pela versão do .NET na qual elas foram introduzidas.</span><span class="sxs-lookup"><span data-stu-id="d3df8-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="d3df8-106">Se você estiver atualizando um aplicativo Windows Forms de .NET Framework ou de uma versão anterior do .NET Core (3,0 ou posterior), este artigo se aplicará a você.</span><span class="sxs-lookup"><span data-stu-id="d3df8-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="d3df8-107">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="d3df8-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d3df8-108">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="d3df8-108">Breaking change</span></span> | <span data-ttu-id="d3df8-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d3df8-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="d3df8-110">TextFormatFlags. Modifystring é obsoleto</span><span class="sxs-lookup"><span data-stu-id="d3df8-110">TextFormatFlags.ModifyString is obsolete</span></span>](#textformatflagsmodifystring-is-obsolete) | <span data-ttu-id="d3df8-111">5.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-111">5.0</span></span> |
| [<span data-ttu-id="d3df8-112">DataGridView não redefine mais as fontes para estilos de célula personalizados</span><span class="sxs-lookup"><span data-stu-id="d3df8-112">DataGridView no longer resets fonts for customized cell styles</span></span>](#datagridview-no-longer-resets-fonts-for-customized-cell-styles) | <span data-ttu-id="d3df8-113">5.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-113">5.0</span></span> |
| [<span data-ttu-id="d3df8-114">OutputType definido como WinExe para aplicativos WPF e WinForms</span><span class="sxs-lookup"><span data-stu-id="d3df8-114">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="d3df8-115">5.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-115">5.0</span></span> |
| [<span data-ttu-id="d3df8-116">APIs relacionadas a DataGridView agora lança InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="d3df8-116">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="d3df8-117">5.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-117">5.0</span></span> |
| [<span data-ttu-id="d3df8-118">Os aplicativos WinForms e WPF usam Microsoft. NET. Sdk</span><span class="sxs-lookup"><span data-stu-id="d3df8-118">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="d3df8-119">5.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-119">5.0</span></span> |
| [<span data-ttu-id="d3df8-120">Controles da barra de status removidos</span><span class="sxs-lookup"><span data-stu-id="d3df8-120">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="d3df8-121">5.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-121">5.0</span></span> |
| [<span data-ttu-id="d3df8-122">Os métodos WinForms agora lançam ArgumentException</span><span class="sxs-lookup"><span data-stu-id="d3df8-122">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="d3df8-123">5.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-123">5.0</span></span> |
| [<span data-ttu-id="d3df8-124">Os métodos WinForms agora lançam ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="d3df8-124">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="d3df8-125">5.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-125">5.0</span></span> |
| [<span data-ttu-id="d3df8-126">As propriedades do WinForms agora geram ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="d3df8-126">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="d3df8-127">5.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-127">5.0</span></span> |
| [<span data-ttu-id="d3df8-128">Controles removidos</span><span class="sxs-lookup"><span data-stu-id="d3df8-128">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="d3df8-129">3.1</span><span class="sxs-lookup"><span data-stu-id="d3df8-129">3.1</span></span> |
| [<span data-ttu-id="d3df8-130">Evento CellFormatting não gerado se ToolTip for mostrado</span><span class="sxs-lookup"><span data-stu-id="d3df8-130">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="d3df8-131">3.1</span><span class="sxs-lookup"><span data-stu-id="d3df8-131">3.1</span></span> |
| [<span data-ttu-id="d3df8-132">Control. DefaultFont alterado para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="d3df8-132">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="d3df8-133">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-133">3.0</span></span> |
| [<span data-ttu-id="d3df8-134">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="d3df8-134">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="d3df8-135">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-135">3.0</span></span> |
| [<span data-ttu-id="d3df8-136">SerializableAttribute removido de alguns tipos de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3df8-136">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="d3df8-137">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-137">3.0</span></span> |
| [<span data-ttu-id="d3df8-138">Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="d3df8-138">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="d3df8-139">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-139">3.0</span></span> |
| [<span data-ttu-id="d3df8-140">Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling</span><span class="sxs-lookup"><span data-stu-id="d3df8-140">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="d3df8-141">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-141">3.0</span></span> |
| [<span data-ttu-id="d3df8-142">Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="d3df8-142">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="d3df8-143">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-143">3.0</span></span> |
| [<span data-ttu-id="d3df8-144">Não há suporte para a opção de compatibilidade DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="d3df8-144">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="d3df8-145">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-145">3.0</span></span> |
| [<span data-ttu-id="d3df8-146">Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="d3df8-146">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="d3df8-147">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-147">3.0</span></span> |
| [<span data-ttu-id="d3df8-148">Não há suporte para a opção de compatibilidade EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="d3df8-148">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="d3df8-149">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-149">3.0</span></span> |
| [<span data-ttu-id="d3df8-150">Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="d3df8-150">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="d3df8-151">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-151">3.0</span></span> |
| [<span data-ttu-id="d3df8-152">Não há suporte para a opção de compatibilidade UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="d3df8-152">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="d3df8-153">3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-153">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="d3df8-154">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d3df8-154">.NET 5.0</span></span>

[!INCLUDE [modifystring-field-of-textformatflags-obsolete](../../../includes/core-changes/windowsforms/5.0/modifystring-field-of-textformatflags-obsolete.md)]

***

[!INCLUDE [datagridview-doesnt-reset-custom-font-settings](../../../includes/core-changes/windowsforms/5.0/datagridview-doesnt-reset-custom-font-settings.md)]

<span data-ttu-id="d3df8-155">\*\*_</span><span class="sxs-lookup"><span data-stu-id="d3df8-155">\*\*_</span></span>

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

_*_

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

_*_

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

_*_

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

_*_

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

_*_

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

_*_

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

_*_

## <a name="net-core-31"></a><span data-ttu-id="d3df8-156">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="d3df8-156">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

_*_

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="d3df8-157">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d3df8-157">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

_*_

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

_*_

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

<span data-ttu-id="d3df8-158">_\*\*</span><span class="sxs-lookup"><span data-stu-id="d3df8-158">_\*\*</span></span>

## <a name="see-also"></a><span data-ttu-id="d3df8-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="d3df8-159">See also</span></span>

- [<span data-ttu-id="d3df8-160">Porta um aplicativo de Windows Forms para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="d3df8-160">Port a Windows Forms app to .NET Core</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)

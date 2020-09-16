---
title: Windows Forms alterações significativas
description: Lista as alterações significativas em Windows Forms para .NET Core e .NET 5.
ms.date: 09/08/2020
ms.openlocfilehash: 3e7d077d07203d9c231ae4a7805e593c5432c135
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678988"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="571f4-103">Alterações recentes no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="571f4-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="571f4-104">Windows Forms suporte foi adicionado ao .NET Core na versão 3,0.</span><span class="sxs-lookup"><span data-stu-id="571f4-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="571f4-105">Este artigo lista as alterações significativas para Windows Forms pela versão do .NET na qual elas foram introduzidas.</span><span class="sxs-lookup"><span data-stu-id="571f4-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="571f4-106">Se você estiver atualizando um aplicativo Windows Forms de .NET Framework ou de uma versão anterior do .NET Core (3,0 ou posterior), este artigo se aplicará a você.</span><span class="sxs-lookup"><span data-stu-id="571f4-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="571f4-107">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="571f4-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="571f4-108">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="571f4-108">Breaking change</span></span> | <span data-ttu-id="571f4-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="571f4-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="571f4-110">OutputType definido como WinExe para aplicativos WPF e WinForms</span><span class="sxs-lookup"><span data-stu-id="571f4-110">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="571f4-111">5,0</span><span class="sxs-lookup"><span data-stu-id="571f4-111">5.0</span></span> |
| [<span data-ttu-id="571f4-112">APIs relacionadas a DataGridView agora lança InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="571f4-112">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="571f4-113">5,0</span><span class="sxs-lookup"><span data-stu-id="571f4-113">5.0</span></span> |
| [<span data-ttu-id="571f4-114">Os aplicativos WinForms e WPF usam Microsoft. NET. Sdk</span><span class="sxs-lookup"><span data-stu-id="571f4-114">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="571f4-115">5,0</span><span class="sxs-lookup"><span data-stu-id="571f4-115">5.0</span></span> |
| [<span data-ttu-id="571f4-116">Controles da barra de status removidos</span><span class="sxs-lookup"><span data-stu-id="571f4-116">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="571f4-117">5,0</span><span class="sxs-lookup"><span data-stu-id="571f4-117">5.0</span></span> |
| [<span data-ttu-id="571f4-118">Os métodos WinForms agora lançam ArgumentException</span><span class="sxs-lookup"><span data-stu-id="571f4-118">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="571f4-119">5,0</span><span class="sxs-lookup"><span data-stu-id="571f4-119">5.0</span></span> |
| [<span data-ttu-id="571f4-120">Os métodos WinForms agora lançam ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="571f4-120">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="571f4-121">5,0</span><span class="sxs-lookup"><span data-stu-id="571f4-121">5.0</span></span> |
| [<span data-ttu-id="571f4-122">As propriedades do WinForms agora geram ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="571f4-122">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="571f4-123">5,0</span><span class="sxs-lookup"><span data-stu-id="571f4-123">5.0</span></span> |
| [<span data-ttu-id="571f4-124">Controles removidos</span><span class="sxs-lookup"><span data-stu-id="571f4-124">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="571f4-125">3.1</span><span class="sxs-lookup"><span data-stu-id="571f4-125">3.1</span></span> |
| [<span data-ttu-id="571f4-126">Evento CellFormatting não gerado se ToolTip for mostrado</span><span class="sxs-lookup"><span data-stu-id="571f4-126">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="571f4-127">3.1</span><span class="sxs-lookup"><span data-stu-id="571f4-127">3.1</span></span> |
| [<span data-ttu-id="571f4-128">Control. DefaultFont alterado para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="571f4-128">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="571f4-129">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-129">3.0</span></span> |
| [<span data-ttu-id="571f4-130">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="571f4-130">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="571f4-131">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-131">3.0</span></span> |
| [<span data-ttu-id="571f4-132">SerializableAttribute removido de alguns tipos de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="571f4-132">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="571f4-133">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-133">3.0</span></span> |
| [<span data-ttu-id="571f4-134">Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="571f4-134">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="571f4-135">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-135">3.0</span></span> |
| [<span data-ttu-id="571f4-136">Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling</span><span class="sxs-lookup"><span data-stu-id="571f4-136">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="571f4-137">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-137">3.0</span></span> |
| [<span data-ttu-id="571f4-138">Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="571f4-138">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="571f4-139">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-139">3.0</span></span> |
| [<span data-ttu-id="571f4-140">Não há suporte para a opção de compatibilidade DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="571f4-140">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="571f4-141">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-141">3.0</span></span> |
| [<span data-ttu-id="571f4-142">Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="571f4-142">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="571f4-143">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-143">3.0</span></span> |
| [<span data-ttu-id="571f4-144">Não há suporte para a opção de compatibilidade EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="571f4-144">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="571f4-145">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-145">3.0</span></span> |
| [<span data-ttu-id="571f4-146">Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="571f4-146">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="571f4-147">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-147">3.0</span></span> |
| [<span data-ttu-id="571f4-148">Não há suporte para a opção de compatibilidade UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="571f4-148">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="571f4-149">3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-149">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="571f4-150">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="571f4-150">.NET 5.0</span></span>

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

***

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

***

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

***

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="571f4-151">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="571f4-151">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="571f4-152">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="571f4-152">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="571f4-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="571f4-153">See also</span></span>

- [<span data-ttu-id="571f4-154">Porta um aplicativo de Windows Forms para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="571f4-154">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)

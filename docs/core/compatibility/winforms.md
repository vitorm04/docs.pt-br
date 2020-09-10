---
title: Windows Forms alterações significativas
description: Lista as alterações significativas em Windows Forms para .NET Core e .NET 5.
ms.date: 09/08/2020
ms.openlocfilehash: c3d2d23601d6a2d9d44761c4371fe34d3d5ed1f3
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656321"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="29eb9-103">Alterações recentes no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29eb9-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="29eb9-104">Windows Forms suporte foi adicionado ao .NET Core na versão 3,0.</span><span class="sxs-lookup"><span data-stu-id="29eb9-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="29eb9-105">Este artigo lista as alterações significativas para Windows Forms pela versão do .NET na qual elas foram introduzidas.</span><span class="sxs-lookup"><span data-stu-id="29eb9-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="29eb9-106">Se você estiver atualizando um aplicativo Windows Forms de .NET Framework ou de uma versão anterior do .NET Core (3,0 ou posterior), este artigo se aplicará a você.</span><span class="sxs-lookup"><span data-stu-id="29eb9-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="29eb9-107">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="29eb9-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="29eb9-108">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="29eb9-108">Breaking change</span></span> | <span data-ttu-id="29eb9-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="29eb9-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="29eb9-110">APIs relacionadas a DataGridView agora lança InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="29eb9-110">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="29eb9-111">5,0</span><span class="sxs-lookup"><span data-stu-id="29eb9-111">5.0</span></span> |
| [<span data-ttu-id="29eb9-112">Os aplicativos WinForms e WPF usam Microsoft. NET. Sdk</span><span class="sxs-lookup"><span data-stu-id="29eb9-112">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="29eb9-113">5,0</span><span class="sxs-lookup"><span data-stu-id="29eb9-113">5.0</span></span> |
| [<span data-ttu-id="29eb9-114">Controles da barra de status removidos</span><span class="sxs-lookup"><span data-stu-id="29eb9-114">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="29eb9-115">5,0</span><span class="sxs-lookup"><span data-stu-id="29eb9-115">5.0</span></span> |
| [<span data-ttu-id="29eb9-116">Os métodos WinForms agora lançam ArgumentException</span><span class="sxs-lookup"><span data-stu-id="29eb9-116">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="29eb9-117">5,0</span><span class="sxs-lookup"><span data-stu-id="29eb9-117">5.0</span></span> |
| [<span data-ttu-id="29eb9-118">Os métodos WinForms agora lançam ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="29eb9-118">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="29eb9-119">5,0</span><span class="sxs-lookup"><span data-stu-id="29eb9-119">5.0</span></span> |
| [<span data-ttu-id="29eb9-120">As propriedades do WinForms agora geram ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="29eb9-120">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="29eb9-121">5,0</span><span class="sxs-lookup"><span data-stu-id="29eb9-121">5.0</span></span> |
| [<span data-ttu-id="29eb9-122">Controles removidos</span><span class="sxs-lookup"><span data-stu-id="29eb9-122">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="29eb9-123">3.1</span><span class="sxs-lookup"><span data-stu-id="29eb9-123">3.1</span></span> |
| [<span data-ttu-id="29eb9-124">Evento CellFormatting não gerado se ToolTip for mostrado</span><span class="sxs-lookup"><span data-stu-id="29eb9-124">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="29eb9-125">3.1</span><span class="sxs-lookup"><span data-stu-id="29eb9-125">3.1</span></span> |
| [<span data-ttu-id="29eb9-126">Control. DefaultFont alterado para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="29eb9-126">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="29eb9-127">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-127">3.0</span></span> |
| [<span data-ttu-id="29eb9-128">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="29eb9-128">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="29eb9-129">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-129">3.0</span></span> |
| [<span data-ttu-id="29eb9-130">SerializableAttribute removido de alguns tipos de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29eb9-130">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="29eb9-131">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-131">3.0</span></span> |
| [<span data-ttu-id="29eb9-132">Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="29eb9-132">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="29eb9-133">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-133">3.0</span></span> |
| [<span data-ttu-id="29eb9-134">Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling</span><span class="sxs-lookup"><span data-stu-id="29eb9-134">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="29eb9-135">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-135">3.0</span></span> |
| [<span data-ttu-id="29eb9-136">Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="29eb9-136">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="29eb9-137">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-137">3.0</span></span> |
| [<span data-ttu-id="29eb9-138">Não há suporte para a opção de compatibilidade DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="29eb9-138">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="29eb9-139">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-139">3.0</span></span> |
| [<span data-ttu-id="29eb9-140">Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="29eb9-140">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="29eb9-141">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-141">3.0</span></span> |
| [<span data-ttu-id="29eb9-142">Não há suporte para a opção de compatibilidade EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="29eb9-142">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="29eb9-143">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-143">3.0</span></span> |
| [<span data-ttu-id="29eb9-144">Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="29eb9-144">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="29eb9-145">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-145">3.0</span></span> |
| [<span data-ttu-id="29eb9-146">Não há suporte para a opção de compatibilidade UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="29eb9-146">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="29eb9-147">3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-147">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="29eb9-148">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="29eb9-148">.NET 5.0</span></span>

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

## <a name="net-core-31"></a><span data-ttu-id="29eb9-149">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="29eb9-149">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="29eb9-150">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="29eb9-150">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="29eb9-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="29eb9-151">See also</span></span>

- [<span data-ttu-id="29eb9-152">Porta um aplicativo de Windows Forms para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="29eb9-152">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)

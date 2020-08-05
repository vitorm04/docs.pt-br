---
title: Windows Forms alterações significativas
description: Lista as alterações significativas no Windows Forms para .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: beb9a42e4b5007f03480cd74f57bbfbbfc3f48b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556127"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="9e1dc-103">Alterações recentes no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e1dc-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="9e1dc-104">Windows Forms suporte foi adicionado ao .NET Core na versão 3,0.</span><span class="sxs-lookup"><span data-stu-id="9e1dc-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="9e1dc-105">Este artigo lista as alterações significativas para Windows Forms pela versão do .NET Core na qual elas foram introduzidas.</span><span class="sxs-lookup"><span data-stu-id="9e1dc-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="9e1dc-106">Se você estiver atualizando um aplicativo Windows Forms de .NET Framework ou de uma versão anterior do .NET Core (3,0 ou posterior), este artigo será aplicável a você.</span><span class="sxs-lookup"><span data-stu-id="9e1dc-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="9e1dc-107">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="9e1dc-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9e1dc-108">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="9e1dc-108">Breaking change</span></span> | <span data-ttu-id="9e1dc-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9e1dc-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="9e1dc-110">Controles da barra de status removidos</span><span class="sxs-lookup"><span data-stu-id="9e1dc-110">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="9e1dc-111">5.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-111">5.0</span></span> |
| [<span data-ttu-id="9e1dc-112">Os métodos WinForms agora lançam ArgumentException</span><span class="sxs-lookup"><span data-stu-id="9e1dc-112">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="9e1dc-113">5.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-113">5.0</span></span> |
| [<span data-ttu-id="9e1dc-114">Os métodos WinForms agora lançam ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="9e1dc-114">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="9e1dc-115">5.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-115">5.0</span></span> |
| [<span data-ttu-id="9e1dc-116">As propriedades do WinForms agora geram ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="9e1dc-116">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="9e1dc-117">5.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-117">5.0</span></span> |
| [<span data-ttu-id="9e1dc-118">Controles removidos</span><span class="sxs-lookup"><span data-stu-id="9e1dc-118">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="9e1dc-119">3.1</span><span class="sxs-lookup"><span data-stu-id="9e1dc-119">3.1</span></span> |
| [<span data-ttu-id="9e1dc-120">Evento CellFormatting não gerado se ToolTip for mostrado</span><span class="sxs-lookup"><span data-stu-id="9e1dc-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="9e1dc-121">3.1</span><span class="sxs-lookup"><span data-stu-id="9e1dc-121">3.1</span></span> |
| [<span data-ttu-id="9e1dc-122">Control. DefaultFont alterado para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="9e1dc-122">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="9e1dc-123">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-123">3.0</span></span> |
| [<span data-ttu-id="9e1dc-124">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="9e1dc-124">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="9e1dc-125">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-125">3.0</span></span> |
| [<span data-ttu-id="9e1dc-126">SerializableAttribute removido de alguns tipos de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e1dc-126">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="9e1dc-127">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-127">3.0</span></span> |
| [<span data-ttu-id="9e1dc-128">Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="9e1dc-128">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="9e1dc-129">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-129">3.0</span></span> |
| [<span data-ttu-id="9e1dc-130">Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling</span><span class="sxs-lookup"><span data-stu-id="9e1dc-130">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="9e1dc-131">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-131">3.0</span></span> |
| [<span data-ttu-id="9e1dc-132">Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="9e1dc-132">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="9e1dc-133">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-133">3.0</span></span> |
| [<span data-ttu-id="9e1dc-134">Não há suporte para a opção de compatibilidade DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="9e1dc-134">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="9e1dc-135">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-135">3.0</span></span> |
| [<span data-ttu-id="9e1dc-136">Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="9e1dc-136">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="9e1dc-137">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-137">3.0</span></span> |
| [<span data-ttu-id="9e1dc-138">Não há suporte para a opção de compatibilidade EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="9e1dc-138">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="9e1dc-139">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-139">3.0</span></span> |
| [<span data-ttu-id="9e1dc-140">Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="9e1dc-140">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="9e1dc-141">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-141">3.0</span></span> |
| [<span data-ttu-id="9e1dc-142">Não há suporte para a opção de compatibilidade UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="9e1dc-142">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="9e1dc-143">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-143">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="9e1dc-144">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-144">.NET 5.0</span></span>

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="9e1dc-145">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9e1dc-145">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="9e1dc-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9e1dc-146">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9e1dc-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="9e1dc-147">See also</span></span>

- [<span data-ttu-id="9e1dc-148">Porta um aplicativo de Windows Forms para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="9e1dc-148">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)

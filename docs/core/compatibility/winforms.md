---
title: Formulários do Windows quebrando alterações
description: Lista as alterações de quebra no Windows Forms para .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 25c568a8a0092a9c4874419c64c7dcebea4dce9e
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888096"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="222f1-103">Quebrando mudanças nos formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="222f1-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="222f1-104">O suporte ao Windows Forms foi adicionado ao .NET Core na versão 3.0.</span><span class="sxs-lookup"><span data-stu-id="222f1-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="222f1-105">Este artigo lista alterações de quebra de formulários do Windows pela versão .NET Core na qual eles foram introduzidos.</span><span class="sxs-lookup"><span data-stu-id="222f1-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="222f1-106">Se você estiver atualizando um aplicativo do Windows Forms do .NET Framework ou de uma versão anterior do .NET Core (3.0 ou posterior), este artigo é aplicável a você.</span><span class="sxs-lookup"><span data-stu-id="222f1-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="222f1-107">As seguintes alterações de quebra estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="222f1-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="222f1-108">Mudança de ruptura</span><span class="sxs-lookup"><span data-stu-id="222f1-108">Breaking change</span></span> | <span data-ttu-id="222f1-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="222f1-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="222f1-110">WinForms APIs agora lançam ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="222f1-110">WinForms APIs now throw ArgumentNullException</span></span>](#winforms-apis-now-throw-argumentnullexception) | <span data-ttu-id="222f1-111">5.0</span><span class="sxs-lookup"><span data-stu-id="222f1-111">5.0</span></span> |
| [<span data-ttu-id="222f1-112">Controles removidos</span><span class="sxs-lookup"><span data-stu-id="222f1-112">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="222f1-113">3.1</span><span class="sxs-lookup"><span data-stu-id="222f1-113">3.1</span></span> |
| [<span data-ttu-id="222f1-114">Evento de formatação de células não levantada se a dica de ferramenta for mostrada</span><span class="sxs-lookup"><span data-stu-id="222f1-114">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="222f1-115">3.1</span><span class="sxs-lookup"><span data-stu-id="222f1-115">3.1</span></span> |
| [<span data-ttu-id="222f1-116">Control.DefaultFont alterado para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="222f1-116">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="222f1-117">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-117">3.0</span></span> |
| [<span data-ttu-id="222f1-118">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="222f1-118">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="222f1-119">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-119">3.0</span></span> |
| [<span data-ttu-id="222f1-120">SerializableAttribute removido de alguns tipos de formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="222f1-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="222f1-121">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-121">3.0</span></span> |
| [<span data-ttu-id="222f1-122">AllowUpdateChildControlIndexForTabControls switch de compatibilidade não suportado</span><span class="sxs-lookup"><span data-stu-id="222f1-122">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="222f1-123">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-123">3.0</span></span> |
| [<span data-ttu-id="222f1-124">DomínioUpDown.UseLegacyO switch de compatibilidade não é suportado</span><span class="sxs-lookup"><span data-stu-id="222f1-124">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="222f1-125">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-125">3.0</span></span> |
| [<span data-ttu-id="222f1-126">DoNotLoadLastRichEditO switch de compatibilidade não suportado</span><span class="sxs-lookup"><span data-stu-id="222f1-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="222f1-127">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-127">3.0</span></span> |
| [<span data-ttu-id="222f1-128">DoNotSupportSelect$ShortcutInMultilineTextBox não é suportado</span><span class="sxs-lookup"><span data-stu-id="222f1-128">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="222f1-129">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-129">3.0</span></span> |
| [<span data-ttu-id="222f1-130">Interruptor de compatibilidade DontSupportReentrantFilterMessage não suportado</span><span class="sxs-lookup"><span data-stu-id="222f1-130">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="222f1-131">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-131">3.0</span></span> |
| [<span data-ttu-id="222f1-132">Ativaro switch de compatibilidade DoVisualStyleValidation não suportado</span><span class="sxs-lookup"><span data-stu-id="222f1-132">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="222f1-133">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-133">3.0</span></span> |
| [<span data-ttu-id="222f1-134">UseLegacyContextMenuStripStripOswitch de compatibilidade Do value não suportado</span><span class="sxs-lookup"><span data-stu-id="222f1-134">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="222f1-135">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-135">3.0</span></span> |
| [<span data-ttu-id="222f1-136">O switch de compatibilidade UseLegacyImages não é suportado</span><span class="sxs-lookup"><span data-stu-id="222f1-136">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="222f1-137">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-137">3.0</span></span> |
| [<span data-ttu-id="222f1-138">Mudança de acesso para AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="222f1-138">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="222f1-139">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-139">3.0</span></span> |
| [<span data-ttu-id="222f1-140">APIs duplicadas removidas dos formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="222f1-140">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="222f1-141">3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-141">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="222f1-142">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="222f1-142">.NET 5.0</span></span>

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="222f1-143">.NET Núcleo 3.1</span><span class="sxs-lookup"><span data-stu-id="222f1-143">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="222f1-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="222f1-144">.NET Core 3.0</span></span>

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

***

## <a name="see-also"></a><span data-ttu-id="222f1-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="222f1-145">See also</span></span>

- [<span data-ttu-id="222f1-146">Porta um aplicativo Do Windows Forms para .NET Core</span><span class="sxs-lookup"><span data-stu-id="222f1-146">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)

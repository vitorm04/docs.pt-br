---
title: Formulários do Windows quebrando alterações
description: Lista as alterações de quebra no Windows Forms para .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 7fba78382d011bc9d489924fa185a44e598c5a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399094"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="8c487-103">Quebrando mudanças nos formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="8c487-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="8c487-104">O suporte ao Windows Forms foi adicionado ao .NET Core na versão 3.0.</span><span class="sxs-lookup"><span data-stu-id="8c487-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="8c487-105">Este artigo lista alterações de quebra de formulários do Windows pela versão .NET Core na qual eles foram introduzidos.</span><span class="sxs-lookup"><span data-stu-id="8c487-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="8c487-106">Se você estiver atualizando um aplicativo do Windows Forms do .NET Framework ou de uma versão anterior do .NET Core (3.0 ou posterior), este artigo é aplicável a você.</span><span class="sxs-lookup"><span data-stu-id="8c487-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="8c487-107">As seguintes alterações de quebra estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="8c487-107">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="8c487-108">Controles removidos</span><span class="sxs-lookup"><span data-stu-id="8c487-108">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="8c487-109">Evento de formatação de células não levantada se a dica de ferramenta for mostrada</span><span class="sxs-lookup"><span data-stu-id="8c487-109">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="8c487-110">Control.DefaultFont alterado para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="8c487-110">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="8c487-111">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="8c487-111">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="8c487-112">SerializableAttribute removido de alguns tipos de formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="8c487-112">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="8c487-113">AllowUpdateChildControlIndexForTabControls switch de compatibilidade não suportado</span><span class="sxs-lookup"><span data-stu-id="8c487-113">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="8c487-114">DomínioUpDown.UseLegacyO switch de compatibilidade não é suportado</span><span class="sxs-lookup"><span data-stu-id="8c487-114">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="8c487-115">DoNotLoadLastRichEditO switch de compatibilidade não suportado</span><span class="sxs-lookup"><span data-stu-id="8c487-115">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="8c487-116">DoNotSupportSelect$ShortcutInMultilineTextBox não é suportado</span><span class="sxs-lookup"><span data-stu-id="8c487-116">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="8c487-117">Interruptor de compatibilidade DontSupportReentrantFilterMessage não suportado</span><span class="sxs-lookup"><span data-stu-id="8c487-117">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="8c487-118">Ativaro switch de compatibilidade DoVisualStyleValidation não suportado</span><span class="sxs-lookup"><span data-stu-id="8c487-118">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="8c487-119">UseLegacyContextMenuStripStripOswitch de compatibilidade Do value não suportado</span><span class="sxs-lookup"><span data-stu-id="8c487-119">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="8c487-120">O switch de compatibilidade UseLegacyImages não é suportado</span><span class="sxs-lookup"><span data-stu-id="8c487-120">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="8c487-121">Mudança de acesso para AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="8c487-121">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="8c487-122">APIs duplicadas removidas dos formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="8c487-122">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a><span data-ttu-id="8c487-123">.NET Núcleo 3.1</span><span class="sxs-lookup"><span data-stu-id="8c487-123">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="8c487-124">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8c487-124">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8c487-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c487-125">See also</span></span>

- [<span data-ttu-id="8c487-126">Porta um aplicativo Do Windows Forms para .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c487-126">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)

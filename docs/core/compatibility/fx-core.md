---
title: Alterações - .NET Framework para .NET Core
titleSuffix: ''
description: Lista as alterações de quebra de .NET Framework para .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: ef16132c8dcffbe9bcfbe02834c9a78d6d0c33e4
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021800"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="1775c-103">Alterações de separação de migração do .NET Framework para .NET Core</span><span class="sxs-lookup"><span data-stu-id="1775c-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="1775c-104">Se você estiver migrando um aplicativo do .NET Framework para o .NET Core, as alterações de quebra listadas neste artigo podem afetá-lo.</span><span class="sxs-lookup"><span data-stu-id="1775c-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="1775c-105">As mudanças de quebra são agrupadas por categoria, e dentro dessas categorias, pela versão do .NET Core em que foram introduzidas.</span><span class="sxs-lookup"><span data-stu-id="1775c-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="1775c-106">Este artigo não é uma lista completa de alterações de ruptura entre .NET Framework e .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1775c-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="1775c-107">As mudanças de quebra mais importantes são adicionadas aqui à medida que nos tornamos conscientes delas.</span><span class="sxs-lookup"><span data-stu-id="1775c-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="1775c-108">Bibliotecas Core .NET</span><span class="sxs-lookup"><span data-stu-id="1775c-108">Core .NET libraries</span></span>

- [<span data-ttu-id="1775c-109">Alterar o valor padrão do UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="1775c-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="1775c-110">Não autorizadoAccessException lançado por FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="1775c-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a><span data-ttu-id="1775c-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1775c-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="1775c-112">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="1775c-112">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a><span data-ttu-id="1775c-113">Criptografia</span><span class="sxs-lookup"><span data-stu-id="1775c-113">Cryptography</span></span>

- [<span data-ttu-id="1775c-114">Parâmetro booleano de SignedCms.ComputeSignature é respeitado</span><span class="sxs-lookup"><span data-stu-id="1775c-114">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="1775c-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1775c-115">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="1775c-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1775c-116">Windows Forms</span></span>

<span data-ttu-id="1775c-117">O suporte ao Windows Forms foi adicionado ao .NET Core na versão 3.0.</span><span class="sxs-lookup"><span data-stu-id="1775c-117">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="1775c-118">Se você estiver migrando um aplicativo do Windows Forms do .NET Framework para o .NET Core, as alterações de quebra listadas aqui podem afetar o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1775c-118">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="1775c-119">Controles removidos</span><span class="sxs-lookup"><span data-stu-id="1775c-119">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="1775c-120">Evento de formatação de células não levantada se a dica de ferramenta for mostrada</span><span class="sxs-lookup"><span data-stu-id="1775c-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="1775c-121">Control.DefaultFont alterado para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="1775c-121">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="1775c-122">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="1775c-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="1775c-123">SerializableAttribute removido de alguns tipos de formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="1775c-123">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="1775c-124">AllowUpdateChildControlIndexForTabControls switch de compatibilidade não suportado</span><span class="sxs-lookup"><span data-stu-id="1775c-124">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="1775c-125">DomínioUpDown.UseLegacyO switch de compatibilidade não é suportado</span><span class="sxs-lookup"><span data-stu-id="1775c-125">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="1775c-126">DoNotLoadLastRichEditO switch de compatibilidade não suportado</span><span class="sxs-lookup"><span data-stu-id="1775c-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="1775c-127">DoNotSupportSelect$ShortcutInMultilineTextBox não é suportado</span><span class="sxs-lookup"><span data-stu-id="1775c-127">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="1775c-128">Interruptor de compatibilidade DontSupportReentrantFilterMessage não suportado</span><span class="sxs-lookup"><span data-stu-id="1775c-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="1775c-129">Ativaro switch de compatibilidade DoVisualStyleValidation não suportado</span><span class="sxs-lookup"><span data-stu-id="1775c-129">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="1775c-130">UseLegacyContextMenuStripStripOswitch de compatibilidade Do value não suportado</span><span class="sxs-lookup"><span data-stu-id="1775c-130">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="1775c-131">O switch de compatibilidade UseLegacyImages não é suportado</span><span class="sxs-lookup"><span data-stu-id="1775c-131">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="1775c-132">Mudança de acesso para AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="1775c-132">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="1775c-133">APIs duplicadas removidas dos formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="1775c-133">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="1775c-134">.NET Núcleo 3.1</span><span class="sxs-lookup"><span data-stu-id="1775c-134">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="1775c-135">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1775c-135">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9 pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a><span data-ttu-id="1775c-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="1775c-136">See also</span></span>

- [<span data-ttu-id="1775c-137">APIs que sempre lançam exceções no .NET Core</span><span class="sxs-lookup"><span data-stu-id="1775c-137">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="1775c-138">Tecnologias do .NET Framework não disponíveis no .NET Core</span><span class="sxs-lookup"><span data-stu-id="1775c-138">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)

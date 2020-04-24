---
title: Alterações recentes – .NET Framework para o .NET Core
titleSuffix: ''
description: Lista as alterações significativas de .NET Framework para o .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 6a6cbffed5a54e3683832da54d408d77bb553cf1
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135615"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="5059d-103">Alterações recentes de migração do .NET Framework para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="5059d-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="5059d-104">Se você estiver migrando um aplicativo do .NET Framework para o .NET Core, as alterações significativas listadas neste artigo poderão afetar você.</span><span class="sxs-lookup"><span data-stu-id="5059d-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="5059d-105">As alterações significativas são agrupadas por categoria e dentro dessas categorias, pela versão do .NET Core na qual elas foram introduzidas.</span><span class="sxs-lookup"><span data-stu-id="5059d-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="5059d-106">Este artigo não é uma lista completa de alterações significativas entre o .NET Framework e o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5059d-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="5059d-107">As alterações significativas mais importantes são adicionadas aqui, pois estamos cientes delas.</span><span class="sxs-lookup"><span data-stu-id="5059d-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="5059d-108">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="5059d-108">Core .NET libraries</span></span>

- [<span data-ttu-id="5059d-109">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="5059d-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="5059d-110">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="5059d-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [<span data-ttu-id="5059d-111">Tratamento de exceções de estado de processo corrompido não é suportado</span><span class="sxs-lookup"><span data-stu-id="5059d-111">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported)

### <a name="net-core-21"></a><span data-ttu-id="5059d-112">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5059d-112">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="5059d-113">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5059d-113">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

## <a name="cryptography"></a><span data-ttu-id="5059d-114">Criptografia</span><span class="sxs-lookup"><span data-stu-id="5059d-114">Cryptography</span></span>

- [<span data-ttu-id="5059d-115">O parâmetro booliano de SignedCms. ComputeSignature é respeitado</span><span class="sxs-lookup"><span data-stu-id="5059d-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="5059d-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5059d-116">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="5059d-117">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5059d-117">Windows Forms</span></span>

<span data-ttu-id="5059d-118">Windows Forms suporte foi adicionado ao .NET Core na versão 3,0.</span><span class="sxs-lookup"><span data-stu-id="5059d-118">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="5059d-119">Se você estiver migrando um aplicativo Windows Forms do .NET Framework para o .NET Core, as alterações significativas listadas aqui podem afetar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5059d-119">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="5059d-120">Controles removidos</span><span class="sxs-lookup"><span data-stu-id="5059d-120">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="5059d-121">Evento CellFormatting não gerado se ToolTip for mostrado</span><span class="sxs-lookup"><span data-stu-id="5059d-121">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="5059d-122">Control. DefaultFont alterado para Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="5059d-122">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="5059d-123">Modernização do FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="5059d-123">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="5059d-124">SerializableAttribute removido de alguns tipos de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5059d-124">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="5059d-125">Não há suporte para a opção de compatibilidade AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="5059d-125">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="5059d-126">Não há suporte para a opção de compatibilidade DomainUpDown. UseLegacyScrolling</span><span class="sxs-lookup"><span data-stu-id="5059d-126">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="5059d-127">Não há suporte para a opção de compatibilidade DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="5059d-127">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="5059d-128">Não há suporte para a opção de compatibilidade DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="5059d-128">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="5059d-129">Não há suporte para a opção de compatibilidade DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="5059d-129">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="5059d-130">Não há suporte para a opção de compatibilidade EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="5059d-130">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="5059d-131">Não há suporte para a opção de compatibilidade UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="5059d-131">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="5059d-132">Não há suporte para a opção de compatibilidade UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="5059d-132">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="5059d-133">Alteração de acesso para AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="5059d-133">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="5059d-134">APIs duplicadas removidas do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5059d-134">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="5059d-135">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="5059d-135">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="5059d-136">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5059d-136">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5059d-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="5059d-137">See also</span></span>

- [<span data-ttu-id="5059d-138">APIs que sempre lançam exceções no .NET Core</span><span class="sxs-lookup"><span data-stu-id="5059d-138">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="5059d-139">Tecnologias do .NET Framework não disponíveis no .NET Core</span><span class="sxs-lookup"><span data-stu-id="5059d-139">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)

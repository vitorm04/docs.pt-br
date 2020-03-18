---
title: Alterações - .NET Framework para .NET Core
titleSuffix: ''
description: Lista as alterações de quebra de .NET Framework para .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: f712be14d7debc4b3008f8459e6ee925754b25f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449382"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Alterações de separação de migração do .NET Framework para .NET Core

Se você estiver migrando um aplicativo do .NET Framework para o .NET Core, as alterações de quebra listadas neste artigo podem afetá-lo. As mudanças de quebra são agrupadas por categoria, e dentro dessas categorias, pela versão do .NET Core em que foram introduzidas.

> [!NOTE]
> Este artigo não é uma lista completa de alterações de ruptura entre .NET Framework e .NET Core. As mudanças de quebra mais importantes são adicionadas aqui à medida que nos tornamos conscientes delas.

## <a name="corefx"></a>CoreFx

- [Alterar o valor padrão do UseShellExecute](#change-in-default-value-of-useshellexecute)
- [Não autorizadoAccessException lançado por FileSystemInfo.Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a>Criptografia

- [Parâmetro booleano de SignedCms.ComputeSignature é respeitado](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a>Windows Forms

O suporte ao Windows Forms foi adicionado ao .NET Core na versão 3.0. Se você estiver migrando um aplicativo do Windows Forms do .NET Framework para o .NET Core, as alterações de quebra listadas aqui podem afetar o seu aplicativo.

- [Controles removidos](#removed-controls)
- [Evento de formatação de células não levantada se a dica de ferramenta for mostrada](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control.DefaultFont alterado para Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernização do FolderBrowserDialog](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute removido de alguns tipos de formulários do Windows](#serializableattribute-removed-from-some-windows-forms-types)
- [AllowUpdateChildControlIndexForTabControls switch de compatibilidade não suportado](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [DomínioUpDown.UseLegacyO switch de compatibilidade não é suportado](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [DoNotLoadLastRichEditO switch de compatibilidade não suportado](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [DoNotSupportSelect$ShortcutInMultilineTextBox não é suportado](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Interruptor de compatibilidade DontSupportReentrantFilterMessage não suportado](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [Ativaro switch de compatibilidade DoVisualStyleValidation não suportado](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [UseLegacyContextMenuStripStripOswitch de compatibilidade Do value não suportado](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [O switch de compatibilidade UseLegacyImages não é suportado](#uselegacyimages-compatibility-switch-not-supported)
- [Mudança de acesso para AccessibleObject.RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [APIs duplicadas removidas dos formulários do Windows](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a>.NET Núcleo 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="see-also"></a>Confira também

- [APIs que sempre lançam exceções no .NET Core](unsupported-apis.md)
- [Tecnologias do .NET Framework não disponíveis no .NET Core](../porting/net-framework-tech-unavailable.md)

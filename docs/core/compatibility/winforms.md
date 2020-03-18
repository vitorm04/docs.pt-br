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
# <a name="breaking-changes-in-windows-forms"></a>Quebrando mudanças nos formulários do Windows

O suporte ao Windows Forms foi adicionado ao .NET Core na versão 3.0. Este artigo lista alterações de quebra de formulários do Windows pela versão .NET Core na qual eles foram introduzidos. Se você estiver atualizando um aplicativo do Windows Forms do .NET Framework ou de uma versão anterior do .NET Core (3.0 ou posterior), este artigo é aplicável a você.

As seguintes alterações de quebra estão documentadas nesta página:

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

## <a name="net-core-31"></a>.NET Núcleo 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="see-also"></a>Confira também

- [Porta um aplicativo Do Windows Forms para .NET Core](../porting/winforms.md)

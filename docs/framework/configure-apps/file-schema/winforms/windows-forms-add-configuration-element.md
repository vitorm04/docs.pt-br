---
title: "Windows Forms adicionar elemento de configuração"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 367ca30c577cbb4ed7fed130bdcbd4faac2d46c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms adicionar elemento de configuração

O `<add>` elemento adiciona uma chave predefinida que especifica se o seu aplicativo de formulário do Windows oferece suporte a recursos adicionados aos aplicativos de formulários do Windows em que o .NET Framework 4.7 ou posterior.

## <a name="syntax"></a>Sintaxe

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

| Atributo | Descrição |
| --------- | ----------- |
| `key`     | Atributo obrigatório. Um nome de chave predefinido que corresponde a um determinado recurso personalizável de formulários do Windows. |
| `value`   | Atributo obrigatório. O valor a ser atribuído a `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key`nomes de atributos e valores associados

| nome de `key` | Valores | Descrição |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "verdadeiro" &#124;" False" | Indica se os controles ancorados são dimensionados em uma única passagem. passa "true" para desabilitar única escala; Caso contrário, false. Consulte a seção "Único passar dimensionamento" o [comentários](#Remarks) para obter mais informações. |
| "DpiAwareness" | "PerMonitorV2" &#124;" False" | Indica se um aplicativo com reconhecimento de DPI. Defina a chave como "PerMonitorV2" para dar suporte ao reconhecimento de Dpi; Caso contrário, defina-o como "false". Reconhecimento DPI é um recurso de aceitação; para aproveitar o suporte DPI alto de formulários do Windows, você deve definir seu valor como "PerMonitorV2". Consulte o [comentários](#remarks) para obter mais informações. |
| "CheckedListBox.DisableHighDpiImprovements" | "verdadeiro" &#124;" False" | Indica se o <xref:System.Windows.Forms.CheckedListBox> controle tira proveito dos aprimoramentos de dimensionamento e o layout introduzidos no .NET Framework 4.7. "true" para recusar aprimoramentos de layout e caling; Caso contrário, "falso". |
| "DataGridView.DisableHighDpiImprovements" | "verdadeiro" &#124;" False" | Indica se o <xref:System.Windows.Forms.DataGridView> controlar aprimoramentos de dimensionamento e o layout introduzidos no .NET Framework 4.7. "true" para recusar o reconhecimento DPI; "false" caso contrário. |
| "DisableDpiChangedMessageHandling" | "verdadeiro" &#124;" False" | "true" para recusar o recebimento de mensagens relacionadas a alterações; de dimensionamento de DPI "false" caso contrário. Consulte o [comentários](#remarks) para obter mais informações. |
| "EnableWindowsFormsHighDpiAutoResizing" | "verdadeiro" &#124;" False" | Indica se um aplicativo do Windows Forms é redimensionado automaticamente devido a alterações de dimensionamento de DPI. "true" para habilitar o redimensionamento automático; Caso contrário, false. |
| "Form.DisableSinglePassControlScaling" | "verdadeiro" &#124;" False" | Indica se o <xref:System.Windows.Forms.Form> é dimensionado em uma única passagem. "true" para desabilitar a passagem única escala; Caso contrário, false. Consulte a seção "Único passar dimensionamento" o [comentários](#Remarks) para obter mais informações. |
| "MonthCalendar.DisableSinglePassControlScaling" | "verdadeiro" &#124;" False" | Indica se o <xref:System.Windows.Forms.MonthCalendar> controle é dimensionado em uma única passagem. "true" para desabilitar a passagem única escala; Caso contrário, false. Consulte a seção "Único passar dimensionamento" o [comentários](#Remarks) para obter mais informações. |
| "Toolstrip.DisableHighDpiImprovements" | "verdadeiro" &#124;" False" | Indica se o <xref:System.Windows.Forms.ToolStrip> controle tira proveito dos aprimoramentos de dimensionamento e o layout introduzidos no .NET Framework 4.7. "true" para recusar o reconhecimento DPI; "false" caso contrário. |

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Configura o suporte a novos recursos de aplicativos de formulários do Windows. |

## <a name="a-nameremarks--remarks"></a><a name="remarks" />Comentários

A partir do .NET Framework 4.7, o elemento `<System.Windows.Forms.ApplicationConfigurationSection>` permite configurar os aplicativos do Windows Forms para aproveitar os recursos adicionados em versões recentes do .NET Framework. 

O `<System.Windows.Forms.ApplicationConfigurationSection>` elemento permite que você adicione um ou mais filhos `<add>` elementos, cada um deles define uma configuração específica.  

Para obter uma visão geral do suporte a alto DPI do Windows Forms, consulte [alto DPI suporte no Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Aplicativos de formulários do Windows que são executados em versões de Windows, começando com os criadores de edição do Windows 10 e versões de destino do .NET Framework, começando com o .NET Framework 4.7 podem ser configurados para tirar proveito dos aprimoramentos de DPI alto introduzido no .NET Framework 4.7. Elas incluem:

- Suporte para cenários DPI dinâmicos no qual o usuário altera o fator de escala ou DPI depois que um aplicativo Windows Forms foi iniciado.

- Melhorias no layout de um número de formulários do Windows e dimensionando controles, como o <xref:System.Windows.Forms.MonthCalendar> controle e o <xref:System.Windows.Forms.CheckedListBox> controle. 

Reconhecimento DPI alto é um recurso de aceitação; Por padrão, o valor de `DpiAwareness` é `false`. Você pode escolher para suporte de formulários do Windows para que o reconhecimento DPI definindo o valor dessa chave para `PerMonitorV2` no arquivo de configuração do aplicativo. Se o reconhecimento DPI estiver habilitado, todos os recursos DPI individuais também estão habilitados. Elas incluem:

- DPI alterado mensagens, que são controladas pelo `DisableDpiChangedMessageHandling` chave.

- Suporte DPI dinâmico, que é controlado pelo `EnableWindowsFormsHighDpiAutoResizing` chave.

- Passada única e dimensionamento de controle, que é controlada pelo `Form.DisableSinglePassControlScaling` indivíduo <xref:System.Windows.Forms.Form> controla, pelo `AnchorLayout.DisableSinglePassControlScaling` chave controles ancorados e pela `MonthCalendar.DisableSinglePassControlScaling` chave para o <xref:System.Windows.Forms.MonthCalendar> controle 

- Alto DPI dimensionamento e layout aprimoramentos, que é controlado pelo `CheckListBox.DisableHighDpiImprovements` chave para o <xref:System.Windows.Forms.CheckedListBox> controlar, pelo `DataGridView.DisableHighDpiImprovements` chave para o <xref:System.Windows.Forms.DataGridView> controle e pela `Toolstrip.DisableHighDpiImprovements` chave para o <xref:System.Windows.Forms.ToolStrip> controle.  

A única aceitar configuração padrão fornecida definindo `DpiAwareness` para `PerMonitorV2` é geralmente adequado para novos aplicativos de formulários do Windows. No entanto, você pode, em seguida, recusar melhorias de DPI alto individuais, adicionando a chave correspondente no arquivo de configuração do aplicativo. Por exemplo, para tirar proveito de todos os as featuers DPI novo exceto para suporte DPI dinâmico, adicione o seguinte arquivo de configuração de aplicativo:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <--! Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
Normalmente, você optar por um determinado recurso porque você optou por tratá-la por meio de programação.

Para obter mais informações sobre aproveitando as vantagens do suporte a alto DPI em aplicativos de formulários do Windows, consulte [alto DPI suporte no Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

Começando com o .NET Framework 4.7, controles de formulários do Windows geram um número de eventos relacionados às alterações de dimensionamento de DPI. Isso inclui o <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, e <xref:System.Windows.Forms.Form.DpiChanged> eventos. O valor de `DisableDpiChangedMessageHandling` chave determina se esses eventos são gerados em um aplicativo do Windows Forms. 

### <a name="single-pass-scaling"></a>Dimensionamento de passagem de único

Dimensionamento único ou vários passos influencia a capacidade de resposta percebida da interface do usuário e os elementos da interface a aparência visual do usuário conforme são dimensionadas. Começando com o .NET Framework 4.7, formulários do Windows usa a escala de passagem. Nas versões anteriores do .NET Framework, o dimensionamento foi realizada por meio de várias passagens, o que causou alguns controles será dimensionada mais do que era necessária. Dimensionamento de fase única só deve ser desabilitado se seu aplicativo depende do comportamento antigo.  

## <a name="see-also"></a>Consulte também
 
[Seção de configuração do Windows Forms](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md) (Suporte a alto DPI no Windows Forms)

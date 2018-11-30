---
title: Windows Forms adicionar elemento de configuração
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cb0d058cd1ade65bfdc966819c0c41d9c1a9750
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52672115"
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms adicionar elemento de configuração

O `<add>` elemento adiciona uma chave predefinida que especifica se o seu aplicativo de formulário do Windows dá suporte a recursos adicionados aos aplicativos do Windows Forms no .NET Framework 4.7 ou posterior.

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

### <a name="key-attribute-names-and-associated-values"></a>`key` nomes de atributo e valores associados

| nome de `key` | Valores | Descrição |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | Indica se os controles ancorados serão reduzidas horizontalmente em uma única passagem. "true" para desabilitar um único passe dimensionamento; Caso contrário, false. Consulte a seção "Único pass dimensionamento" a [comentários](#Remarks) para obter mais informações. |
| "DpiAwareness" | "PerMonitorV2"&#124;"false" | Indica se um aplicativo com reconhecimento de DPI. Defina a chave como "PerMonitorV2" para dar suporte ao reconhecimento de Dpi; Caso contrário, defina-o como "false". Reconhecimento de DPI é um recurso de aceitação; para tirar proveito do suporte ao DPI alto dos Windows Forms, você deve definir seu valor para "PerMonitorV2". Consulte a [comentários](#remarks) seção para obter mais informações. |
| "CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | Indica se o <xref:System.Windows.Forms.CheckedListBox> controle se beneficia dos aprimoramentos de dimensionamento e layout introduzido no .NET Framework 4.7. "true" para recusar a aprimoramentos de layout e caling; Caso contrário, "false". |
| "DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | Indica se o <xref:System.Windows.Forms.DataGridView> controlar aprimoramentos de dimensionamento e layout introduzidos no .NET Framework 4.7. "true" para recusar o reconhecimento de DPI; "false" caso contrário. |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | "true" para recusar o recebimento de mensagens relacionadas a alterações; de dimensionamento de DPI "false" caso contrário. Consulte a [comentários](#remarks) seção para obter mais informações. |
| "EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | Indica se um aplicativo do Windows Forms é redimensionado automaticamente devido a alterações de colocação em escala de DPI. "true" para habilitar o redimensionamento automático; Caso contrário, false. |
| "Form.DisableSinglePassControlScaling" | "true"&#124;"false" | Indica se o <xref:System.Windows.Forms.Form> é dimensionado em uma única passagem. "true" para desabilitar a passagem única escala; Caso contrário, false. Consulte a seção "Único pass dimensionamento" a [comentários](#Remarks) para obter mais informações. |
| "MonthCalendar.DisableSinglePassControlScaling" | "true"&#124;"false" | Indica se o <xref:System.Windows.Forms.MonthCalendar> controle é dimensionado em uma única passagem. "true" para desabilitar a passagem única escala; Caso contrário, false. Consulte a seção "Único pass dimensionamento" a [comentários](#Remarks) para obter mais informações. |
| "Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | Indica se o <xref:System.Windows.Forms.ToolStrip> controle se beneficia dos aprimoramentos de dimensionamento e layout introduzido no .NET Framework 4.7. "true" para recusar o reconhecimento de DPI; "false" caso contrário. |

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Configura o suporte para novos recursos de aplicativo do Windows Forms. |

## <a name="a-nameremarks--remarks"></a><a name="remarks" /> Comentários

A partir do .NET Framework 4.7, o elemento `<System.Windows.Forms.ApplicationConfigurationSection>` permite configurar os aplicativos do Windows Forms para aproveitar os recursos adicionados em versões recentes do .NET Framework. 

O `<System.Windows.Forms.ApplicationConfigurationSection>` elemento permite que você adicione um ou mais filhos `<add>` elementos, cada um deles define uma configuração específica.  

Para uma visão geral do suporte a DPI alta do Windows Forms, consulte [suporte a DPI alto nos Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Aplicativos de formulários do Windows que são executados em versões de Windows, começando com a edição do Windows 10 para criadores e versões de destino do .NET Framework começando com o .NET Framework 4.7 podem ser configurados para tirar proveito dos aprimoramentos de DPI alta introduzido no .NET Framework 4.7. Elas incluem:

- Suporte para cenários DPI dinâmicos em que o usuário altera o fator de escala de DPI após um aplicativo do Windows Forms foi iniciado.

- Controles de melhorias no dimensionamento e layout de um número de formulários do Windows, como o <xref:System.Windows.Forms.MonthCalendar> controle e o <xref:System.Windows.Forms.CheckedListBox> controle. 

Reconhecimento de DPI alta é um recurso de aceitação; Por padrão, o valor de `DpiAwareness` é `false`. Você pode aceitar o suporte dos Windows Forms para reconhecimento de DPI, definindo o valor desta chave como `PerMonitorV2` no arquivo de configuração do aplicativo. Se o reconhecimento de DPI é habilitado, todos os recursos individuais do DPI também são habilitados. Elas incluem:

- DPI alterado mensagens, que são controladas pelo `DisableDpiChangedMessageHandling` chave.

- Suporte ao DPI dinâmico, que é controlada pela `EnableWindowsFormsHighDpiAutoResizing` chave.

- Passada única e dimensionamento do controle, que é controlada pela `Form.DisableSinglePassControlScaling` de indivíduo <xref:System.Windows.Forms.Form> controla, pela `AnchorLayout.DisableSinglePassControlScaling` chave controles ancorados e pela `MonthCalendar.DisableSinglePassControlScaling` chave para o <xref:System.Windows.Forms.MonthCalendar> controle 

- Alto DPI dimensionamento e layout aprimoramentos, que é controlado pelo `CheckListBox.DisableHighDpiImprovements` chave para o <xref:System.Windows.Forms.CheckedListBox> controlar, pela `DataGridView.DisableHighDpiImprovements` chave para o <xref:System.Windows.Forms.DataGridView> controle e pela `Toolstrip.DisableHighDpiImprovements` chave para o <xref:System.Windows.Forms.ToolStrip> controle.  

A única opt-in configuração padrão fornecida definindo `DpiAwareness` para `PerMonitorV2` é geralmente adequado para novos aplicativos de formulários do Windows. No entanto, você pode, em seguida, optar por não individuais melhorias de DPI alta, adicionando a chave correspondente no arquivo de configuração do aplicativo. Por exemplo, para tirar proveito de todos os os featuers novo DPI, exceto para suporte ao DPI dinâmico, adicione o seguinte ao arquivo de configuração de aplicativo:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
Normalmente, recusar um determinado recurso porque você optou por tratá-la por meio de programação.

Para obter mais informações sobre aproveitando as vantagens do suporte a DPI alto em aplicativos do Windows Forms, consulte [suporte a DPI alto nos Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

Controles dos Windows Forms a partir do .NET Framework 4.7, geram um número de eventos relacionados às alterações de dimensionamento de DPI. Isso inclui o <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, e <xref:System.Windows.Forms.Form.DpiChanged> eventos. O valor da `DisableDpiChangedMessageHandling` chave determina se esses eventos são gerados em um aplicativo Windows Forms. 

### <a name="single-pass-scaling"></a>Dimensionamento de passagem única

Dimensionando único ou vários passos influencia a capacidade de resposta percebida da interface do usuário e a aparência visual de elementos da interface do usuário conforme eles são dimensionados. Começando com o .NET Framework 4.7, Windows Forms usa o dimensionamento de única passagem. Nas versões anteriores do .NET Framework, o dimensionamento foi executado por meio de várias passagens, o que causou alguns controles sejam escalonados de mais do que era necessário. Dimensionamento de passagem única só deve ser desabilitado se seu aplicativo depende do comportamento antigo.  

## <a name="see-also"></a>Consulte também
 
[Seção de configuração do Windows Forms](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md) (Suporte a alto DPI no Windows Forms)

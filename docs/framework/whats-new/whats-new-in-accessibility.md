---
title: "O que há de novo no acessibilidade no .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4886dad94d3a67e78525241a1538c06b9fe4b0be
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2017
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>O que há de novo no acessibilidade no .NET Framework

O .NET Framework pretende fazer mais acessíveis para os usuários de aplicativos. Recursos de acessibilidade permitem que um aplicativo fornecer uma experiência apropriada para os usuários de tecnologia assistencial. Iniciando com o .NET Framework 4.7.1, o .NET Framework inclui um grande número de aprimoramentos de acessibilidade que permitem aos desenvolvedores criar aplicativos acessíveis. 

Os novos recursos de acessibilidade são habilitados por padrão para aplicativos voltados para o .NET Framework 4.7.1 ou posterior. Além disso, aplicativos que uma versão anterior do .NET Framework de destino, mas estão em execução no .NET Framework 4.7.1 ou posterior podem optar por comportamentos de acessibilidade herdado (e, portanto, escolha os aprimoramentos de acessibilidade no .NET Framework 4.7.1) por adicionando a seguinte opção para o [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento o [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) seção do arquivo de configuração do aplicativo. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Da mesma forma, aplicativos destinados a versões do .NET Framework a partir 4.7.1 podem desabilitar os recursos de acessibilidade, adicionando a seguinte opção para o [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento o [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) seção do arquivo de configuração do aplicativo. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>O que há de novo no acessibilidade no .NET Framework 4.7.1

O .NET Framework 4.7.1 inclui novos recursos de acessibilidade nas seguintes áreas:

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows Forms](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Aprimoramentos de leitor de tela**

Se os aprimoramentos de acessibilidade estão habilitados, o .NET Framework 4.7.1 inclui os seguintes aprimoramentos que afetam os leitores de tela:

- No .NET Framework 4.7 e versões anteriores, <xref:System.Windows.Controls.Expander> controles foram lançados por leitores de tela como botões. Iniciando com o .NET Framework 4.7.1, eles são corretamente anunciados como grupos expansível recolhível.

- No .NET Framework 4.7 e versões anteriores, <xref:System.Windows.Controls.DataGridCell> controles foram lançados por leitores de tela como "custom". Iniciando com o .NET Framework 4.7.1, eles agora estão corretamente anunciados como célula de grade de dados (localizada).
 
- Iniciando com o .NET Framework 4.7.1, leitores de tela anunciam o nome de um editável <xref:System.Windows.Controls.ComboBox>.

- No .NET Framework 4.7 e versões anteriores, <xref:System.Windows.Controls.PasswordBox> controles foram anunciados como "nenhum item no modo de exibição" ou tinha um comportamento incorreto caso contrário. Esse problema é corrigido, iniciando com o .NET Framework 4.7.1.     

**Suporte de UIAutomation LiveRegion**

Leitores de tela, como as pessoas de ajuda o Narrator ler o conteúdo de interface do usuário de um aplicativo, normalmente pela saída de texto em fala do conteúdo da interface do usuário que tem o foco. No entanto, se um elemento de interface do usuário for alterado e não tem o foco, o usuário não pode ser notificado e poderá perder informações importantes. Regiões ao vivo focalizam a solução do problema. Um desenvolvedor pode usá-los para informar o leitor de tela ou qualquer outro cliente de automação da IU que foi feita uma alteração importante de um elemento de interface do usuário. O leitor de tela, em seguida, pode decidir como e quando para informar ao usuário dessa alteração. 

Para dar suporte ao vivo regiões, as seguintes APIs foram adicionadas para WPF:

- O <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> campos que identificam o **LiveSetting** propriedade e o **LiveRegionChanged** eventos. Eles podem ser definidos usando XAML.

- O **AutomationProperties.LiveSetting** anexado a propriedade, que informa o leitor de tela da importância da alteração da interface do usuário para o usuário.

- O <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> propriedade que identifica o **AutomationProperties.LiveSetting** propriedade anexada.
 
- O <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> método, que pode ser substituído para fornecer uma **LiveSetting** valor.

- O <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> métodos, que obtém e definir um **LiveSetting** valor.
 
- O <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeração, que define os seguintes possíveis **LiveSetting** valores:

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. O elemento não enviar notificações se o conteúdo da região de dados ao vivo foi alterado.   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. O elemento enviará notificações não interruptivas se o conteúdo da região dinâmica tiver sido alterado.   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. O elemento enviará notificações interruptivas se o conteúdo da região dinâmica tiver sido alterado.   

Você pode criar um LiveRegion definindo o **AutomationProperties.LiveSetting** propriedade no elemento de interesse, como mostrado no exemplo a seguir:   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Quando os dados na região dinâmica são alterados e você precisa informar um leitor de tela, você explicitamente gerar um evento, conforme mostrado no exemplo a seguir.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Alto contraste**

Iniciando com o .NET Framework 4.7.1, em alto contraste foram feitas melhorias para vários controles do WPF. Agora são visíveis quando a <xref:System.Windows.SystemParameters.HighContrast%2A> tema está definido. Elas incluem:

- Controle <xref:System.Windows.Controls.Expander>

    O foco visual para o <xref:System.Windows.Controls.Expander> controle agora está visível. Os visuais de teclado para <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, e <xref:System.Windows.Controls.RadioButton> controles também são visíveis. Por exemplo:

    Antes: 
    
    ![Controle expansor com foco antes de aprimoramentos de acessibilidade](media/expander-before.png)

    Depois: 

    ![Controle expansor com foco após aprimoramentos de acessibilidade](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox>e <xref:System.Windows.Controls.RadioButton> controles
 
    O texto a <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton> controles agora é mais fácil ver quando selecionados em temas de alto contraste. Por exemplo:

    Antes: 

    ![Botão de opção de alto contraste com foco antes de aprimoramentos de acessibilidade](media/radio-button-before.png)
    
    Depois: 

    ![Botão de opção de alto contraste com foco após aprimoramentos de acessibilidade](media/radio-button-after.png)

- Controle <xref:System.Windows.Controls.ComboBox>
 
    Iniciando com o .NET Framework 4.7.1, a borda de um desativado <xref:System.Windows.Controls.ComboBox> controle é a mesma cor do texto desabilitado. Por exemplo:
    
    Antes: 

     ![Caixa de combinação desabilitado borda e o texto antes de aprimoramentos de acessibilidade](media/combo-disabled-before.png)

    Depois:   

     ![Caixa de combinação desabilitado borda e o texto depois de aprimoramentos de acessibilidade](media/combo-disabled-after.png)

    Além disso, botões desabilitados e voltada para usam a cor de tema correto.

    Antes:

    ![Cores de tema do botão antes de aprimoramentos de acessibilidade](media/button-themes-before.png) 
    
    Depois: 

    ![Cores de tema do botão após aprimoramentos de acessibilidade](media/button-themes-after.png) 

    Por fim, no .NET Framework 4.7 e versões anteriores, definindo um <xref:System.Windows.Controls.ComboBox> estilo de controle para `Toolbar.ComboBoxStyleKey` causou a seta suspensa invisível. Esse problema é corrigido, iniciando com o .NET Framework 4.7.1. Por exemplo:

    Antes: 

    ![Toolbar.ComboBoxStyleKey antes de aprimoramentos de acessibilidade](media/comboboxstylekey-before.png) 
    
    Depois: 

    ![Toolbar.ComboBoxStyleKey depois de aprimoramentos de acessibilidade](media/comboboxstylekey-after.png) 

- Controle <xref:System.Windows.Controls.DataGrid>

    Iniciando com o .NET Framework 4.7.1, na seta de indicador de classificação no <xref:System.Windows.Controls.DataGrid> controla agora usa corrigir cores do tema. Por exemplo:

    Antes: 

    ![Seta de indicador de classificação antes de aprimoramentos de acessibilidade](media/sort-indicator-before.png) 
    
    Depois:   
 
    ![Seta de indicador de classificação depois de aprimoramentos de acessibilidade](media/sort-indicator-after.png) 
    
    Além disso, no .NET Framework 4.7 e versões anteriores, o estilo de link padrão alterada para uma cor incorretova no mouse nos modos de alto contraste. Isso é resolvido a partir do .NET Framework 4.7.1. Da mesma forma, <xref:System.Windows.Controls.DataGrid> caixa de seleção colunas usa as cores esperadas para comentários de foco do teclado iniciando com o .NET Framework 4.7.1.

    Antes: 

    ![Estilo de link do DataGrid padrão antes de aprimoramentos de acessibilidade](media/default-link-style-before.png) 
 
    Depois:    
  
    ![Estilo de link padrão DataGrid depois de aprimoramentos de acessibilidade](media/default-link-style-after.png)  

Para obter mais informações sobre aprimoramentos de acessibilidade do WPF no .NET Framework 4.7.1, consulte [aprimoramentos de acessibilidade no WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

## <a name="windows-forms-accessibility-improvements"></a>Aprimoramentos de acessibilidade do Windows Forms

No .NET Framework 4.7.1, o Windows Forms (WinForms) inclui alterações de acessibilidade nas seguintes áreas.

**Vídeo aprimorado no modo de alto contraste**

Iniciando com o .NET Framework 4.7.1, vários controles WinForms oferecem maior processamento nos modos de alto contraste será disponíveis no sistema operacional. Windows 10 foi alterado os valores para algumas cores do sistema de alto contraste e formulários do Windows é baseado na estrutura do Windows 10 Win32. Para obter a melhor experiência, execute a versão mais recente do Windows e aceitar as alterações mais recentes do sistema operacional, adicionando que um arquivo App. manifest em um aplicativo de teste e cancelar os comentários do Windows 10 com suporte de linha de sistema operacional para que ele tenha o seguinte:

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
Alguns exemplos de alterações de alto contraste incluem:

- Marcas de seleção no <xref:System.Windows.Forms.MenuStrip> itens são mais fáceis de ler.

- Quando selecionado, desabilitado <xref:System.Windows.Forms.MenuStrip> itens são mais fáceis de ler.

- Texto em um selecionado <xref:System.Windows.Forms.Button> controlar contrasta com a cor da seleção.

- Texto desabilitado é mais fácil de ler. Por exemplo:

    Antes:

    ![Texto desabilitado antes de aprimoramentos de acessibilidade](media/wf-disabled-before.png) 

    Depois:

    ![Texto desabilitado depois aprimoramentos de acessibilidade](media/wf-disabled-after.png) 

- Melhorias de alto contraste na caixa de diálogo exceção de Thread.

**Suporte aprimorado do Narrator**

Windows Forms no .NET Framework 4.7.1 inclui os seguintes aprimoramentos de acessibilidade para o Narrator:

- O <xref:System.Windows.Forms.MonthCalendar> controle pode ser acessado pelo Narrator, bem como por outras ferramentas de automação de interface do usuário.

- O <xref:System.Windows.Forms.CheckedListBox> controle notifica o Narrator quando o estado de seleção do item mudou para o usuário será notificado de que eles alterou o valor de um item de lista.
 
- O <xref:System.Windows.Forms.DataGridViewCell> controle relata o status de somente leitura correto para o Narrator.
 
- O Narrator poderá ler desabilitado <xref:System.Windows.Forms.ToolStripMenuItem> texto, enquanto que anteriormente ele seria ignorar itens de menu desativado.

**Suporte aprimorado para padrões de acessibilidade de automação da IU**

Iniciando com o .NET Framework 4.7.1, os desenvolvedores de ferramentas de tecnologia de acessibilidade podem aproveitar padrões comuns de acessibilidade de API e as propriedades de vários controles WinForms. Esses aprimoramentos de acessibilidade incluem:

- O <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ToolStripSplitButton> agora oferecem suporte a [padrão Expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
 
- O <xref:System.Windows.Forms.DataGridViewCheckBoxCell> agora oferece suporte a [padrão toggle](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).
 
- O <xref:System.Windows.Forms.ToolStripItem> controle oferece suporte a <xref:System.Windows.Automation.AutomationElement.Name> propriedade e o [padrão Expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- O <xref:System.Windows.Forms.NumericUpDown> e <xref:System.Windows.Forms.DomainUpDown> controla o suporte a <xref:System.Windows.Automation.automationElement.Name> propriedade.

**Propriedade melhor experiência de navegador**

Iniciando com o .NET Framework 4.7.1, formulários do Windows incluem:

- Navegação de teclado melhor por meio de várias janelas de seleção de lista suspensa.
- Uma redução de paradas de tabulação desnecessários.
- Melhor relatório de tipos de controle.
- O narrator melhor comportamento.
 
## <a name="see-also"></a>Consulte também
[O que há de novo no .NET Framework](whats-new.md)   
 
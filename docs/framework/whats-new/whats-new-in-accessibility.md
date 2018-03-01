---
title: Novidades na acessibilidade do .NET Framework
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6a6759ae285f2dd101bddf71ea8e5ca792e87df
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Novidades na acessibilidade do .NET Framework

O .NET Framework pretende tornar os aplicativos mais acessíveis para os usuários. As funcionalidades de acessibilidade permitem que um aplicativo forneça uma experiência apropriada para os usuários da Tecnologia Adaptativa. A partir do .NET Framework 4.7.1, o .NET Framework inclui diversas melhorias de acessibilidade que permitem aos desenvolvedores criar aplicativos acessíveis. 

As novas funcionalidades de acessibilidade são habilitadas por padrão para os aplicativos direcionados a o .NET Framework 4.7.1 ou posterior. Além disso, os aplicativos direcionados a uma versão anterior do .NET Framework, mas que estão em execução no .NET Framework 4.7.1 ou posterior, podem recusar os comportamentos de acessibilidade herdados (e, portanto, aceitar as melhorias de acessibilidade do .NET Framework 4.7.1) adicionando a opção a seguir ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Da mesma forma, os aplicativos direcionados a versões do .NET Framework a partir do 4.7.1 podem desabilitar as funcionalidades de acessibilidade adicionando a opção a seguir ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>Novidades na acessibilidade do .NET Framework 4.7.1

O .NET Framework 4.7.1 inclui novas funcionalidades de acessibilidade nas seguintes áreas:

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows Forms](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Melhorias do leitor de tela**

Se as melhorias de acessibilidade estiverem habilitadas, o .NET Framework 4.7.1 incluirá as seguintes melhorias que afetam os leitores de tela:

- No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.Expander> foram divulgados pelos leitores de tela como botões. A partir do .NET Framework 4.7.1, eles são corretamente divulgados como grupos expansíveis/recolhíveis.

- No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.DataGridCell> foram divulgados pelos leitores de tela como “personalizados”. A partir do .NET Framework 4.7.1, agora eles são corretamente divulgados como célula de grade de dados (localizada).
 
- A partir do .NET Framework 4.7.1, os leitores de tela divulgam o nome de uma <xref:System.Windows.Controls.ComboBox> editável.

- No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.PasswordBox> eram divulgados como “nenhum item em exibição” ou, de outro modo, apresentavam um comportamento incorreto. Esse problema é corrigido a partir do .NET Framework 4.7.1.     

**Suporte a UIAutomation LiveRegion**

Leitores de tela, como o Narrador, ajudam as pessoas a ler o conteúdo da interface do usuário de um aplicativo, normalmente, pela saída de conversão de texto em fala do conteúdo da interface do usuário que tem o foco. No entanto, se um elemento da interface do usuário for alterado e não tiver o foco, o usuário poderá não ser notificado e perder informações importantes. As regiões dinâmicas pretendem resolver esse problema. Um desenvolvedor pode usá-las para informar o leitor de tela ou qualquer outro cliente de UIAutomation de que foi feita uma alteração importante em um elemento da interface do usuário. Em seguida, o leitor de tela pode decidir como e quando informar o usuário dessa alteração. 

Para dar suporte a regiões dinâmicas, as seguintes APIs foram adicionadas ao WPF:

- Os campos <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, que identificam a propriedade **LiveSetting** e o evento **LiveRegionChanged**. Eles podem ser definidos com XAML.

- A propriedade anexada **AutomationProperties.LiveSetting**, que informa o leitor de tela da importância da alteração da interface do usuário para o usuário.

- A propriedade <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, que identifica a propriedade anexada **AutomationProperties.LiveSetting**.
 
- O método <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, que pode ser substituído para fornecer um valor de **LiveSetting**.

- Os métodos <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, que obtêm e definem um valor de **LiveSetting**.
 
- A enumeração <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, que define os seguintes possíveis valores de **LiveSetting**:

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. O elemento não envia notificações se o conteúdo da região dinâmica foi alterado.   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. O elemento enviará notificações não interruptivas se o conteúdo da região dinâmica tiver sido alterado.   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. O elemento enviará notificações interruptivas se o conteúdo da região dinâmica tiver sido alterado.   

Crie uma LiveRegion configurar a propriedade **AutomationProperties.LiveSetting** no elemento de interesse, conforme mostrado no seguinte exemplo:   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Quando os dados da região dinâmica forem alterados e você precisar informar um leitor de tela, acione um evento explicitamente, conforme mostrado na amostra a seguir.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Alto contraste**

A partir do .NET Framework 4.7.1, foram feitas melhorias de alto contraste em vários controles do WPF. Agora eles estão visíveis quando o tema <xref:System.Windows.SystemParameters.HighContrast%2A> é definido. Elas incluem:

- Controle <xref:System.Windows.Controls.Expander>

    O visual de foco do controle <xref:System.Windows.Controls.Expander> agora está visível. Os visuais de teclado dos controles <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.RadioButton> também estão visíveis. Por exemplo:

    Antes: 
    
    ![Controle expansor com foco antes das melhorias de acessibilidade](media/expander-before.png)

    Depois: 

    ![Controle expansor com foco após as melhorias de acessibilidade](media/expander-after.png)

- Controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton>
 
    O texto nos controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton> agora é de visualização mais fácil quando selecionado em temas de alto contraste. Por exemplo:

    Antes: 

    ![Botão de opção de alto contraste com foco antes das melhorias de acessibilidade](media/radio-button-before.png)
    
    Depois: 

    ![Botão de opção de alto contraste com foco após as melhorias de acessibilidade](media/radio-button-after.png)

- Controle <xref:System.Windows.Controls.ComboBox>
 
    A partir do .NET Framework 4.7.1, a borda de um controle <xref:System.Windows.Controls.ComboBox> desabilitado é da mesma cor do texto desabilitado. Por exemplo:
    
    Antes: 

     ![Borda e texto desabilitados da ComboBox antes das melhorias de acessibilidade](media/combo-disabled-before.png)

    Depois:   

     ![Borda e texto desabilitados da ComboBox após as melhorias de acessibilidade](media/combo-disabled-after.png)

    Além disso, os botões desabilitados e com foco usam a cor de tema correta.

    Antes:

    ![Cores de tema do botão antes das melhorias de acessibilidade](media/button-themes-before.png) 
    
    Depois: 

    ![Cores de tema do botão após as melhorias de acessibilidade](media/button-themes-after.png) 

    Por fim, no .NET Framework 4.7 e em versões anteriores, a configuração do estilo de um controle <xref:System.Windows.Controls.ComboBox> como `Toolbar.ComboBoxStyleKey` fazia com que a seta suspensa ficasse invisível. Esse problema é corrigido a partir do .NET Framework 4.7.1. Por exemplo:

    Antes: 

    ![Toolbar.ComboBoxStyleKey antes das melhorias de acessibilidade](media/comboboxstylekey-before.png) 
    
    Depois: 

    ![Toolbar.ComboBoxStyleKey após as melhorias de acessibilidade](media/comboboxstylekey-after.png) 

- Controle <xref:System.Windows.Controls.DataGrid>

    A partir do .NET Framework 4.7.1, a seta do indicador de classificação nos controles <xref:System.Windows.Controls.DataGrid> agora usa as cores de tema corretas. Por exemplo:

    Antes: 

    ![Seta do indicador de classificação antes das melhorias de acessibilidade](media/sort-indicator-before.png) 
    
    Depois:   
 
    ![Seta do indicador de classificação após as melhorias de acessibilidade](media/sort-indicator-after.png) 
    
    Além disso, no .NET Framework 4.7 e em versões anteriores, o estilo de link padrão era alterado para uma cor incorreta ao passar o mouse nos modos de alto contraste. Isso é resolvido a partir do .NET Framework 4.7.1. Da mesma forma, as colunas da caixa de seleção <xref:System.Windows.Controls.DataGrid> usam as cores esperadas para os comentários do foco de teclado a partir do .NET Framework 4.7.1.

    Antes: 

    ![Estilo de link padrão de DataGrid antes das melhorias de acessibilidade](media/default-link-style-before.png) 
 
    Depois:    
  
    ![Estilo de link padrão de DataGrid após as melhorias de acessibilidade](media/default-link-style-after.png)  

Para obter mais informações sobre as melhorias de acessibilidade do WPF no .NET Framework 4.7.1, consulte [Melhorias de acessibilidade no WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

## <a name="windows-forms-accessibility-improvements"></a>Melhorias de acessibilidade do Windows Forms

No .NET Framework 4.7.1, o WinForms (Windows Forms) inclui alterações de acessibilidade nas áreas a seguir.

**Vídeo aprimorado no modo de Alto Contraste**

A partir do .NET Framework 4.7.1, vários controles do WinForms oferecem uma melhor renderização nos modos de HighContrast disponíveis no sistema operacional. O Windows 10 alterou os valores de algumas cores do sistema de alto contraste e o Windows Forms é baseado na estrutura Win32 do Windows 10. Para obter a melhor experiência, execute a última versão do Windows e aceite as últimas alterações do sistema operacional adicionando um arquivo app.manifest a um aplicativo de teste e remova a marca de comentário da linha de sistema operacional com suporte do Windows 10 para que ela seja semelhante à seguinte:

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
Alguns exemplos de alterações de alto contraste incluem:

- Marcas de seleção em itens <xref:System.Windows.Forms.MenuStrip> são mais fáceis de serem exibidas.

- Quando selecionados, os itens <xref:System.Windows.Forms.MenuStrip> desabilitados são mais fáceis de serem exibidos.

- O texto em um controle <xref:System.Windows.Forms.Button> selecionado contrasta com a cor da seleção.

- O texto desabilitado é mais fácil de ser lido. Por exemplo:

    Antes:

    ![Texto desabilitado antes das melhorias de acessibilidade](media/wf-disabled-before.png) 

    Depois:

    ![Texto desabilitado após as melhorias de acessibilidade](media/wf-disabled-after.png) 

- Melhorias de alto contraste na caixa de diálogo Exceção de Thread.

**Melhor suporte ao Narrador**

O Windows Forms no .NET Framework 4.7.1 inclui as seguintes melhorias de acessibilidade para o Narrador:

- O controle <xref:System.Windows.Forms.MonthCalendar> pode ser acessado pelo Narrador, bem como por outras ferramentas de automação da interface do usuário.

- O controle <xref:System.Windows.Forms.CheckedListBox> notifica o Narrador quando o estado de seleção do item foi alterado, para que o usuário seja notificado de que ele alterou o valor de um item de lista.
 
- O controle <xref:System.Windows.Forms.DataGridViewCell> relata o status somente leitura correto para o Narrador.
 
- O Narrador agora pode ler o texto <xref:System.Windows.Forms.ToolStripMenuItem> desabilitado, enquanto, anteriormente, ele ignorava itens de menu desabilitados.

**Suporte aprimorado para padrões de acessibilidade de UIAutomation**

A partir do .NET Framework 4.7.1, os desenvolvedores de ferramentas de tecnologia de acessibilidade podem utilizar padrões comuns de acessibilidade de API e as propriedades de vários controles WinForms. Essas melhorias de acessibilidade incluem:

- O <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ToolStripSplitButton> agora dão suporte ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
 
- O <xref:System.Windows.Forms.DataGridViewCheckBoxCell> agora dá suporte ao [padrão alternar](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).
 
- O controle <xref:System.Windows.Forms.ToolStripItem> dá suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> e ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- Os controles <xref:System.Windows.Forms.NumericUpDown> e <xref:System.Windows.Forms.DomainUpDown> dão suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.

**Melhor experiência do navegador de propriedades**

A partir do .NET Framework 4.7.1, o Windows Forms inclui:

- Melhor navegação de teclado por meio das várias janelas de seleção suspensa.
- Uma redução de paradas de tabulação desnecessárias.
- Melhor relatório de tipos de controle.
- Melhor comportamento do Narrador.
 
## <a name="see-also"></a>Consulte também
[Novidades do .NET Framework](whats-new.md)   
 
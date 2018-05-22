---
title: Novidades na acessibilidade do .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fe7e15e482028b9988d7e560b98be19b6c07427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Novidades na acessibilidade do .NET Framework

O .NET Framework pretende tornar os aplicativos mais acessíveis para os usuários. As funcionalidades de acessibilidade permitem que um aplicativo forneça uma experiência apropriada para os usuários da Tecnologia Adaptativa. A partir do .NET Framework 4.7.1, o .NET Framework inclui diversas melhorias de acessibilidade que permitem aos desenvolvedores criar aplicativos acessíveis. 

## <a name="accessibility-switches"></a>Opções de acessibilidade

Configure seu aplicativo para aceitar os recursos de acessibilidade se ele for direcionado ao .NET Framework 4.7 ou a uma versão anterior, mas estiver em execução no .NET Framework 4.7.1 ou posterior. Além disso, configure seu aplicativo para usar recursos herdados (e não aproveitar os recursos de acessibilidade) se ele for direcionado ao .NET Framework 4.7.1 ou posterior. Cada versão do .NET Framework que inclui recursos de acessibilidade tem uma opção de acessibilidade específica à versão, que você adiciona ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo. Estas são as opções compatíveis:

|Versão|Alternar|
|---|---|
|.NET Framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
|.NET Framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Aproveitando as vantagens das melhorias de acessibilidade

As novas funcionalidades de acessibilidade são habilitadas por padrão para os aplicativos direcionados a o .NET Framework 4.7.1 ou posterior. Além disso, os aplicativos direcionados a uma versão anterior do .NET Framework, mas que estão em execução no .NET Framework 4.7.1 ou posterior, podem recusar os comportamentos de acessibilidade herdados (e, portanto, aproveitar as melhorias de acessibilidade) adicionando opções ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo e definindo seu valor como `false`. O seguinte exemplo mostra como aceitar as melhorias de acessibilidade introduzidas no .NET Framework 4.7.1:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Se você optar por aceitar os recursos de acessibilidade em uma versão posterior do .NET Framework, deverá também aceitar explicitamente os recursos de versões anteriores do .NET Framework. A configuração do aplicativo para aproveitar as melhorias de acessibilidade do .NET Framework 4.7.1 e 4.7.2 exige o seguinte elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Restaurando o comportamento herdado

Os aplicativos direcionados a versões do .NET Framework a começar pela 4.7.1 podem desabilitar os recursos de acessibilidade adicionando opções ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo e definindo seu valor como `true`. Por exemplo, a seguinte configuração recusa os recursos de acessibilidade introduzidos no .NET Framework 4.7.2:  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a>Novidades na acessibilidade do .NET Framework 4.7.2

O .NET Framework 4.7.2 inclui novos recursos de acessibilidade nas seguintes áreas:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a>Windows Forms

**Cores definidas pelo sistema operacional em temas de Alto Contraste**

Começando no .NET Framework 4.7.2, o Windows Forms usa cores definidas pelo sistema operacional em temas de Alto Contraste. Isso afeta os seguintes controles:

- A seta suspensa do controle <xref:System.Windows.Forms.ToolStripDropDownButton>.

- Os controles <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> e <xref:System.Windows.Forms.CheckBox> com <xref:System.Windows.Forms.ButtonBase.FlatStyle> definido como <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> ou <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>. Anteriormente, as cores de texto e da tela de fundo selecionadas não eram contrastantes e eram difíceis de serem lidas.

- Os controles contidos em uma <xref:System.Windows.Forms.GroupBox> que tem sua propriedade <xref:System.Windows.Forms.Control.Enabled> definida como `false`.
 
- Os controles <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox> e <xref:System.Windows.Forms.ToolStripDropDownButton>, que têm uma taxa maior de contraste de luminosidade no Modo de Alto Contraste.

- A propriedade <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> do <xref:System.Windows.Forms.DataGridViewLinkCell>.

**Melhorias do Narrador**

Começando no .NET Framework 4.7.2, o suporte ao Narrador é aprimorado da seguinte maneira:

- Ele anuncia o valor da propriedade <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> quando anuncia o texto de um <xref:System.Windows.Forms.ToolStripMenuItem>. 

- Ele indica quando um <xref:System.Windows.Forms.ToolStripMenuItem> tem sua propriedade <xref:System.Windows.Forms.Control.Enabled> definida como `false`.

- Ele fornece comentários sobre o estado de uma caixa de seleção quando a propriedade <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> está definida como `true`.

- A ordem de foco do Modo de Verificação do Narrador é consistente com a ordem visual dos controles na janela de diálogo de download do ClickOnce.

**Melhorias de DataGridView**

Começando no .NET Framework 4.7.2, o controle <xref:System.Windows.Forms.DataGridView> introduziu as seguintes melhorias de acessibilidade:

- As linhas podem ser classificadas com o teclado. Um usuário pode usar a tecla F3 para classificar pela coluna atual.

- Quando o <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> é definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, o cabeçalho da coluna muda de cor para indicar a coluna atual, à medida que o usuário pressiona Tab para percorrer as células na linha atual.

- A propriedade <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> de um <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> retorna o controle pai correto.

**Melhoria das indicações visuais**

- Os controles <xref:System.Windows.Forms.RadioButton> e <xref:System.Windows.Forms.CheckBox> com uma propriedade <xref:System.Windows.Forms.ButtonBase.Text> vazia exibem um indicador de foco quando recebem o foco.

**Melhoria no suporte à grade de propriedade**

- Os elementos filhos do controle <xref:System.Windows.Forms.PropertyGrid> agora retornam um `true` para a propriedade <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> somente quando um elemento PropertyGrid está habilitado.

- Os elementos filho do controle <xref:System.Windows.Forms.PropertyGrid> retornam um `false` para a propriedade <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> somente quando um elemento PropertyGrid pode ser alterado pelo usuário.

**Melhoria na navegação por teclado**

- O controle <xref:System.Windows.Forms.ToolStripButton> permite o foco quando contido em um <xref:System.Windows.Forms.ToolStripPanel> que tem a propriedade <xref:System.Windows.Forms.ToolStripPanel.TabStop> definida como `true`

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Alterações nos controles CheckBox e RadioButton**

No .NET Framework 4.7.1 e nas versões anteriores, os controles <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> e <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> do WPF têm visuais de foco inconsistentes e, nos temas Clássico e de Alto Contraste, eles têm visuais de foco incorretos.  Esses problemas ocorrem quando os controles não têm nenhum conjunto de conteúdo.  Isso pode dificultar a transição entre os temas e deixar o visual de foco confuso.

No .NET Framework 4.7.2, agora esses visuais são mais consistentes entre os temas e mais facilmente visíveis nos temas Clássico e de Alto Contraste.

**Controles do WinForms hospedados em um aplicativo WPF**

Para controles do WinForms hospedados em um aplicativo do WPF no .NET Framework 4.7.1 e versões anteriores, os usuários não podem sair da guia da camada do WinForms se o primeiro ou o último controle da camada é o controle <xref:System.Windows.Forms.Integration.ElementHost> do WPF. No .NET Framework 4.7.2, os usuários agora podem sair da guia da camada do WinForms.

No entanto, os aplicativos automatizados que se baseiam em foco e que nunca são escapados da camada do WinForms podem deixar de funcionar conforme o esperado.

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>Novidades na acessibilidade do .NET Framework 4.7.1

O .NET Framework 4.7.1 inclui novas funcionalidades de acessibilidade nas seguintes áreas:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [Controles da Web do ASP.NET](#aspnet471)

- [Ferramentas do SDK do .NET](#tools471)

- [Designer de Fluxo de Trabalho do WF (Windows Workflow Foundation)](#wf471)

<a name="wpf471"></a>
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

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a>Melhorias de acessibilidade do Windows Forms

No .NET Framework 4.7.1, o WinForms (Windows Forms) inclui alterações de acessibilidade nas áreas a seguir.

**Vídeo aprimorado no modo de Alto Contraste**

A partir do .NET Framework 4.7.1, vários controles do WinForms oferecem uma melhor renderização nos modos de HighContrast disponíveis no sistema operacional. O Windows 10 alterou os valores de algumas cores do sistema de alto contraste e o Windows Forms é baseado na estrutura Win32 do Windows 10. Para obter a melhor experiência, execute a última versão do Windows e aceite as últimas alterações do sistema operacional adicionando um arquivo app.manifest a um aplicativo de teste e remova a marca de comentário da linha de sistema operacional com suporte do Windows 10 para que ela seja semelhante à seguinte:

```xml
<!-- Windows 10 -->
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
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a>Controles da Web do ASP.NET

Começando no .NET Framework 4.7.1 e no Visual Studio 2017 15.3, o ASP.NET melhorará o funcionamento dos controles da Web do ASP.NET com a tecnologia de acessibilidade no Visual Studio. As alterações incluem as seguintes:

- Alterações para implementar padrões de acessibilidade de interface do usuário ausentes em controles como a caixa de diálogo **Adicionar Campo** no assistente de **Exibição de Detalhes** ou a caixa de diálogo **Configurar ListView** do assistente **ListView**.

- Alterações para melhorar a exibição no modo de Alto Contraste, como o **Editor de Campos do Pager de Dados**.

- Alterações para melhorar as experiências de navegação por teclado para controles como a caixa de diálogo **Campos** no assistente **Editar Campos do Pager** do controle DataPager, a caixa de diálogo **Configurar ObjectContext** ou a caixa de diálogo **Configurar Seleção de Dados** do assistente **Configurar Fonte de Dados**.

<a name="tools471"></a>
## <a name="net-sdk-tools"></a>Ferramentas do SDK do .NET

A [Ferramenta Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) e a [Ferramenta Service Trace Viewer (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) foram aprimoradas com a correção de problemas variados de acessibilidade. A maioria eram problemas pequenos, como um nome que não está definido ou certos padrões de automação de interface do usuário implementados incorretamente. Embora muitos usuários não estejam cientes desses valores incorretos, os clientes que usam tecnologias adaptativas como leitores de tela considerarão essas ferramentas de SDK mais acessíveis. 

Essas melhorias alteram alguns comportamentos anteriores, como a ordem de foco do teclado.

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a>Designer de Fluxo de Trabalho do WF (Windows Workflow Foundation)

As alterações de acessibilidade no Designer de Fluxo de Trabalho incluem as seguintes:

- A ordem de tabulação é alterada para a esquerda para a direita e de cima para baixo em alguns controles:

  - A janela de inicialização de correlação para definir dados de correlação para a atividade <xref:System.ServiceModel.Activities.InitializeCorrelation>.

  - A janela de definição de conteúdo para as atividades <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>.

- Mais funções estão disponíveis por meio do teclado:

  - Ao editar as propriedades de uma atividade, grupos de propriedades podem ser recolhidos pelo teclado na primeira vez em que são colocados em foco.

  - Ícones de aviso podem ser acessados por teclado.

  - O botão **Mais Propriedades** na janela **Propriedades** pode ser acessado pelo teclado.

  - Usuários do teclado podem acessar os itens de cabeçalho nos painéis **Argumentos** e **Variáveis** do Designer de Fluxo de Trabalho.

- Melhor visibilidade de itens com foco, como ao:

  - Adicionar linhas às grades de dados usadas pelo Designer de Fluxo de Trabalho e por designers de atividades.

  - Percorrer campos nas atividades <xref:System.ServiceModel.Activities.ReceiveReply> e <xref:System.ServiceModel.Activities.SendReply>.

  - Definir valores padrão para variáveis ou argumentos

- Agora, leitores de tela podem reconhecer corretamente:

  - Pontos de interrupção definidos no Designer de Fluxo de Trabalho.

  - As atividades <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision> e <xref:System.ServiceModel.Activities.CorrelationScope>.
  - O conteúdo da atividade <xref:System.ServiceModel.Activities.Receive>.

  - O Tipo de Destino da atividade <xref:System.Activities.Statements.InvokeMethod>.

  - A caixa de combinação Exceção e a seção Finalmente na atividade <xref:System.Activities.Statements.TryCatch>.

  - A caixa de combinação Tipo de Mensagem, o divisor na janela Adicionar Inicializadores de Correlação, a janela Definição de Conteúdo e a janela de Definição de CorrelatesOn nas atividades de mensagens (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>).

  - Transições de máquinas de estado e destinos de transição.

  - Anotações e conectores em atividades <xref:System.Activities.Statements.FlowDecision>.

  - Os menus de contexto (clique com o botão direito do mouse) para atividades.

  - Os editores de valor de propriedade, o botão Limpar Pesquisa, os botões de classificação Por Categoria e Ordem Alfabética e a caixa de diálogo Editor de Expressão na grade de propriedades.

  - A porcentagem de zoom no Designer de Fluxo de Trabalho.

  - O separador nas atividades <xref:System.Activities.Statements.Parallel> e <xref:System.Activities.Statements.Pick>.

  - A atividade <xref:System.Activities.Statements.InvokeDelegate>.

  - A janela Selecionar Tipos para atividades de dicionário (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` etc.).

  - A janela Procurar e Selecionar um Tipo .NET.

  - Trilhas de navegação no Designer de Fluxo de Trabalho.

- Usuários que escolherem temas de Alto Contraste verão muitas melhorias na visibilidade do Designer de Fluxo de Trabalho e em seus controles, como melhores taxas de contraste entre elementos e caixas de seleção mais perceptíveis usadas para elementos de foco.

## <a name="see-also"></a>Consulte também

[Novidades do .NET Framework](whats-new.md)
 

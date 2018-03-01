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
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="d4153-102">Novidades na acessibilidade do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d4153-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="d4153-103">O .NET Framework pretende tornar os aplicativos mais acessíveis para os usuários.</span><span class="sxs-lookup"><span data-stu-id="d4153-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="d4153-104">As funcionalidades de acessibilidade permitem que um aplicativo forneça uma experiência apropriada para os usuários da Tecnologia Adaptativa.</span><span class="sxs-lookup"><span data-stu-id="d4153-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="d4153-105">A partir do .NET Framework 4.7.1, o .NET Framework inclui diversas melhorias de acessibilidade que permitem aos desenvolvedores criar aplicativos acessíveis.</span><span class="sxs-lookup"><span data-stu-id="d4153-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="d4153-106">As novas funcionalidades de acessibilidade são habilitadas por padrão para os aplicativos direcionados a o .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="d4153-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="d4153-107">Além disso, os aplicativos direcionados a uma versão anterior do .NET Framework, mas que estão em execução no .NET Framework 4.7.1 ou posterior, podem recusar os comportamentos de acessibilidade herdados (e, portanto, aceitar as melhorias de acessibilidade do .NET Framework 4.7.1) adicionando a opção a seguir ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d4153-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="d4153-108">Da mesma forma, os aplicativos direcionados a versões do .NET Framework a partir do 4.7.1 podem desabilitar as funcionalidades de acessibilidade adicionando a opção a seguir ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d4153-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="d4153-109">Novidades na acessibilidade do .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="d4153-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="d4153-110">O .NET Framework 4.7.1 inclui novas funcionalidades de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="d4153-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="d4153-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="d4153-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="d4153-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d4153-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="d4153-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="d4153-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="d4153-114">**Melhorias do leitor de tela**</span><span class="sxs-lookup"><span data-stu-id="d4153-114">**Screen reader improvements**</span></span>

<span data-ttu-id="d4153-115">Se as melhorias de acessibilidade estiverem habilitadas, o .NET Framework 4.7.1 incluirá as seguintes melhorias que afetam os leitores de tela:</span><span class="sxs-lookup"><span data-stu-id="d4153-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="d4153-116">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.Expander> foram divulgados pelos leitores de tela como botões.</span><span class="sxs-lookup"><span data-stu-id="d4153-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="d4153-117">A partir do .NET Framework 4.7.1, eles são corretamente divulgados como grupos expansíveis/recolhíveis.</span><span class="sxs-lookup"><span data-stu-id="d4153-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="d4153-118">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.DataGridCell> foram divulgados pelos leitores de tela como “personalizados”.</span><span class="sxs-lookup"><span data-stu-id="d4153-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="d4153-119">A partir do .NET Framework 4.7.1, agora eles são corretamente divulgados como célula de grade de dados (localizada).</span><span class="sxs-lookup"><span data-stu-id="d4153-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="d4153-120">A partir do .NET Framework 4.7.1, os leitores de tela divulgam o nome de uma <xref:System.Windows.Controls.ComboBox> editável.</span><span class="sxs-lookup"><span data-stu-id="d4153-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="d4153-121">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.PasswordBox> eram divulgados como “nenhum item em exibição” ou, de outro modo, apresentavam um comportamento incorreto.</span><span class="sxs-lookup"><span data-stu-id="d4153-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="d4153-122">Esse problema é corrigido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="d4153-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="d4153-123">**Suporte a UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="d4153-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="d4153-124">Leitores de tela, como o Narrador, ajudam as pessoas a ler o conteúdo da interface do usuário de um aplicativo, normalmente, pela saída de conversão de texto em fala do conteúdo da interface do usuário que tem o foco.</span><span class="sxs-lookup"><span data-stu-id="d4153-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="d4153-125">No entanto, se um elemento da interface do usuário for alterado e não tiver o foco, o usuário poderá não ser notificado e perder informações importantes.</span><span class="sxs-lookup"><span data-stu-id="d4153-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="d4153-126">As regiões dinâmicas pretendem resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="d4153-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="d4153-127">Um desenvolvedor pode usá-las para informar o leitor de tela ou qualquer outro cliente de UIAutomation de que foi feita uma alteração importante em um elemento da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d4153-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="d4153-128">Em seguida, o leitor de tela pode decidir como e quando informar o usuário dessa alteração.</span><span class="sxs-lookup"><span data-stu-id="d4153-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="d4153-129">Para dar suporte a regiões dinâmicas, as seguintes APIs foram adicionadas ao WPF:</span><span class="sxs-lookup"><span data-stu-id="d4153-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="d4153-130">Os campos <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, que identificam a propriedade **LiveSetting** e o evento **LiveRegionChanged**.</span><span class="sxs-lookup"><span data-stu-id="d4153-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="d4153-131">Eles podem ser definidos com XAML.</span><span class="sxs-lookup"><span data-stu-id="d4153-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="d4153-132">A propriedade anexada **AutomationProperties.LiveSetting**, que informa o leitor de tela da importância da alteração da interface do usuário para o usuário.</span><span class="sxs-lookup"><span data-stu-id="d4153-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="d4153-133">A propriedade <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, que identifica a propriedade anexada **AutomationProperties.LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="d4153-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="d4153-134">O método <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, que pode ser substituído para fornecer um valor de **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="d4153-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="d4153-135">Os métodos <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, que obtêm e definem um valor de **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="d4153-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="d4153-136">A enumeração <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, que define os seguintes possíveis valores de **LiveSetting**:</span><span class="sxs-lookup"><span data-stu-id="d4153-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="d4153-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4153-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d4153-138">O elemento não envia notificações se o conteúdo da região dinâmica foi alterado.</span><span class="sxs-lookup"><span data-stu-id="d4153-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="d4153-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4153-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d4153-140">O elemento enviará notificações não interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="d4153-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="d4153-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4153-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d4153-142">O elemento enviará notificações interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="d4153-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="d4153-143">Crie uma LiveRegion configurar a propriedade **AutomationProperties.LiveSetting** no elemento de interesse, conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4153-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="d4153-144">Quando os dados da região dinâmica forem alterados e você precisar informar um leitor de tela, acione um evento explicitamente, conforme mostrado na amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4153-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="d4153-145">**Alto contraste**</span><span class="sxs-lookup"><span data-stu-id="d4153-145">**High contrast**</span></span>

<span data-ttu-id="d4153-146">A partir do .NET Framework 4.7.1, foram feitas melhorias de alto contraste em vários controles do WPF.</span><span class="sxs-lookup"><span data-stu-id="d4153-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="d4153-147">Agora eles estão visíveis quando o tema <xref:System.Windows.SystemParameters.HighContrast%2A> é definido.</span><span class="sxs-lookup"><span data-stu-id="d4153-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="d4153-148">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="d4153-148">These include:</span></span>

- <span data-ttu-id="d4153-149">Controle <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="d4153-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="d4153-150">O visual de foco do controle <xref:System.Windows.Controls.Expander> agora está visível.</span><span class="sxs-lookup"><span data-stu-id="d4153-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="d4153-151">Os visuais de teclado dos controles <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.RadioButton> também estão visíveis.</span><span class="sxs-lookup"><span data-stu-id="d4153-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="d4153-152">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4153-152">For example:</span></span>

    <span data-ttu-id="d4153-153">Antes:</span><span class="sxs-lookup"><span data-stu-id="d4153-153">Before:</span></span> 
    
    ![Controle expansor com foco antes das melhorias de acessibilidade](media/expander-before.png)

    <span data-ttu-id="d4153-155">Depois:</span><span class="sxs-lookup"><span data-stu-id="d4153-155">After:</span></span> 

    ![Controle expansor com foco após as melhorias de acessibilidade](media/expander-after.png)

- <span data-ttu-id="d4153-157">Controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton></span><span class="sxs-lookup"><span data-stu-id="d4153-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="d4153-158">O texto nos controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton> agora é de visualização mais fácil quando selecionado em temas de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="d4153-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="d4153-159">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4153-159">For example:</span></span>

    <span data-ttu-id="d4153-160">Antes:</span><span class="sxs-lookup"><span data-stu-id="d4153-160">Before:</span></span> 

    ![Botão de opção de alto contraste com foco antes das melhorias de acessibilidade](media/radio-button-before.png)
    
    <span data-ttu-id="d4153-162">Depois:</span><span class="sxs-lookup"><span data-stu-id="d4153-162">After:</span></span> 

    ![Botão de opção de alto contraste com foco após as melhorias de acessibilidade](media/radio-button-after.png)

- <span data-ttu-id="d4153-164">Controle <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="d4153-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="d4153-165">A partir do .NET Framework 4.7.1, a borda de um controle <xref:System.Windows.Controls.ComboBox> desabilitado é da mesma cor do texto desabilitado.</span><span class="sxs-lookup"><span data-stu-id="d4153-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="d4153-166">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4153-166">For example:</span></span>
    
    <span data-ttu-id="d4153-167">Antes:</span><span class="sxs-lookup"><span data-stu-id="d4153-167">Before:</span></span> 

     ![Borda e texto desabilitados da ComboBox antes das melhorias de acessibilidade](media/combo-disabled-before.png)

    <span data-ttu-id="d4153-169">Depois:</span><span class="sxs-lookup"><span data-stu-id="d4153-169">After:</span></span>   

     ![Borda e texto desabilitados da ComboBox após as melhorias de acessibilidade](media/combo-disabled-after.png)

    <span data-ttu-id="d4153-171">Além disso, os botões desabilitados e com foco usam a cor de tema correta.</span><span class="sxs-lookup"><span data-stu-id="d4153-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="d4153-172">Antes:</span><span class="sxs-lookup"><span data-stu-id="d4153-172">Before:</span></span>

    ![Cores de tema do botão antes das melhorias de acessibilidade](media/button-themes-before.png) 
    
    <span data-ttu-id="d4153-174">Depois:</span><span class="sxs-lookup"><span data-stu-id="d4153-174">After:</span></span> 

    ![Cores de tema do botão após as melhorias de acessibilidade](media/button-themes-after.png) 

    <span data-ttu-id="d4153-176">Por fim, no .NET Framework 4.7 e em versões anteriores, a configuração do estilo de um controle <xref:System.Windows.Controls.ComboBox> como `Toolbar.ComboBoxStyleKey` fazia com que a seta suspensa ficasse invisível.</span><span class="sxs-lookup"><span data-stu-id="d4153-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="d4153-177">Esse problema é corrigido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="d4153-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="d4153-178">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4153-178">For example:</span></span>

    <span data-ttu-id="d4153-179">Antes:</span><span class="sxs-lookup"><span data-stu-id="d4153-179">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey antes das melhorias de acessibilidade](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="d4153-181">Depois:</span><span class="sxs-lookup"><span data-stu-id="d4153-181">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey após as melhorias de acessibilidade](media/comboboxstylekey-after.png) 

- <span data-ttu-id="d4153-183">Controle <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="d4153-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="d4153-184">A partir do .NET Framework 4.7.1, a seta do indicador de classificação nos controles <xref:System.Windows.Controls.DataGrid> agora usa as cores de tema corretas.</span><span class="sxs-lookup"><span data-stu-id="d4153-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="d4153-185">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4153-185">For example:</span></span>

    <span data-ttu-id="d4153-186">Antes:</span><span class="sxs-lookup"><span data-stu-id="d4153-186">Before:</span></span> 

    ![Seta do indicador de classificação antes das melhorias de acessibilidade](media/sort-indicator-before.png) 
    
    <span data-ttu-id="d4153-188">Depois:</span><span class="sxs-lookup"><span data-stu-id="d4153-188">After:</span></span>   
 
    ![Seta do indicador de classificação após as melhorias de acessibilidade](media/sort-indicator-after.png) 
    
    <span data-ttu-id="d4153-190">Além disso, no .NET Framework 4.7 e em versões anteriores, o estilo de link padrão era alterado para uma cor incorreta ao passar o mouse nos modos de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="d4153-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="d4153-191">Isso é resolvido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="d4153-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="d4153-192">Da mesma forma, as colunas da caixa de seleção <xref:System.Windows.Controls.DataGrid> usam as cores esperadas para os comentários do foco de teclado a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="d4153-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="d4153-193">Antes:</span><span class="sxs-lookup"><span data-stu-id="d4153-193">Before:</span></span> 

    ![Estilo de link padrão de DataGrid antes das melhorias de acessibilidade](media/default-link-style-before.png) 
 
    <span data-ttu-id="d4153-195">Depois:</span><span class="sxs-lookup"><span data-stu-id="d4153-195">After:</span></span>    
  
    ![Estilo de link padrão de DataGrid após as melhorias de acessibilidade](media/default-link-style-after.png)  

<span data-ttu-id="d4153-197">Para obter mais informações sobre as melhorias de acessibilidade do WPF no .NET Framework 4.7.1, consulte [Melhorias de acessibilidade no WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="d4153-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="d4153-198">Melhorias de acessibilidade do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d4153-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="d4153-199">No .NET Framework 4.7.1, o WinForms (Windows Forms) inclui alterações de acessibilidade nas áreas a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4153-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="d4153-200">**Vídeo aprimorado no modo de Alto Contraste**</span><span class="sxs-lookup"><span data-stu-id="d4153-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="d4153-201">A partir do .NET Framework 4.7.1, vários controles do WinForms oferecem uma melhor renderização nos modos de HighContrast disponíveis no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="d4153-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="d4153-202">O Windows 10 alterou os valores de algumas cores do sistema de alto contraste e o Windows Forms é baseado na estrutura Win32 do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="d4153-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="d4153-203">Para obter a melhor experiência, execute a última versão do Windows e aceite as últimas alterações do sistema operacional adicionando um arquivo app.manifest a um aplicativo de teste e remova a marca de comentário da linha de sistema operacional com suporte do Windows 10 para que ela seja semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="d4153-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="d4153-204">Alguns exemplos de alterações de alto contraste incluem:</span><span class="sxs-lookup"><span data-stu-id="d4153-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="d4153-205">Marcas de seleção em itens <xref:System.Windows.Forms.MenuStrip> são mais fáceis de serem exibidas.</span><span class="sxs-lookup"><span data-stu-id="d4153-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="d4153-206">Quando selecionados, os itens <xref:System.Windows.Forms.MenuStrip> desabilitados são mais fáceis de serem exibidos.</span><span class="sxs-lookup"><span data-stu-id="d4153-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="d4153-207">O texto em um controle <xref:System.Windows.Forms.Button> selecionado contrasta com a cor da seleção.</span><span class="sxs-lookup"><span data-stu-id="d4153-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="d4153-208">O texto desabilitado é mais fácil de ser lido.</span><span class="sxs-lookup"><span data-stu-id="d4153-208">Disabled text is easier to read.</span></span> <span data-ttu-id="d4153-209">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d4153-209">For example:</span></span>

    <span data-ttu-id="d4153-210">Antes:</span><span class="sxs-lookup"><span data-stu-id="d4153-210">Before:</span></span>

    ![Texto desabilitado antes das melhorias de acessibilidade](media/wf-disabled-before.png) 

    <span data-ttu-id="d4153-212">Depois:</span><span class="sxs-lookup"><span data-stu-id="d4153-212">After:</span></span>

    ![Texto desabilitado após as melhorias de acessibilidade](media/wf-disabled-after.png) 

- <span data-ttu-id="d4153-214">Melhorias de alto contraste na caixa de diálogo Exceção de Thread.</span><span class="sxs-lookup"><span data-stu-id="d4153-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="d4153-215">**Melhor suporte ao Narrador**</span><span class="sxs-lookup"><span data-stu-id="d4153-215">**Improved Narrator support**</span></span>

<span data-ttu-id="d4153-216">O Windows Forms no .NET Framework 4.7.1 inclui as seguintes melhorias de acessibilidade para o Narrador:</span><span class="sxs-lookup"><span data-stu-id="d4153-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="d4153-217">O controle <xref:System.Windows.Forms.MonthCalendar> pode ser acessado pelo Narrador, bem como por outras ferramentas de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d4153-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="d4153-218">O controle <xref:System.Windows.Forms.CheckedListBox> notifica o Narrador quando o estado de seleção do item foi alterado, para que o usuário seja notificado de que ele alterou o valor de um item de lista.</span><span class="sxs-lookup"><span data-stu-id="d4153-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="d4153-219">O controle <xref:System.Windows.Forms.DataGridViewCell> relata o status somente leitura correto para o Narrador.</span><span class="sxs-lookup"><span data-stu-id="d4153-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="d4153-220">O Narrador agora pode ler o texto <xref:System.Windows.Forms.ToolStripMenuItem> desabilitado, enquanto, anteriormente, ele ignorava itens de menu desabilitados.</span><span class="sxs-lookup"><span data-stu-id="d4153-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="d4153-221">**Suporte aprimorado para padrões de acessibilidade de UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="d4153-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="d4153-222">A partir do .NET Framework 4.7.1, os desenvolvedores de ferramentas de tecnologia de acessibilidade podem utilizar padrões comuns de acessibilidade de API e as propriedades de vários controles WinForms.</span><span class="sxs-lookup"><span data-stu-id="d4153-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="d4153-223">Essas melhorias de acessibilidade incluem:</span><span class="sxs-lookup"><span data-stu-id="d4153-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="d4153-224">O <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ToolStripSplitButton> agora dão suporte ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d4153-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="d4153-225">O <xref:System.Windows.Forms.DataGridViewCheckBoxCell> agora dá suporte ao [padrão alternar](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d4153-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="d4153-226">O controle <xref:System.Windows.Forms.ToolStripItem> dá suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> e ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="d4153-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="d4153-227">Os controles <xref:System.Windows.Forms.NumericUpDown> e <xref:System.Windows.Forms.DomainUpDown> dão suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.</span><span class="sxs-lookup"><span data-stu-id="d4153-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="d4153-228">**Melhor experiência do navegador de propriedades**</span><span class="sxs-lookup"><span data-stu-id="d4153-228">**Improved property browser experience**</span></span>

<span data-ttu-id="d4153-229">A partir do .NET Framework 4.7.1, o Windows Forms inclui:</span><span class="sxs-lookup"><span data-stu-id="d4153-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="d4153-230">Melhor navegação de teclado por meio das várias janelas de seleção suspensa.</span><span class="sxs-lookup"><span data-stu-id="d4153-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="d4153-231">Uma redução de paradas de tabulação desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="d4153-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="d4153-232">Melhor relatório de tipos de controle.</span><span class="sxs-lookup"><span data-stu-id="d4153-232">Better reporting of control types.</span></span>
- <span data-ttu-id="d4153-233">Melhor comportamento do Narrador.</span><span class="sxs-lookup"><span data-stu-id="d4153-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="d4153-234">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4153-234">See Also</span></span>
[<span data-ttu-id="d4153-235">Novidades do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d4153-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 
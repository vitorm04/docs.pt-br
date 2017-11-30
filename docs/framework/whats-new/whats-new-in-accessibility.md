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
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="4ca1a-102">O que há de novo no acessibilidade no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4ca1a-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="4ca1a-103">O .NET Framework pretende fazer mais acessíveis para os usuários de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="4ca1a-104">Recursos de acessibilidade permitem que um aplicativo fornecer uma experiência apropriada para os usuários de tecnologia assistencial.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="4ca1a-105">Iniciando com o .NET Framework 4.7.1, o .NET Framework inclui um grande número de aprimoramentos de acessibilidade que permitem aos desenvolvedores criar aplicativos acessíveis.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="4ca1a-106">Os novos recursos de acessibilidade são habilitados por padrão para aplicativos voltados para o .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="4ca1a-107">Além disso, aplicativos que uma versão anterior do .NET Framework de destino, mas estão em execução no .NET Framework 4.7.1 ou posterior podem optar por comportamentos de acessibilidade herdado (e, portanto, escolha os aprimoramentos de acessibilidade no .NET Framework 4.7.1) por adicionando a seguinte opção para o [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento o [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) seção do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="4ca1a-108">Da mesma forma, aplicativos destinados a versões do .NET Framework a partir 4.7.1 podem desabilitar os recursos de acessibilidade, adicionando a seguinte opção para o [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento o [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) seção do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="4ca1a-109">O que há de novo no acessibilidade no .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="4ca1a-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="4ca1a-110">O .NET Framework 4.7.1 inclui novos recursos de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="4ca1a-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="4ca1a-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="4ca1a-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ca1a-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="4ca1a-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="4ca1a-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="4ca1a-114">**Aprimoramentos de leitor de tela**</span><span class="sxs-lookup"><span data-stu-id="4ca1a-114">**Screen reader improvements**</span></span>

<span data-ttu-id="4ca1a-115">Se os aprimoramentos de acessibilidade estão habilitados, o .NET Framework 4.7.1 inclui os seguintes aprimoramentos que afetam os leitores de tela:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="4ca1a-116">No .NET Framework 4.7 e versões anteriores, <xref:System.Windows.Controls.Expander> controles foram lançados por leitores de tela como botões.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="4ca1a-117">Iniciando com o .NET Framework 4.7.1, eles são corretamente anunciados como grupos expansível recolhível.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="4ca1a-118">No .NET Framework 4.7 e versões anteriores, <xref:System.Windows.Controls.DataGridCell> controles foram lançados por leitores de tela como "custom".</span><span class="sxs-lookup"><span data-stu-id="4ca1a-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="4ca1a-119">Iniciando com o .NET Framework 4.7.1, eles agora estão corretamente anunciados como célula de grade de dados (localizada).</span><span class="sxs-lookup"><span data-stu-id="4ca1a-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="4ca1a-120">Iniciando com o .NET Framework 4.7.1, leitores de tela anunciam o nome de um editável <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="4ca1a-121">No .NET Framework 4.7 e versões anteriores, <xref:System.Windows.Controls.PasswordBox> controles foram anunciados como "nenhum item no modo de exibição" ou tinha um comportamento incorreto caso contrário.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="4ca1a-122">Esse problema é corrigido, iniciando com o .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="4ca1a-123">**Suporte de UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="4ca1a-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="4ca1a-124">Leitores de tela, como as pessoas de ajuda o Narrator ler o conteúdo de interface do usuário de um aplicativo, normalmente pela saída de texto em fala do conteúdo da interface do usuário que tem o foco.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="4ca1a-125">No entanto, se um elemento de interface do usuário for alterado e não tem o foco, o usuário não pode ser notificado e poderá perder informações importantes.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="4ca1a-126">Regiões ao vivo focalizam a solução do problema.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="4ca1a-127">Um desenvolvedor pode usá-los para informar o leitor de tela ou qualquer outro cliente de automação da IU que foi feita uma alteração importante de um elemento de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="4ca1a-128">O leitor de tela, em seguida, pode decidir como e quando para informar ao usuário dessa alteração.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="4ca1a-129">Para dar suporte ao vivo regiões, as seguintes APIs foram adicionadas para WPF:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="4ca1a-130">O <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> campos que identificam o **LiveSetting** propriedade e o **LiveRegionChanged** eventos.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="4ca1a-131">Eles podem ser definidos usando XAML.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="4ca1a-132">O **AutomationProperties.LiveSetting** anexado a propriedade, que informa o leitor de tela da importância da alteração da interface do usuário para o usuário.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="4ca1a-133">O <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> propriedade que identifica o **AutomationProperties.LiveSetting** propriedade anexada.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="4ca1a-134">O <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> método, que pode ser substituído para fornecer uma **LiveSetting** valor.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="4ca1a-135">O <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> métodos, que obtém e definir um **LiveSetting** valor.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="4ca1a-136">O <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeração, que define os seguintes possíveis **LiveSetting** valores:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="4ca1a-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4ca1a-138">O elemento não enviar notificações se o conteúdo da região de dados ao vivo foi alterado.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="4ca1a-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4ca1a-140">O elemento enviará notificações não interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="4ca1a-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4ca1a-142">O elemento enviará notificações interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="4ca1a-143">Você pode criar um LiveRegion definindo o **AutomationProperties.LiveSetting** propriedade no elemento de interesse, como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="4ca1a-144">Quando os dados na região dinâmica são alterados e você precisa informar um leitor de tela, você explicitamente gerar um evento, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="4ca1a-145">**Alto contraste**</span><span class="sxs-lookup"><span data-stu-id="4ca1a-145">**High contrast**</span></span>

<span data-ttu-id="4ca1a-146">Iniciando com o .NET Framework 4.7.1, em alto contraste foram feitas melhorias para vários controles do WPF.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="4ca1a-147">Agora são visíveis quando a <xref:System.Windows.SystemParameters.HighContrast%2A> tema está definido.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="4ca1a-148">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-148">These include:</span></span>

- <span data-ttu-id="4ca1a-149">Controle <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="4ca1a-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="4ca1a-150">O foco visual para o <xref:System.Windows.Controls.Expander> controle agora está visível.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="4ca1a-151">Os visuais de teclado para <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, e <xref:System.Windows.Controls.RadioButton> controles também são visíveis.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="4ca1a-152">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-152">For example:</span></span>

    <span data-ttu-id="4ca1a-153">Antes:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-153">Before:</span></span> 
    
    ![Controle expansor com foco antes de aprimoramentos de acessibilidade](media/expander-before.png)

    <span data-ttu-id="4ca1a-155">Depois:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-155">After:</span></span> 

    ![Controle expansor com foco após aprimoramentos de acessibilidade](media/expander-after.png)

- <span data-ttu-id="4ca1a-157"><xref:System.Windows.Controls.CheckBox>e <xref:System.Windows.Controls.RadioButton> controles</span><span class="sxs-lookup"><span data-stu-id="4ca1a-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="4ca1a-158">O texto a <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton> controles agora é mais fácil ver quando selecionados em temas de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="4ca1a-159">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-159">For example:</span></span>

    <span data-ttu-id="4ca1a-160">Antes:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-160">Before:</span></span> 

    ![Botão de opção de alto contraste com foco antes de aprimoramentos de acessibilidade](media/radio-button-before.png)
    
    <span data-ttu-id="4ca1a-162">Depois:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-162">After:</span></span> 

    ![Botão de opção de alto contraste com foco após aprimoramentos de acessibilidade](media/radio-button-after.png)

- <span data-ttu-id="4ca1a-164">Controle <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="4ca1a-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="4ca1a-165">Iniciando com o .NET Framework 4.7.1, a borda de um desativado <xref:System.Windows.Controls.ComboBox> controle é a mesma cor do texto desabilitado.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="4ca1a-166">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-166">For example:</span></span>
    
    <span data-ttu-id="4ca1a-167">Antes:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-167">Before:</span></span> 

     ![Caixa de combinação desabilitado borda e o texto antes de aprimoramentos de acessibilidade](media/combo-disabled-before.png)

    <span data-ttu-id="4ca1a-169">Depois:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-169">After:</span></span>   

     ![Caixa de combinação desabilitado borda e o texto depois de aprimoramentos de acessibilidade](media/combo-disabled-after.png)

    <span data-ttu-id="4ca1a-171">Além disso, botões desabilitados e voltada para usam a cor de tema correto.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="4ca1a-172">Antes:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-172">Before:</span></span>

    ![Cores de tema do botão antes de aprimoramentos de acessibilidade](media/button-themes-before.png) 
    
    <span data-ttu-id="4ca1a-174">Depois:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-174">After:</span></span> 

    ![Cores de tema do botão após aprimoramentos de acessibilidade](media/button-themes-after.png) 

    <span data-ttu-id="4ca1a-176">Por fim, no .NET Framework 4.7 e versões anteriores, definindo um <xref:System.Windows.Controls.ComboBox> estilo de controle para `Toolbar.ComboBoxStyleKey` causou a seta suspensa invisível.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="4ca1a-177">Esse problema é corrigido, iniciando com o .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="4ca1a-178">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-178">For example:</span></span>

    <span data-ttu-id="4ca1a-179">Antes:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-179">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey antes de aprimoramentos de acessibilidade](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="4ca1a-181">Depois:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-181">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey depois de aprimoramentos de acessibilidade](media/comboboxstylekey-after.png) 

- <span data-ttu-id="4ca1a-183">Controle <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="4ca1a-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="4ca1a-184">Iniciando com o .NET Framework 4.7.1, na seta de indicador de classificação no <xref:System.Windows.Controls.DataGrid> controla agora usa corrigir cores do tema.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="4ca1a-185">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-185">For example:</span></span>

    <span data-ttu-id="4ca1a-186">Antes:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-186">Before:</span></span> 

    ![Seta de indicador de classificação antes de aprimoramentos de acessibilidade](media/sort-indicator-before.png) 
    
    <span data-ttu-id="4ca1a-188">Depois:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-188">After:</span></span>   
 
    ![Seta de indicador de classificação depois de aprimoramentos de acessibilidade](media/sort-indicator-after.png) 
    
    <span data-ttu-id="4ca1a-190">Além disso, no .NET Framework 4.7 e versões anteriores, o estilo de link padrão alterada para uma cor incorretova no mouse nos modos de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="4ca1a-191">Isso é resolvido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="4ca1a-192">Da mesma forma, <xref:System.Windows.Controls.DataGrid> caixa de seleção colunas usa as cores esperadas para comentários de foco do teclado iniciando com o .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="4ca1a-193">Antes:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-193">Before:</span></span> 

    ![Estilo de link do DataGrid padrão antes de aprimoramentos de acessibilidade](media/default-link-style-before.png) 
 
    <span data-ttu-id="4ca1a-195">Depois:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-195">After:</span></span>    
  
    ![Estilo de link padrão DataGrid depois de aprimoramentos de acessibilidade](media/default-link-style-after.png)  

<span data-ttu-id="4ca1a-197">Para obter mais informações sobre aprimoramentos de acessibilidade do WPF no .NET Framework 4.7.1, consulte [aprimoramentos de acessibilidade no WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="4ca1a-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="4ca1a-198">Aprimoramentos de acessibilidade do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ca1a-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="4ca1a-199">No .NET Framework 4.7.1, o Windows Forms (WinForms) inclui alterações de acessibilidade nas seguintes áreas.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="4ca1a-200">**Vídeo aprimorado no modo de alto contraste**</span><span class="sxs-lookup"><span data-stu-id="4ca1a-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="4ca1a-201">Iniciando com o .NET Framework 4.7.1, vários controles WinForms oferecem maior processamento nos modos de alto contraste será disponíveis no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="4ca1a-202">Windows 10 foi alterado os valores para algumas cores do sistema de alto contraste e formulários do Windows é baseado na estrutura do Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="4ca1a-203">Para obter a melhor experiência, execute a versão mais recente do Windows e aceitar as alterações mais recentes do sistema operacional, adicionando que um arquivo App. manifest em um aplicativo de teste e cancelar os comentários do Windows 10 com suporte de linha de sistema operacional para que ele tenha o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="4ca1a-204">Alguns exemplos de alterações de alto contraste incluem:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="4ca1a-205">Marcas de seleção no <xref:System.Windows.Forms.MenuStrip> itens são mais fáceis de ler.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="4ca1a-206">Quando selecionado, desabilitado <xref:System.Windows.Forms.MenuStrip> itens são mais fáceis de ler.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="4ca1a-207">Texto em um selecionado <xref:System.Windows.Forms.Button> controlar contrasta com a cor da seleção.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="4ca1a-208">Texto desabilitado é mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-208">Disabled text is easier to read.</span></span> <span data-ttu-id="4ca1a-209">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-209">For example:</span></span>

    <span data-ttu-id="4ca1a-210">Antes:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-210">Before:</span></span>

    ![Texto desabilitado antes de aprimoramentos de acessibilidade](media/wf-disabled-before.png) 

    <span data-ttu-id="4ca1a-212">Depois:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-212">After:</span></span>

    ![Texto desabilitado depois aprimoramentos de acessibilidade](media/wf-disabled-after.png) 

- <span data-ttu-id="4ca1a-214">Melhorias de alto contraste na caixa de diálogo exceção de Thread.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="4ca1a-215">**Suporte aprimorado do Narrator**</span><span class="sxs-lookup"><span data-stu-id="4ca1a-215">**Improved Narrator support**</span></span>

<span data-ttu-id="4ca1a-216">Windows Forms no .NET Framework 4.7.1 inclui os seguintes aprimoramentos de acessibilidade para o Narrator:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="4ca1a-217">O <xref:System.Windows.Forms.MonthCalendar> controle pode ser acessado pelo Narrator, bem como por outras ferramentas de automação de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="4ca1a-218">O <xref:System.Windows.Forms.CheckedListBox> controle notifica o Narrator quando o estado de seleção do item mudou para o usuário será notificado de que eles alterou o valor de um item de lista.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="4ca1a-219">O <xref:System.Windows.Forms.DataGridViewCell> controle relata o status de somente leitura correto para o Narrator.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="4ca1a-220">O Narrator poderá ler desabilitado <xref:System.Windows.Forms.ToolStripMenuItem> texto, enquanto que anteriormente ele seria ignorar itens de menu desativado.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="4ca1a-221">**Suporte aprimorado para padrões de acessibilidade de automação da IU**</span><span class="sxs-lookup"><span data-stu-id="4ca1a-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="4ca1a-222">Iniciando com o .NET Framework 4.7.1, os desenvolvedores de ferramentas de tecnologia de acessibilidade podem aproveitar padrões comuns de acessibilidade de API e as propriedades de vários controles WinForms.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="4ca1a-223">Esses aprimoramentos de acessibilidade incluem:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="4ca1a-224">O <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ToolStripSplitButton> agora oferecem suporte a [padrão Expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4ca1a-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="4ca1a-225">O <xref:System.Windows.Forms.DataGridViewCheckBoxCell> agora oferece suporte a [padrão toggle](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4ca1a-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="4ca1a-226">O <xref:System.Windows.Forms.ToolStripItem> controle oferece suporte a <xref:System.Windows.Automation.AutomationElement.Name> propriedade e o [padrão Expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4ca1a-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="4ca1a-227">O <xref:System.Windows.Forms.NumericUpDown> e <xref:System.Windows.Forms.DomainUpDown> controla o suporte a <xref:System.Windows.Automation.automationElement.Name> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.automationElement.Name> property.</span></span>

<span data-ttu-id="4ca1a-228">**Propriedade melhor experiência de navegador**</span><span class="sxs-lookup"><span data-stu-id="4ca1a-228">**Improved property browser experience**</span></span>

<span data-ttu-id="4ca1a-229">Iniciando com o .NET Framework 4.7.1, formulários do Windows incluem:</span><span class="sxs-lookup"><span data-stu-id="4ca1a-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="4ca1a-230">Navegação de teclado melhor por meio de várias janelas de seleção de lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="4ca1a-231">Uma redução de paradas de tabulação desnecessários.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="4ca1a-232">Melhor relatório de tipos de controle.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-232">Better reporting of control types.</span></span>
- <span data-ttu-id="4ca1a-233">O narrator melhor comportamento.</span><span class="sxs-lookup"><span data-stu-id="4ca1a-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="4ca1a-234">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ca1a-234">See Also</span></span>
[<span data-ttu-id="4ca1a-235">O que há de novo no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4ca1a-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 
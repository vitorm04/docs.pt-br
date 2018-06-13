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
ms.locfileid: "33509210"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="bfebb-102">Novidades na acessibilidade do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bfebb-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="bfebb-103">O .NET Framework pretende tornar os aplicativos mais acessíveis para os usuários.</span><span class="sxs-lookup"><span data-stu-id="bfebb-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="bfebb-104">As funcionalidades de acessibilidade permitem que um aplicativo forneça uma experiência apropriada para os usuários da Tecnologia Adaptativa.</span><span class="sxs-lookup"><span data-stu-id="bfebb-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="bfebb-105">A partir do .NET Framework 4.7.1, o .NET Framework inclui diversas melhorias de acessibilidade que permitem aos desenvolvedores criar aplicativos acessíveis.</span><span class="sxs-lookup"><span data-stu-id="bfebb-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

## <a name="accessibility-switches"></a><span data-ttu-id="bfebb-106">Opções de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="bfebb-106">Accessibility switches</span></span>

<span data-ttu-id="bfebb-107">Configure seu aplicativo para aceitar os recursos de acessibilidade se ele for direcionado ao .NET Framework 4.7 ou a uma versão anterior, mas estiver em execução no .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="bfebb-107">You can configure your app to opt into accessibility features if it targets the .NET Framework 4.7 or an earlier version but is running on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="bfebb-108">Além disso, configure seu aplicativo para usar recursos herdados (e não aproveitar os recursos de acessibilidade) se ele for direcionado ao .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="bfebb-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="bfebb-109">Cada versão do .NET Framework que inclui recursos de acessibilidade tem uma opção de acessibilidade específica à versão, que você adiciona ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bfebb-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="bfebb-110">Estas são as opções compatíveis:</span><span class="sxs-lookup"><span data-stu-id="bfebb-110">The following are the supported switches:</span></span>

|<span data-ttu-id="bfebb-111">Versão</span><span class="sxs-lookup"><span data-stu-id="bfebb-111">Version</span></span>|<span data-ttu-id="bfebb-112">Alternar</span><span class="sxs-lookup"><span data-stu-id="bfebb-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="bfebb-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="bfebb-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="bfebb-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="bfebb-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="bfebb-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="bfebb-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="bfebb-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="bfebb-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="bfebb-117">Aproveitando as vantagens das melhorias de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="bfebb-117">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="bfebb-118">As novas funcionalidades de acessibilidade são habilitadas por padrão para os aplicativos direcionados a o .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="bfebb-118">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="bfebb-119">Além disso, os aplicativos direcionados a uma versão anterior do .NET Framework, mas que estão em execução no .NET Framework 4.7.1 ou posterior, podem recusar os comportamentos de acessibilidade herdados (e, portanto, aproveitar as melhorias de acessibilidade) adicionando opções ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo e definindo seu valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="bfebb-119">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="bfebb-120">O seguinte exemplo mostra como aceitar as melhorias de acessibilidade introduzidas no .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="bfebb-120">The following shows how to opt in to accessibility enhancements introduced in the .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="bfebb-121">Se você optar por aceitar os recursos de acessibilidade em uma versão posterior do .NET Framework, deverá também aceitar explicitamente os recursos de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfebb-121">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="bfebb-122">A configuração do aplicativo para aproveitar as melhorias de acessibilidade do .NET Framework 4.7.1 e 4.7.2 exige o seguinte elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="bfebb-122">Configuring your app to take advantage of accessibility improvements in both the .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="bfebb-123">Restaurando o comportamento herdado</span><span class="sxs-lookup"><span data-stu-id="bfebb-123">Restoring legacy behavior</span></span>

<span data-ttu-id="bfebb-124">Os aplicativos direcionados a versões do .NET Framework a começar pela 4.7.1 podem desabilitar os recursos de acessibilidade adicionando opções ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo e definindo seu valor como `true`.</span><span class="sxs-lookup"><span data-stu-id="bfebb-124">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="bfebb-125">Por exemplo, a seguinte configuração recusa os recursos de acessibilidade introduzidos no .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="bfebb-125">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a><span data-ttu-id="bfebb-126">Novidades na acessibilidade do .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="bfebb-126">What's new in accessibility in the .NET Framework 4.7.2</span></span>

<span data-ttu-id="bfebb-127">O .NET Framework 4.7.2 inclui novos recursos de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="bfebb-127">The .NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="bfebb-128">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bfebb-128">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="bfebb-129">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bfebb-129">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a><span data-ttu-id="bfebb-130">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bfebb-130">Windows Forms</span></span>

<span data-ttu-id="bfebb-131">**Cores definidas pelo sistema operacional em temas de Alto Contraste**</span><span class="sxs-lookup"><span data-stu-id="bfebb-131">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="bfebb-132">Começando no .NET Framework 4.7.2, o Windows Forms usa cores definidas pelo sistema operacional em temas de Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="bfebb-132">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="bfebb-133">Isso afeta os seguintes controles:</span><span class="sxs-lookup"><span data-stu-id="bfebb-133">This affects the following controls:</span></span>

- <span data-ttu-id="bfebb-134">A seta suspensa do controle <xref:System.Windows.Forms.ToolStripDropDownButton>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-134">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="bfebb-135">Os controles <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> e <xref:System.Windows.Forms.CheckBox> com <xref:System.Windows.Forms.ButtonBase.FlatStyle> definido como <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> ou <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-135">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bfebb-136">Anteriormente, as cores de texto e da tela de fundo selecionadas não eram contrastantes e eram difíceis de serem lidas.</span><span class="sxs-lookup"><span data-stu-id="bfebb-136">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="bfebb-137">Os controles contidos em uma <xref:System.Windows.Forms.GroupBox> que tem sua propriedade <xref:System.Windows.Forms.Control.Enabled> definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="bfebb-137">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>
 
- <span data-ttu-id="bfebb-138">Os controles <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox> e <xref:System.Windows.Forms.ToolStripDropDownButton>, que têm uma taxa maior de contraste de luminosidade no Modo de Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="bfebb-138">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="bfebb-139">A propriedade <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> do <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-139">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="bfebb-140">**Melhorias do Narrador**</span><span class="sxs-lookup"><span data-stu-id="bfebb-140">**Narrator improvements**</span></span>

<span data-ttu-id="bfebb-141">Começando no .NET Framework 4.7.2, o suporte ao Narrador é aprimorado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="bfebb-141">Starting with the .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="bfebb-142">Ele anuncia o valor da propriedade <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> quando anuncia o texto de um <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-142">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span> 

- <span data-ttu-id="bfebb-143">Ele indica quando um <xref:System.Windows.Forms.ToolStripMenuItem> tem sua propriedade <xref:System.Windows.Forms.Control.Enabled> definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="bfebb-143">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="bfebb-144">Ele fornece comentários sobre o estado de uma caixa de seleção quando a propriedade <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="bfebb-144">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="bfebb-145">A ordem de foco do Modo de Verificação do Narrador é consistente com a ordem visual dos controles na janela de diálogo de download do ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="bfebb-145">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="bfebb-146">**Melhorias de DataGridView**</span><span class="sxs-lookup"><span data-stu-id="bfebb-146">**DataGridView improvements**</span></span>

<span data-ttu-id="bfebb-147">Começando no .NET Framework 4.7.2, o controle <xref:System.Windows.Forms.DataGridView> introduziu as seguintes melhorias de acessibilidade:</span><span class="sxs-lookup"><span data-stu-id="bfebb-147">Starting with the .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="bfebb-148">As linhas podem ser classificadas com o teclado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-148">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="bfebb-149">Um usuário pode usar a tecla F3 para classificar pela coluna atual.</span><span class="sxs-lookup"><span data-stu-id="bfebb-149">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="bfebb-150">Quando o <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> é definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, o cabeçalho da coluna muda de cor para indicar a coluna atual, à medida que o usuário pressiona Tab para percorrer as células na linha atual.</span><span class="sxs-lookup"><span data-stu-id="bfebb-150">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="bfebb-151">A propriedade <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> de um <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> retorna o controle pai correto.</span><span class="sxs-lookup"><span data-stu-id="bfebb-151">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="bfebb-152">**Melhoria das indicações visuais**</span><span class="sxs-lookup"><span data-stu-id="bfebb-152">**Improved visual cues**</span></span>

- <span data-ttu-id="bfebb-153">Os controles <xref:System.Windows.Forms.RadioButton> e <xref:System.Windows.Forms.CheckBox> com uma propriedade <xref:System.Windows.Forms.ButtonBase.Text> vazia exibem um indicador de foco quando recebem o foco.</span><span class="sxs-lookup"><span data-stu-id="bfebb-153">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="bfebb-154">**Melhoria no suporte à grade de propriedade**</span><span class="sxs-lookup"><span data-stu-id="bfebb-154">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="bfebb-155">Os elementos filhos do controle <xref:System.Windows.Forms.PropertyGrid> agora retornam um `true` para a propriedade <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> somente quando um elemento PropertyGrid está habilitado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-155">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="bfebb-156">Os elementos filho do controle <xref:System.Windows.Forms.PropertyGrid> retornam um `false` para a propriedade <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> somente quando um elemento PropertyGrid pode ser alterado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="bfebb-156">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="bfebb-157">**Melhoria na navegação por teclado**</span><span class="sxs-lookup"><span data-stu-id="bfebb-157">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="bfebb-158">O controle <xref:System.Windows.Forms.ToolStripButton> permite o foco quando contido em um <xref:System.Windows.Forms.ToolStripPanel> que tem a propriedade <xref:System.Windows.Forms.ToolStripPanel.TabStop> definida como `true`</span><span class="sxs-lookup"><span data-stu-id="bfebb-158">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="bfebb-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bfebb-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="bfebb-160">**Alterações nos controles CheckBox e RadioButton**</span><span class="sxs-lookup"><span data-stu-id="bfebb-160">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="bfebb-161">No .NET Framework 4.7.1 e nas versões anteriores, os controles <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> e <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> do WPF têm visuais de foco inconsistentes e, nos temas Clássico e de Alto Contraste, eles têm visuais de foco incorretos.</span><span class="sxs-lookup"><span data-stu-id="bfebb-161">In the .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="bfebb-162">Esses problemas ocorrem quando os controles não têm nenhum conjunto de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bfebb-162">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="bfebb-163">Isso pode dificultar a transição entre os temas e deixar o visual de foco confuso.</span><span class="sxs-lookup"><span data-stu-id="bfebb-163">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="bfebb-164">No .NET Framework 4.7.2, agora esses visuais são mais consistentes entre os temas e mais facilmente visíveis nos temas Clássico e de Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="bfebb-164">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="bfebb-165">**Controles do WinForms hospedados em um aplicativo WPF**</span><span class="sxs-lookup"><span data-stu-id="bfebb-165">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="bfebb-166">Para controles do WinForms hospedados em um aplicativo do WPF no .NET Framework 4.7.1 e versões anteriores, os usuários não podem sair da guia da camada do WinForms se o primeiro ou o último controle da camada é o controle <xref:System.Windows.Forms.Integration.ElementHost> do WPF.</span><span class="sxs-lookup"><span data-stu-id="bfebb-166">For WinForms control hosted in a WPF application in the .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="bfebb-167">No .NET Framework 4.7.2, os usuários agora podem sair da guia da camada do WinForms.</span><span class="sxs-lookup"><span data-stu-id="bfebb-167">In the .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="bfebb-168">No entanto, os aplicativos automatizados que se baseiam em foco e que nunca são escapados da camada do WinForms podem deixar de funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-168">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="bfebb-169">Novidades na acessibilidade do .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="bfebb-169">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="bfebb-170">O .NET Framework 4.7.1 inclui novas funcionalidades de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="bfebb-170">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="bfebb-171">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bfebb-171">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="bfebb-172">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bfebb-172">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="bfebb-173">Controles da Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bfebb-173">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="bfebb-174">Ferramentas do SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="bfebb-174">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="bfebb-175">Designer de Fluxo de Trabalho do WF (Windows Workflow Foundation)</span><span class="sxs-lookup"><span data-stu-id="bfebb-175">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="bfebb-176">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="bfebb-176">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="bfebb-177">**Melhorias do leitor de tela**</span><span class="sxs-lookup"><span data-stu-id="bfebb-177">**Screen reader improvements**</span></span>

<span data-ttu-id="bfebb-178">Se as melhorias de acessibilidade estiverem habilitadas, o .NET Framework 4.7.1 incluirá as seguintes melhorias que afetam os leitores de tela:</span><span class="sxs-lookup"><span data-stu-id="bfebb-178">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="bfebb-179">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.Expander> foram divulgados pelos leitores de tela como botões.</span><span class="sxs-lookup"><span data-stu-id="bfebb-179">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="bfebb-180">A partir do .NET Framework 4.7.1, eles são corretamente divulgados como grupos expansíveis/recolhíveis.</span><span class="sxs-lookup"><span data-stu-id="bfebb-180">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="bfebb-181">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.DataGridCell> foram divulgados pelos leitores de tela como “personalizados”.</span><span class="sxs-lookup"><span data-stu-id="bfebb-181">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="bfebb-182">A partir do .NET Framework 4.7.1, agora eles são corretamente divulgados como célula de grade de dados (localizada).</span><span class="sxs-lookup"><span data-stu-id="bfebb-182">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="bfebb-183">A partir do .NET Framework 4.7.1, os leitores de tela divulgam o nome de uma <xref:System.Windows.Controls.ComboBox> editável.</span><span class="sxs-lookup"><span data-stu-id="bfebb-183">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="bfebb-184">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.PasswordBox> eram divulgados como “nenhum item em exibição” ou, de outro modo, apresentavam um comportamento incorreto.</span><span class="sxs-lookup"><span data-stu-id="bfebb-184">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="bfebb-185">Esse problema é corrigido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="bfebb-185">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>

<span data-ttu-id="bfebb-186">**Suporte a UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="bfebb-186">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="bfebb-187">Leitores de tela, como o Narrador, ajudam as pessoas a ler o conteúdo da interface do usuário de um aplicativo, normalmente, pela saída de conversão de texto em fala do conteúdo da interface do usuário que tem o foco.</span><span class="sxs-lookup"><span data-stu-id="bfebb-187">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="bfebb-188">No entanto, se um elemento da interface do usuário for alterado e não tiver o foco, o usuário poderá não ser notificado e perder informações importantes.</span><span class="sxs-lookup"><span data-stu-id="bfebb-188">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="bfebb-189">As regiões dinâmicas pretendem resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="bfebb-189">Live regions aim at solving this problem.</span></span> <span data-ttu-id="bfebb-190">Um desenvolvedor pode usá-las para informar o leitor de tela ou qualquer outro cliente de UIAutomation de que foi feita uma alteração importante em um elemento da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="bfebb-190">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="bfebb-191">Em seguida, o leitor de tela pode decidir como e quando informar o usuário dessa alteração.</span><span class="sxs-lookup"><span data-stu-id="bfebb-191">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="bfebb-192">Para dar suporte a regiões dinâmicas, as seguintes APIs foram adicionadas ao WPF:</span><span class="sxs-lookup"><span data-stu-id="bfebb-192">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="bfebb-193">Os campos <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, que identificam a propriedade **LiveSetting** e o evento **LiveRegionChanged**.</span><span class="sxs-lookup"><span data-stu-id="bfebb-193">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="bfebb-194">Eles podem ser definidos com XAML.</span><span class="sxs-lookup"><span data-stu-id="bfebb-194">They can be set by using XAML.</span></span>

- <span data-ttu-id="bfebb-195">A propriedade anexada **AutomationProperties.LiveSetting**, que informa o leitor de tela da importância da alteração da interface do usuário para o usuário.</span><span class="sxs-lookup"><span data-stu-id="bfebb-195">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="bfebb-196">A propriedade <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, que identifica a propriedade anexada **AutomationProperties.LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="bfebb-196">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="bfebb-197">O método <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, que pode ser substituído para fornecer um valor de **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="bfebb-197">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="bfebb-198">Os métodos <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, que obtêm e definem um valor de **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="bfebb-198">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="bfebb-199">A enumeração <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, que define os seguintes possíveis valores de **LiveSetting**:</span><span class="sxs-lookup"><span data-stu-id="bfebb-199">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="bfebb-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bfebb-201">O elemento não envia notificações se o conteúdo da região dinâmica foi alterado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-201">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="bfebb-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bfebb-203">O elemento enviará notificações não interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-203">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="bfebb-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bfebb-205">O elemento enviará notificações interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-205">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="bfebb-206">Crie uma LiveRegion configurar a propriedade **AutomationProperties.LiveSetting** no elemento de interesse, conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="bfebb-206">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="bfebb-207">Quando os dados da região dinâmica forem alterados e você precisar informar um leitor de tela, acione um evento explicitamente, conforme mostrado na amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="bfebb-207">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="bfebb-208">**Alto contraste**</span><span class="sxs-lookup"><span data-stu-id="bfebb-208">**High contrast**</span></span>

<span data-ttu-id="bfebb-209">A partir do .NET Framework 4.7.1, foram feitas melhorias de alto contraste em vários controles do WPF.</span><span class="sxs-lookup"><span data-stu-id="bfebb-209">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="bfebb-210">Agora eles estão visíveis quando o tema <xref:System.Windows.SystemParameters.HighContrast%2A> é definido.</span><span class="sxs-lookup"><span data-stu-id="bfebb-210">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="bfebb-211">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="bfebb-211">These include:</span></span>

- <span data-ttu-id="bfebb-212">Controle <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="bfebb-212"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="bfebb-213">O visual de foco do controle <xref:System.Windows.Controls.Expander> agora está visível.</span><span class="sxs-lookup"><span data-stu-id="bfebb-213">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="bfebb-214">Os visuais de teclado dos controles <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.RadioButton> também estão visíveis.</span><span class="sxs-lookup"><span data-stu-id="bfebb-214">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="bfebb-215">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bfebb-215">For example:</span></span>

    <span data-ttu-id="bfebb-216">Antes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-216">Before:</span></span> 
    
    ![Controle expansor com foco antes das melhorias de acessibilidade](media/expander-before.png)

    <span data-ttu-id="bfebb-218">Depois:</span><span class="sxs-lookup"><span data-stu-id="bfebb-218">After:</span></span> 

    ![Controle expansor com foco após as melhorias de acessibilidade](media/expander-after.png)

- <span data-ttu-id="bfebb-220">Controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton></span><span class="sxs-lookup"><span data-stu-id="bfebb-220"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="bfebb-221">O texto nos controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton> agora é de visualização mais fácil quando selecionado em temas de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="bfebb-221">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="bfebb-222">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bfebb-222">For example:</span></span>

    <span data-ttu-id="bfebb-223">Antes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-223">Before:</span></span> 

    ![Botão de opção de alto contraste com foco antes das melhorias de acessibilidade](media/radio-button-before.png)
    
    <span data-ttu-id="bfebb-225">Depois:</span><span class="sxs-lookup"><span data-stu-id="bfebb-225">After:</span></span> 

    ![Botão de opção de alto contraste com foco após as melhorias de acessibilidade](media/radio-button-after.png)

- <span data-ttu-id="bfebb-227">Controle <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="bfebb-227"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="bfebb-228">A partir do .NET Framework 4.7.1, a borda de um controle <xref:System.Windows.Controls.ComboBox> desabilitado é da mesma cor do texto desabilitado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-228">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="bfebb-229">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bfebb-229">For example:</span></span>
    
    <span data-ttu-id="bfebb-230">Antes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-230">Before:</span></span> 

     ![Borda e texto desabilitados da ComboBox antes das melhorias de acessibilidade](media/combo-disabled-before.png)

    <span data-ttu-id="bfebb-232">Depois:</span><span class="sxs-lookup"><span data-stu-id="bfebb-232">After:</span></span>   

     ![Borda e texto desabilitados da ComboBox após as melhorias de acessibilidade](media/combo-disabled-after.png)

    <span data-ttu-id="bfebb-234">Além disso, os botões desabilitados e com foco usam a cor de tema correta.</span><span class="sxs-lookup"><span data-stu-id="bfebb-234">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="bfebb-235">Antes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-235">Before:</span></span>

    ![Cores de tema do botão antes das melhorias de acessibilidade](media/button-themes-before.png) 
    
    <span data-ttu-id="bfebb-237">Depois:</span><span class="sxs-lookup"><span data-stu-id="bfebb-237">After:</span></span> 

    ![Cores de tema do botão após as melhorias de acessibilidade](media/button-themes-after.png) 

    <span data-ttu-id="bfebb-239">Por fim, no .NET Framework 4.7 e em versões anteriores, a configuração do estilo de um controle <xref:System.Windows.Controls.ComboBox> como `Toolbar.ComboBoxStyleKey` fazia com que a seta suspensa ficasse invisível.</span><span class="sxs-lookup"><span data-stu-id="bfebb-239">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="bfebb-240">Esse problema é corrigido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="bfebb-240">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="bfebb-241">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bfebb-241">For example:</span></span>

    <span data-ttu-id="bfebb-242">Antes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-242">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey antes das melhorias de acessibilidade](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="bfebb-244">Depois:</span><span class="sxs-lookup"><span data-stu-id="bfebb-244">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey após as melhorias de acessibilidade](media/comboboxstylekey-after.png) 

- <span data-ttu-id="bfebb-246">Controle <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="bfebb-246"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="bfebb-247">A partir do .NET Framework 4.7.1, a seta do indicador de classificação nos controles <xref:System.Windows.Controls.DataGrid> agora usa as cores de tema corretas.</span><span class="sxs-lookup"><span data-stu-id="bfebb-247">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="bfebb-248">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bfebb-248">For example:</span></span>

    <span data-ttu-id="bfebb-249">Antes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-249">Before:</span></span> 

    ![Seta do indicador de classificação antes das melhorias de acessibilidade](media/sort-indicator-before.png) 
    
    <span data-ttu-id="bfebb-251">Depois:</span><span class="sxs-lookup"><span data-stu-id="bfebb-251">After:</span></span>   
 
    ![Seta do indicador de classificação após as melhorias de acessibilidade](media/sort-indicator-after.png) 
    
    <span data-ttu-id="bfebb-253">Além disso, no .NET Framework 4.7 e em versões anteriores, o estilo de link padrão era alterado para uma cor incorreta ao passar o mouse nos modos de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="bfebb-253">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="bfebb-254">Isso é resolvido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="bfebb-254">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="bfebb-255">Da mesma forma, as colunas da caixa de seleção <xref:System.Windows.Controls.DataGrid> usam as cores esperadas para os comentários do foco de teclado a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="bfebb-255">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="bfebb-256">Antes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-256">Before:</span></span> 

    ![Estilo de link padrão de DataGrid antes das melhorias de acessibilidade](media/default-link-style-before.png) 
 
    <span data-ttu-id="bfebb-258">Depois:</span><span class="sxs-lookup"><span data-stu-id="bfebb-258">After:</span></span>    
  
    ![Estilo de link padrão de DataGrid após as melhorias de acessibilidade](media/default-link-style-after.png)  

<span data-ttu-id="bfebb-260">Para obter mais informações sobre as melhorias de acessibilidade do WPF no .NET Framework 4.7.1, consulte [Melhorias de acessibilidade no WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="bfebb-260">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="bfebb-261">Melhorias de acessibilidade do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bfebb-261">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="bfebb-262">No .NET Framework 4.7.1, o WinForms (Windows Forms) inclui alterações de acessibilidade nas áreas a seguir.</span><span class="sxs-lookup"><span data-stu-id="bfebb-262">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="bfebb-263">**Vídeo aprimorado no modo de Alto Contraste**</span><span class="sxs-lookup"><span data-stu-id="bfebb-263">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="bfebb-264">A partir do .NET Framework 4.7.1, vários controles do WinForms oferecem uma melhor renderização nos modos de HighContrast disponíveis no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="bfebb-264">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="bfebb-265">O Windows 10 alterou os valores de algumas cores do sistema de alto contraste e o Windows Forms é baseado na estrutura Win32 do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="bfebb-265">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="bfebb-266">Para obter a melhor experiência, execute a última versão do Windows e aceite as últimas alterações do sistema operacional adicionando um arquivo app.manifest a um aplicativo de teste e remova a marca de comentário da linha de sistema operacional com suporte do Windows 10 para que ela seja semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="bfebb-266">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="bfebb-267">Alguns exemplos de alterações de alto contraste incluem:</span><span class="sxs-lookup"><span data-stu-id="bfebb-267">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="bfebb-268">Marcas de seleção em itens <xref:System.Windows.Forms.MenuStrip> são mais fáceis de serem exibidas.</span><span class="sxs-lookup"><span data-stu-id="bfebb-268">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="bfebb-269">Quando selecionados, os itens <xref:System.Windows.Forms.MenuStrip> desabilitados são mais fáceis de serem exibidos.</span><span class="sxs-lookup"><span data-stu-id="bfebb-269">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="bfebb-270">O texto em um controle <xref:System.Windows.Forms.Button> selecionado contrasta com a cor da seleção.</span><span class="sxs-lookup"><span data-stu-id="bfebb-270">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="bfebb-271">O texto desabilitado é mais fácil de ser lido.</span><span class="sxs-lookup"><span data-stu-id="bfebb-271">Disabled text is easier to read.</span></span> <span data-ttu-id="bfebb-272">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bfebb-272">For example:</span></span>

    <span data-ttu-id="bfebb-273">Antes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-273">Before:</span></span>

    ![Texto desabilitado antes das melhorias de acessibilidade](media/wf-disabled-before.png) 

    <span data-ttu-id="bfebb-275">Depois:</span><span class="sxs-lookup"><span data-stu-id="bfebb-275">After:</span></span>

    ![Texto desabilitado após as melhorias de acessibilidade](media/wf-disabled-after.png) 

- <span data-ttu-id="bfebb-277">Melhorias de alto contraste na caixa de diálogo Exceção de Thread.</span><span class="sxs-lookup"><span data-stu-id="bfebb-277">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="bfebb-278">**Melhor suporte ao Narrador**</span><span class="sxs-lookup"><span data-stu-id="bfebb-278">**Improved Narrator support**</span></span>

<span data-ttu-id="bfebb-279">O Windows Forms no .NET Framework 4.7.1 inclui as seguintes melhorias de acessibilidade para o Narrador:</span><span class="sxs-lookup"><span data-stu-id="bfebb-279">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="bfebb-280">O controle <xref:System.Windows.Forms.MonthCalendar> pode ser acessado pelo Narrador, bem como por outras ferramentas de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="bfebb-280">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="bfebb-281">O controle <xref:System.Windows.Forms.CheckedListBox> notifica o Narrador quando o estado de seleção do item foi alterado, para que o usuário seja notificado de que ele alterou o valor de um item de lista.</span><span class="sxs-lookup"><span data-stu-id="bfebb-281">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="bfebb-282">O controle <xref:System.Windows.Forms.DataGridViewCell> relata o status somente leitura correto para o Narrador.</span><span class="sxs-lookup"><span data-stu-id="bfebb-282">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="bfebb-283">O Narrador agora pode ler o texto <xref:System.Windows.Forms.ToolStripMenuItem> desabilitado, enquanto, anteriormente, ele ignorava itens de menu desabilitados.</span><span class="sxs-lookup"><span data-stu-id="bfebb-283">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="bfebb-284">**Suporte aprimorado para padrões de acessibilidade de UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="bfebb-284">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="bfebb-285">A partir do .NET Framework 4.7.1, os desenvolvedores de ferramentas de tecnologia de acessibilidade podem utilizar padrões comuns de acessibilidade de API e as propriedades de vários controles WinForms.</span><span class="sxs-lookup"><span data-stu-id="bfebb-285">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="bfebb-286">Essas melhorias de acessibilidade incluem:</span><span class="sxs-lookup"><span data-stu-id="bfebb-286">These accessibility improvements include:</span></span>

- <span data-ttu-id="bfebb-287">O <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ToolStripSplitButton> agora dão suporte ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="bfebb-287">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="bfebb-288">O <xref:System.Windows.Forms.DataGridViewCheckBoxCell> agora dá suporte ao [padrão alternar](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="bfebb-288">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="bfebb-289">O controle <xref:System.Windows.Forms.ToolStripItem> dá suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> e ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="bfebb-289">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="bfebb-290">Os controles <xref:System.Windows.Forms.NumericUpDown> e <xref:System.Windows.Forms.DomainUpDown> dão suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-290">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="bfebb-291">**Melhor experiência do navegador de propriedades**</span><span class="sxs-lookup"><span data-stu-id="bfebb-291">**Improved property browser experience**</span></span>

<span data-ttu-id="bfebb-292">A partir do .NET Framework 4.7.1, o Windows Forms inclui:</span><span class="sxs-lookup"><span data-stu-id="bfebb-292">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="bfebb-293">Melhor navegação de teclado por meio das várias janelas de seleção suspensa.</span><span class="sxs-lookup"><span data-stu-id="bfebb-293">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="bfebb-294">Uma redução de paradas de tabulação desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="bfebb-294">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="bfebb-295">Melhor relatório de tipos de controle.</span><span class="sxs-lookup"><span data-stu-id="bfebb-295">Better reporting of control types.</span></span>
- <span data-ttu-id="bfebb-296">Melhor comportamento do Narrador.</span><span class="sxs-lookup"><span data-stu-id="bfebb-296">Improved narrator behavior.</span></span>
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a><span data-ttu-id="bfebb-297">Controles da Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bfebb-297">ASP.NET web controls</span></span>

<span data-ttu-id="bfebb-298">Começando no .NET Framework 4.7.1 e no Visual Studio 2017 15.3, o ASP.NET melhorará o funcionamento dos controles da Web do ASP.NET com a tecnologia de acessibilidade no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bfebb-298">Starting with the .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="bfebb-299">As alterações incluem as seguintes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-299">Changes include the following:</span></span>

- <span data-ttu-id="bfebb-300">Alterações para implementar padrões de acessibilidade de interface do usuário ausentes em controles como a caixa de diálogo **Adicionar Campo** no assistente de **Exibição de Detalhes** ou a caixa de diálogo **Configurar ListView** do assistente **ListView**.</span><span class="sxs-lookup"><span data-stu-id="bfebb-300">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="bfebb-301">Alterações para melhorar a exibição no modo de Alto Contraste, como o **Editor de Campos do Pager de Dados**.</span><span class="sxs-lookup"><span data-stu-id="bfebb-301">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="bfebb-302">Alterações para melhorar as experiências de navegação por teclado para controles como a caixa de diálogo **Campos** no assistente **Editar Campos do Pager** do controle DataPager, a caixa de diálogo **Configurar ObjectContext** ou a caixa de diálogo **Configurar Seleção de Dados** do assistente **Configurar Fonte de Dados**.</span><span class="sxs-lookup"><span data-stu-id="bfebb-302">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>
## <a name="net-sdk-tools"></a><span data-ttu-id="bfebb-303">Ferramentas do SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="bfebb-303">.NET SDK Tools</span></span>

<span data-ttu-id="bfebb-304">A [Ferramenta Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) e a [Ferramenta Service Trace Viewer (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) foram aprimoradas com a correção de problemas variados de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="bfebb-304">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="bfebb-305">A maioria eram problemas pequenos, como um nome que não está definido ou certos padrões de automação de interface do usuário implementados incorretamente.</span><span class="sxs-lookup"><span data-stu-id="bfebb-305">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="bfebb-306">Embora muitos usuários não estejam cientes desses valores incorretos, os clientes que usam tecnologias adaptativas como leitores de tela considerarão essas ferramentas de SDK mais acessíveis.</span><span class="sxs-lookup"><span data-stu-id="bfebb-306">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> 

<span data-ttu-id="bfebb-307">Essas melhorias alteram alguns comportamentos anteriores, como a ordem de foco do teclado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-307">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="bfebb-308">Designer de Fluxo de Trabalho do WF (Windows Workflow Foundation)</span><span class="sxs-lookup"><span data-stu-id="bfebb-308">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="bfebb-309">As alterações de acessibilidade no Designer de Fluxo de Trabalho incluem as seguintes:</span><span class="sxs-lookup"><span data-stu-id="bfebb-309">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="bfebb-310">A ordem de tabulação é alterada para a esquerda para a direita e de cima para baixo em alguns controles:</span><span class="sxs-lookup"><span data-stu-id="bfebb-310">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="bfebb-311">A janela de inicialização de correlação para definir dados de correlação para a atividade <xref:System.ServiceModel.Activities.InitializeCorrelation>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-311">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="bfebb-312">A janela de definição de conteúdo para as atividades <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-312">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="bfebb-313">Mais funções estão disponíveis por meio do teclado:</span><span class="sxs-lookup"><span data-stu-id="bfebb-313">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="bfebb-314">Ao editar as propriedades de uma atividade, grupos de propriedades podem ser recolhidos pelo teclado na primeira vez em que são colocados em foco.</span><span class="sxs-lookup"><span data-stu-id="bfebb-314">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="bfebb-315">Ícones de aviso podem ser acessados por teclado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-315">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="bfebb-316">O botão **Mais Propriedades** na janela **Propriedades** pode ser acessado pelo teclado.</span><span class="sxs-lookup"><span data-stu-id="bfebb-316">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="bfebb-317">Usuários do teclado podem acessar os itens de cabeçalho nos painéis **Argumentos** e **Variáveis** do Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="bfebb-317">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="bfebb-318">Melhor visibilidade de itens com foco, como ao:</span><span class="sxs-lookup"><span data-stu-id="bfebb-318">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="bfebb-319">Adicionar linhas às grades de dados usadas pelo Designer de Fluxo de Trabalho e por designers de atividades.</span><span class="sxs-lookup"><span data-stu-id="bfebb-319">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="bfebb-320">Percorrer campos nas atividades <xref:System.ServiceModel.Activities.ReceiveReply> e <xref:System.ServiceModel.Activities.SendReply>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-320">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="bfebb-321">Definir valores padrão para variáveis ou argumentos</span><span class="sxs-lookup"><span data-stu-id="bfebb-321">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="bfebb-322">Agora, leitores de tela podem reconhecer corretamente:</span><span class="sxs-lookup"><span data-stu-id="bfebb-322">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="bfebb-323">Pontos de interrupção definidos no Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="bfebb-323">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="bfebb-324">As atividades <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision> e <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-324">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="bfebb-325">O conteúdo da atividade <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-325">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="bfebb-326">O Tipo de Destino da atividade <xref:System.Activities.Statements.InvokeMethod>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-326">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="bfebb-327">A caixa de combinação Exceção e a seção Finalmente na atividade <xref:System.Activities.Statements.TryCatch>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-327">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="bfebb-328">A caixa de combinação Tipo de Mensagem, o divisor na janela Adicionar Inicializadores de Correlação, a janela Definição de Conteúdo e a janela de Definição de CorrelatesOn nas atividades de mensagens (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="bfebb-328">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="bfebb-329">Transições de máquinas de estado e destinos de transição.</span><span class="sxs-lookup"><span data-stu-id="bfebb-329">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="bfebb-330">Anotações e conectores em atividades <xref:System.Activities.Statements.FlowDecision>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-330">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="bfebb-331">Os menus de contexto (clique com o botão direito do mouse) para atividades.</span><span class="sxs-lookup"><span data-stu-id="bfebb-331">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="bfebb-332">Os editores de valor de propriedade, o botão Limpar Pesquisa, os botões de classificação Por Categoria e Ordem Alfabética e a caixa de diálogo Editor de Expressão na grade de propriedades.</span><span class="sxs-lookup"><span data-stu-id="bfebb-332">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="bfebb-333">A porcentagem de zoom no Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="bfebb-333">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="bfebb-334">O separador nas atividades <xref:System.Activities.Statements.Parallel> e <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-334">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="bfebb-335">A atividade <xref:System.Activities.Statements.InvokeDelegate>.</span><span class="sxs-lookup"><span data-stu-id="bfebb-335">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="bfebb-336">A janela Selecionar Tipos para atividades de dicionário (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` etc.).</span><span class="sxs-lookup"><span data-stu-id="bfebb-336">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="bfebb-337">A janela Procurar e Selecionar um Tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="bfebb-337">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="bfebb-338">Trilhas de navegação no Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="bfebb-338">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="bfebb-339">Usuários que escolherem temas de Alto Contraste verão muitas melhorias na visibilidade do Designer de Fluxo de Trabalho e em seus controles, como melhores taxas de contraste entre elementos e caixas de seleção mais perceptíveis usadas para elementos de foco.</span><span class="sxs-lookup"><span data-stu-id="bfebb-339">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfebb-340">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfebb-340">See Also</span></span>

[<span data-ttu-id="bfebb-341">Novidades do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bfebb-341">What's new in the .NET Framework</span></span>](whats-new.md)
 

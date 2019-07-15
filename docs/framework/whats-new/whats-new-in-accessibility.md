---
title: Novidades na acessibilidade do .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da73df97524b9e394fac795daf14a3f0fb1f4e3d
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661381"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="1088f-102">Novidades na acessibilidade do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1088f-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="1088f-103">O .NET Framework pretende tornar os aplicativos mais acessíveis para os usuários.</span><span class="sxs-lookup"><span data-stu-id="1088f-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="1088f-104">As funcionalidades de acessibilidade permitem que um aplicativo forneça uma experiência apropriada para os usuários da Tecnologia Adaptativa.</span><span class="sxs-lookup"><span data-stu-id="1088f-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="1088f-105">A partir do .NET Framework 4.7.1, o .NET Framework inclui diversas melhorias de acessibilidade que permitem aos desenvolvedores criar aplicativos acessíveis.</span><span class="sxs-lookup"><span data-stu-id="1088f-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="1088f-106">Opções de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="1088f-106">Accessibility switches</span></span>

<span data-ttu-id="1088f-107">Configure seu aplicativo para aceitar os recursos de acessibilidade se ele for direcionado ao .NET Framework 4.7 ou a uma versão anterior, mas estiver em execução no .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="1088f-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="1088f-108">Além disso, configure seu aplicativo para usar recursos herdados (e não aproveitar os recursos de acessibilidade) se ele for direcionado ao .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="1088f-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="1088f-109">Cada versão do .NET Framework que inclui recursos de acessibilidade tem uma opção de acessibilidade específica à versão, que você adiciona ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1088f-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="1088f-110">Estas são as opções compatíveis:</span><span class="sxs-lookup"><span data-stu-id="1088f-110">The following are the supported switches:</span></span>

|<span data-ttu-id="1088f-111">Versão</span><span class="sxs-lookup"><span data-stu-id="1088f-111">Version</span></span>|<span data-ttu-id="1088f-112">Alternar</span><span class="sxs-lookup"><span data-stu-id="1088f-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="1088f-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="1088f-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="1088f-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="1088f-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="1088f-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="1088f-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="1088f-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="1088f-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="1088f-117">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="1088f-117">.NET Framework 4.8</span></span>|<span data-ttu-id="1088f-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="1088f-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="1088f-119">Aproveitando as vantagens das melhorias de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="1088f-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="1088f-120">As novas funcionalidades de acessibilidade são habilitadas por padrão para os aplicativos direcionados ao .NET Framework 4.7.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="1088f-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="1088f-121">Além disso, os aplicativos direcionados a uma versão anterior do .NET Framework, mas que estão em execução no .NET Framework 4.7.1 ou posterior, podem recusar os comportamentos de acessibilidade herdados (e, portanto, aproveitar as melhorias de acessibilidade) adicionando opções ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo e definindo seu valor como `false`.</span><span class="sxs-lookup"><span data-stu-id="1088f-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="1088f-122">O seguinte exemplo mostra como aceitar as melhorias de acessibilidade introduzidas no .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="1088f-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="1088f-123">Se você optar por aceitar os recursos de acessibilidade em uma versão posterior do .NET Framework, deverá também aceitar explicitamente os recursos de versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1088f-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="1088f-124">A configuração do aplicativo para aproveitar as melhorias de acessibilidade do .NET Framework 4.7.1 e 4.7.2 exige o seguinte elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="1088f-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="1088f-125">A configuração do aplicativo para aproveitar as melhorias de acessibilidade do .NET Framework 4.7.1, 4.7.2 e 4.8 exige o seguinte elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="1088f-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="1088f-126">Restaurando o comportamento herdado</span><span class="sxs-lookup"><span data-stu-id="1088f-126">Restoring legacy behavior</span></span>

<span data-ttu-id="1088f-127">Os aplicativos direcionados a versões do .NET Framework a começar pela 4.7.1 podem desabilitar os recursos de acessibilidade adicionando opções ao elemento [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) do arquivo de configuração do aplicativo e definindo seu valor como `true`.</span><span class="sxs-lookup"><span data-stu-id="1088f-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="1088f-128">Por exemplo, a seguinte configuração recusa os recursos de acessibilidade introduzidos no .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="1088f-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="1088f-129">Novidades na acessibilidade do .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="1088f-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="1088f-130">O .NET Framework 4.8 inclui novos recursos de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="1088f-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="1088f-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1088f-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="1088f-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1088f-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="1088f-133">Designer de fluxo de trabalho do WF (Windows Workflow Foundation)</span><span class="sxs-lookup"><span data-stu-id="1088f-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="1088f-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1088f-134">Windows Forms</span></span>

<span data-ttu-id="1088f-135">No .NET Framework 4.8, o Windows Forms adiciona suporte ao LiveRegions e Eventos de Notificação para muitos controles usados.</span><span class="sxs-lookup"><span data-stu-id="1088f-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="1088f-136">Ele também adiciona suporte para Dicas de Ferramentas quando um usuário navega para um controle usando o teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="1088f-137">**Suporte para UIA LiveRegions em rótulos e StatusStrips**</span><span class="sxs-lookup"><span data-stu-id="1088f-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="1088f-138">UIA LiveRegions permitem que os desenvolvedores de aplicativos notifiquem os leitores de tela de uma alteração de texto em um controle que está localizado longe do local em que o usuário está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="1088f-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="1088f-139">Isso é útil, por exemplo, para um controle <xref:System.Windows.Forms.StatusStrip> que mostra um status de conexão.</span><span class="sxs-lookup"><span data-stu-id="1088f-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="1088f-140">Se a conexão cair e o status mudar, o desenvolvedor deverá notificar o leitor de tela.</span><span class="sxs-lookup"><span data-stu-id="1088f-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="1088f-141">A partir do .NET Framework 4.8, o Windows Forms implementa UIA LiveRegions nos controles <xref:System.Windows.Forms.Label> e <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="1088f-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="1088f-142">Por exemplo, o seguinte código usa o para LiveRegion em um controle <xref:System.Windows.Forms.Label> chamado `label1`:</span><span class="sxs-lookup"><span data-stu-id="1088f-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="1088f-143">O narrador anuncia “Pronto” independentemente de onde o usuário esteja interagindo com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1088f-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="1088f-144">Você também pode implementar seu <xref:System.Windows.Forms.UserControl> como uma LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="1088f-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

<span data-ttu-id="1088f-145">**Eventos de notificação de UIA**</span><span class="sxs-lookup"><span data-stu-id="1088f-145">**UIA notification events**</span></span>

<span data-ttu-id="1088f-146">O evento de notificação de UIA, apresentado no Windows 10 Fall Creators Update, permite que seu aplicativo gere um evento UIA, que leva o Narrador a simplesmente fazer um anúncio com base no texto que você forneceu com o evento, sem a necessidade de ter um controle correspondente na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1088f-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="1088f-147">Em alguns cenários, isso é uma maneira direta de melhorar consideravelmente a acessibilidade de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1088f-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="1088f-148">Também pode ser útil para notificar sobre o progresso de algum processo que pode levar muito tempo.</span><span class="sxs-lookup"><span data-stu-id="1088f-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="1088f-149">Para obter mais informações sobre eventos de Notificação de UIA, consulte [Seu aplicativo da área de trabalho pode utilizar o novo evento de Notificação de UIA?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span><span class="sxs-lookup"><span data-stu-id="1088f-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span></span>

<span data-ttu-id="1088f-150">O exemplo a seguir gera o [Evento de notificação](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="1088f-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="1088f-151">**Dicas de ferramentas sobre o acesso ao teclado**</span><span class="sxs-lookup"><span data-stu-id="1088f-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="1088f-152">Em aplicativos destinados ao .NET Framework 4.7.2 e versões anteriores, uma [dica de ferramenta](xref:System.Windows.Forms.ToolTip) de controle só pode ser acionada para exibição ao mover o ponteiro do mouse no controle.</span><span class="sxs-lookup"><span data-stu-id="1088f-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="1088f-153">A partir do .NET Framework 4.8, um usuário de teclado pode disparar uma dica de ferramenta de controle, concentrando-se no controle usando uma tecla Tab ou teclas de seta, com ou sem teclas modificadoras.</span><span class="sxs-lookup"><span data-stu-id="1088f-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="1088f-154">Essa melhoria de acessibilidade específica exige uma outra [opção de AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="1088f-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="1088f-155">A figura a seguir mostrará a dica de ferramenta quando o usuário selecionar um botão com o teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![A dica de ferramenta quando o usuário navegar até um botão com o teclado](media/tooltip.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="1088f-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1088f-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="1088f-158">A partir do .NET Framework 4.8, o WPF inclui vários aprimoramentos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="1088f-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="1088f-159">**Narradores de tela não anunciam mais elementos com visibilidade recolhida ou oculta**</span><span class="sxs-lookup"><span data-stu-id="1088f-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="1088f-160">Elementos com visibilidade recolhida ou oculta não são mais anunciados pelo leitor de tela.</span><span class="sxs-lookup"><span data-stu-id="1088f-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="1088f-161">As interfaces do usuário que contêm elementos com uma Visibilidade de <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> ou <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> poderão ser adulteradas pelos leitores de tela se forem apresentadas ao usuário.</span><span class="sxs-lookup"><span data-stu-id="1088f-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="1088f-162">A partir do .NET Framework 4.8, o WPF não inclui mais elementos recolhidos ou ocultos na Exibição de Controle da árvore do UIAutomation. Portanto, os leitores de tela não podem anunciar esses elementos.</span><span class="sxs-lookup"><span data-stu-id="1088f-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="1088f-163">**Propriedade SelectionTextBrush para uso com a seleção de texto não baseada em Adorno**</span><span class="sxs-lookup"><span data-stu-id="1088f-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="1088f-164">No .NET Framework 4.7.2, o WPF adicionou a capacidade de desenhar <xref:System.Windows.Controls.TextBox> e a seleção de texto <xref:System.Windows.Controls.PasswordBox> sem usar a camada de Adorno.</span><span class="sxs-lookup"><span data-stu-id="1088f-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="1088f-165">A cor de primeiro plano do texto selecionado nesse cenário foi determinada pelo <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1088f-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1088f-166">O .NET framework 4.8 adiciona uma nova propriedade, `SelectionTextBrush`, que permite que os desenvolvedores selecionem o pincel específico para o texto selecionado quando usar a seleção de texto não baseada em Adorno.</span><span class="sxs-lookup"><span data-stu-id="1088f-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="1088f-167">Esta propriedade funciona apenas nos controles derivados de <xref:System.Windows.Controls.Primitives.TextBoxBase> e o controle <xref:System.Windows.Controls.PasswordBox> em aplicativos WPF com seleção de texto não baseada em Adorno habilitada.</span><span class="sxs-lookup"><span data-stu-id="1088f-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="1088f-168">Ela não funciona no controle <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="1088f-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="1088f-169">Se a seleção de texto não baseada em Adorno não estiver habilitada, essa propriedade será ignorada.</span><span class="sxs-lookup"><span data-stu-id="1088f-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="1088f-170">Para usar essa propriedade, basta adicioná-la ao seu código XAML e usar a associação ou o pincel adequado.</span><span class="sxs-lookup"><span data-stu-id="1088f-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="1088f-171">A seleção de texto resultante tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="1088f-171">The resulting text selection looks like this:</span></span>

![A dica de ferramenta quando o usuário navegar até um botão com o teclado](media/selectiontextbrush-property.png)

<span data-ttu-id="1088f-173">Você pode combinar o uso das propriedades `SelectionBrush` e `SelectionTextBrush` para gerar qualquer combinação de plano de fundo e cor de primeiro plano que julgar adequada.</span><span class="sxs-lookup"><span data-stu-id="1088f-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="1088f-174">**Suporte para a propriedade ControllerFor do UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="1088f-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="1088f-175">A propriedade `ControllerFor` do UIAutomation retorna uma matriz de elementos de automação manipulados pelo elemento de automação que dá suporte a essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="1088f-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="1088f-176">Essa propriedade normalmente é usada para acessibilidade de sugestão automática.</span><span class="sxs-lookup"><span data-stu-id="1088f-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="1088f-177">`ControllerFor` é usado quando um elemento de automação afeta um ou mais segmentos de interface do usuário do aplicativo ou da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1088f-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="1088f-178">Caso contrário, é difícil associar o impacto da operação de controle com elementos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1088f-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="1088f-179">Este recurso adiciona a capacidade de controles para fornecer um valor para a propriedade `ControllerFor`.</span><span class="sxs-lookup"><span data-stu-id="1088f-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="1088f-180">O .NET framework 4.8 adiciona um novo método virtual, o <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1088f-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1088f-181">Para fornecer um valor para a propriedade `ControllerFor`, basta substituir este método e retornar um `List<AutomationPeer>` para os controles manipulados por este <xref:System.Windows.Automation.Peers.AutomationPeer>:</span><span class="sxs-lookup"><span data-stu-id="1088f-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

<span data-ttu-id="1088f-182">**Dicas de ferramentas sobre o acesso ao teclado**</span><span class="sxs-lookup"><span data-stu-id="1088f-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="1088f-183">No .NET Framework 4.7.2 e versões anteriores, as dicas de ferramentas são exibidas somente quando o usuário passar o cursor do mouse sobre um controle.</span><span class="sxs-lookup"><span data-stu-id="1088f-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="1088f-184">No .NET Framework 4.8, as dicas de ferramentas também são exibidas no foco do teclado, bem como por meio de um atalho de teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="1088f-185">Para habilitar esse recurso, um aplicativo precisa direcionar o .NET Framework 4.8 ou aceitar ao usar as opções `Switch.UseLegacyAccessibilityFeatures.3` e `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="1088f-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="1088f-186">Veja a seguir um arquivo de exemplo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1088f-186">The following is a sample application configuration file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

<span data-ttu-id="1088f-187">Depois de habilitados, todos os controles que contêm uma dica de ferramenta vão exibi-la depois que o controle receber o foco do teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="1088f-188">A dica de ferramenta pode ser ignorada com o tempo ou quando o foco do teclado mudar.</span><span class="sxs-lookup"><span data-stu-id="1088f-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="1088f-189">Os usuários também podem ignorar a dica de ferramenta manualmente usando um novo atalho de teclado, Ctrl + Shift + F10.</span><span class="sxs-lookup"><span data-stu-id="1088f-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="1088f-190">Depois que a dica de ferramenta for ignorada, ela poderá ser exibida novamente usando o mesmo atalho de teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="1088f-191">As [dicas de ferramentas da faixa de opções](xref:System.Windows.Controls.Ribbon.RibbonToolTip) nos controles <xref:System.Windows.Controls.Ribbon.Ribbon> não serão exibidas no foco do teclado. São exibidas somente por meio do atalho de teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="1088f-192">**Adicionado suporte para propriedades SizeOfSet e PositionInSet do UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="1088f-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="1088f-193">O Windows 10 introduziu duas novas propriedades do UIAutomation, `SizeOfSet` e `PositionInSet`, que são usadas por aplicativos para descrever a contagem de itens em um conjunto.</span><span class="sxs-lookup"><span data-stu-id="1088f-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="1088f-194">Aplicativos de cliente do UIAutomation, como leitores de tela podem, então, consultar um aplicativo para essas propriedades e anunciar uma representação precisa da interface de usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1088f-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="1088f-195">A partir do .NET Framework 4.8, o WPF expõe essas duas propriedades para o UIAutomation em aplicativos do WPF.</span><span class="sxs-lookup"><span data-stu-id="1088f-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="1088f-196">Isso pode ser feito de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="1088f-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="1088f-197">Usando propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="1088f-197">By using dependency properties.</span></span>

  <span data-ttu-id="1088f-198">O WPF adiciona duas novas propriedades de dependência, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1088f-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1088f-199">Um desenvolvedor pode usar o XAML para definir seus valores:</span><span class="sxs-lookup"><span data-stu-id="1088f-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="1088f-200">Ao substituir métodos virtuais do AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="1088f-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="1088f-201">Os métodos virtuais <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> e <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> foram adicionados à classe AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="1088f-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="1088f-202">Um desenvolvedor pode fornecer valores para `SizeOfSet` e `PositionInSet` por meio da substituição desses métodos, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1088f-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

<span data-ttu-id="1088f-203">Além disso, os itens nas instâncias <xref:System.Windows.Controls.ItemsControl> fornecem um valor para essas propriedades automaticamente sem ação adicional do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="1088f-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="1088f-204">Se um <xref:System.Windows.Controls.ItemsControl> for agrupado, a coleção de grupos será representada como um conjunto e cada grupo será contado como um conjunto separado, com cada item dentro desse grupo fornecendo sua posição dentro desse grupo, bem como o tamanho do grupo.</span><span class="sxs-lookup"><span data-stu-id="1088f-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="1088f-205">Valores automáticos não são afetados pela virtualização.</span><span class="sxs-lookup"><span data-stu-id="1088f-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="1088f-206">Mesmo que um item não seja percebido, ele ainda é contado para o tamanho total do conjunto e afeta a posição no conjunto de seus itens irmãos.</span><span class="sxs-lookup"><span data-stu-id="1088f-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="1088f-207">Valores automáticos serão fornecidos apenas se o aplicativo for destinado ao .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="1088f-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="1088f-208">Para aplicativos que se destinam a uma versão anterior do .NET Framework, você pode definir a `Switch.UseLegacyAccessibilityFeatures.3` [opção AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), conforme mostrado no seguinte arquivo App.config:</span><span class="sxs-lookup"><span data-stu-id="1088f-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48" />

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="1088f-209">Designer de fluxo de trabalho do WF (Windows Workflow Foundation)</span><span class="sxs-lookup"><span data-stu-id="1088f-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="1088f-210">O designer de fluxo de trabalho inclui as seguintes alterações no .NET Framework 4.8:</span><span class="sxs-lookup"><span data-stu-id="1088f-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="1088f-211">Os usuários que utilizam o Narrador verão melhorias em rótulos de caso do FlowSwitch.</span><span class="sxs-lookup"><span data-stu-id="1088f-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="1088f-212">Os usuários que utilizam o Narrador verão melhorias em descrições de botão.</span><span class="sxs-lookup"><span data-stu-id="1088f-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="1088f-213">Usuários que escolherem temas de Alto Contraste verão melhorias na visibilidade do Designer de Fluxo de Trabalho e em seus controles, como melhores taxas de contraste entre elementos e caixas de seleção mais perceptíveis usadas para elementos de foco.</span><span class="sxs-lookup"><span data-stu-id="1088f-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="1088f-214">Se o seu aplicativo for destinado ao .NET Framework 4.7.2 ou uma versão anterior, você poderá aceitar essas alterações, definindo a `Switch.UseLegacyAccessibilityFeatures.3` [opção de AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) para `false` no seu arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1088f-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="1088f-215">Para obter mais informações, consulte a seção [Aproveitando os aprimoramentos de acessibilidade](#taking-advantage-of-accessibility-enhancements) neste artigo.</span><span class="sxs-lookup"><span data-stu-id="1088f-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="1088f-216">Novidades na acessibilidade do .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="1088f-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="1088f-217">O .NET Framework 4.7.2 inclui novos recursos de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="1088f-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="1088f-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1088f-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="1088f-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1088f-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="1088f-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1088f-220">Windows Forms</span></span>

<span data-ttu-id="1088f-221">**Cores definidas pelo sistema operacional em temas de Alto Contraste**</span><span class="sxs-lookup"><span data-stu-id="1088f-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="1088f-222">Começando no .NET Framework 4.7.2, o Windows Forms usa cores definidas pelo sistema operacional em temas de Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="1088f-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="1088f-223">Isso afeta os seguintes controles:</span><span class="sxs-lookup"><span data-stu-id="1088f-223">This affects the following controls:</span></span>

- <span data-ttu-id="1088f-224">A seta suspensa do controle <xref:System.Windows.Forms.ToolStripDropDownButton>.</span><span class="sxs-lookup"><span data-stu-id="1088f-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="1088f-225">Os controles <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> e <xref:System.Windows.Forms.CheckBox> com <xref:System.Windows.Forms.ButtonBase.FlatStyle> definido como <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> ou <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1088f-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1088f-226">Anteriormente, as cores de texto e da tela de fundo selecionadas não eram contrastantes e eram difíceis de serem lidas.</span><span class="sxs-lookup"><span data-stu-id="1088f-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="1088f-227">Os controles contidos em uma <xref:System.Windows.Forms.GroupBox> que tem sua propriedade <xref:System.Windows.Forms.Control.Enabled> definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="1088f-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="1088f-228">Os controles <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox> e <xref:System.Windows.Forms.ToolStripDropDownButton>, que têm uma taxa maior de contraste de luminosidade no Modo de Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="1088f-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="1088f-229">A propriedade <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> do <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="1088f-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="1088f-230">**Melhorias do Narrador**</span><span class="sxs-lookup"><span data-stu-id="1088f-230">**Narrator improvements**</span></span>

<span data-ttu-id="1088f-231">A partir do .NET Framework 4.7.2, o suporte ao Narrador é aprimorado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1088f-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="1088f-232">Ele anuncia o valor da propriedade <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> quando anuncia o texto de um <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="1088f-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="1088f-233">Ele indica quando um <xref:System.Windows.Forms.ToolStripMenuItem> tem sua propriedade <xref:System.Windows.Forms.Control.Enabled> definida como `false`.</span><span class="sxs-lookup"><span data-stu-id="1088f-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="1088f-234">Ele fornece comentários sobre o estado de uma caixa de seleção quando a propriedade <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="1088f-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="1088f-235">A ordem de foco do Modo de Verificação do Narrador é consistente com a ordem visual dos controles na janela de diálogo de download do ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="1088f-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="1088f-236">**Melhorias de DataGridView**</span><span class="sxs-lookup"><span data-stu-id="1088f-236">**DataGridView improvements**</span></span>

<span data-ttu-id="1088f-237">A partir do .NET Framework 4.7.2, o controle <xref:System.Windows.Forms.DataGridView> introduziu as seguintes melhorias de acessibilidade:</span><span class="sxs-lookup"><span data-stu-id="1088f-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="1088f-238">As linhas podem ser classificadas com o teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="1088f-239">Um usuário pode usar a tecla F3 para classificar pela coluna atual.</span><span class="sxs-lookup"><span data-stu-id="1088f-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="1088f-240">Quando o <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> é definido como <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, o cabeçalho da coluna muda de cor para indicar a coluna atual, à medida que o usuário pressiona Tab para percorrer as células na linha atual.</span><span class="sxs-lookup"><span data-stu-id="1088f-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="1088f-241">A propriedade <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> de um <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> retorna o controle pai correto.</span><span class="sxs-lookup"><span data-stu-id="1088f-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="1088f-242">**Melhoria das indicações visuais**</span><span class="sxs-lookup"><span data-stu-id="1088f-242">**Improved visual cues**</span></span>

- <span data-ttu-id="1088f-243">Os controles <xref:System.Windows.Forms.RadioButton> e <xref:System.Windows.Forms.CheckBox> com uma propriedade <xref:System.Windows.Forms.ButtonBase.Text> vazia exibem um indicador de foco quando recebem o foco.</span><span class="sxs-lookup"><span data-stu-id="1088f-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="1088f-244">**Melhoria no suporte à grade de propriedade**</span><span class="sxs-lookup"><span data-stu-id="1088f-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="1088f-245">Os elementos filhos do controle <xref:System.Windows.Forms.PropertyGrid> agora retornam um `true` para a propriedade <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> somente quando um elemento PropertyGrid está habilitado.</span><span class="sxs-lookup"><span data-stu-id="1088f-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="1088f-246">Os elementos filho do controle <xref:System.Windows.Forms.PropertyGrid> retornam um `false` para a propriedade <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> somente quando um elemento PropertyGrid pode ser alterado pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1088f-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="1088f-247">**Melhoria na navegação por teclado**</span><span class="sxs-lookup"><span data-stu-id="1088f-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="1088f-248">O controle <xref:System.Windows.Forms.ToolStripButton> permite o foco quando contido em um <xref:System.Windows.Forms.ToolStripPanel> que tem a propriedade <xref:System.Windows.Forms.ToolStripPanel.TabStop> definida como `true`</span><span class="sxs-lookup"><span data-stu-id="1088f-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="1088f-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1088f-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="1088f-250">**Alterações nos controles CheckBox e RadioButton**</span><span class="sxs-lookup"><span data-stu-id="1088f-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="1088f-251">No .NET Framework 4.7.1 e nas versões anteriores, os controles <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> e <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> do WPF têm visuais de foco inconsistentes e, nos temas Clássico e de Alto Contraste, têm visuais de foco incorretos.</span><span class="sxs-lookup"><span data-stu-id="1088f-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="1088f-252">Esses problemas ocorrem quando os controles não têm nenhum conjunto de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1088f-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="1088f-253">Isso pode dificultar a transição entre os temas e deixar o visual de foco confuso.</span><span class="sxs-lookup"><span data-stu-id="1088f-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="1088f-254">No .NET Framework 4.7.2, agora esses visuais são mais consistentes entre os temas e mais facilmente visíveis nos temas Clássico e de Alto Contraste.</span><span class="sxs-lookup"><span data-stu-id="1088f-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="1088f-255">**Controles do WinForms hospedados em um aplicativo WPF**</span><span class="sxs-lookup"><span data-stu-id="1088f-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="1088f-256">Para controles do WinForms hospedados em um aplicativo do WPF no .NET Framework 4.7.1 e versões anteriores, os usuários não poderão sair da guia da camada do WinForms se o primeiro ou o último controle da camada for o controle <xref:System.Windows.Forms.Integration.ElementHost> do WPF.</span><span class="sxs-lookup"><span data-stu-id="1088f-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="1088f-257">No .NET Framework 4.7.2, os usuários agora podem sair da guia da camada do WinForms.</span><span class="sxs-lookup"><span data-stu-id="1088f-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="1088f-258">No entanto, os aplicativos automatizados que se baseiam em foco e que nunca são escapados da camada do WinForms podem deixar de funcionar conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="1088f-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="1088f-259">Novidades na acessibilidade do .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="1088f-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="1088f-260">O .NET Framework 4.7.1 inclui novos recursos de acessibilidade nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="1088f-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="1088f-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1088f-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="1088f-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1088f-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="1088f-263">Controles da Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1088f-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="1088f-264">Ferramentas do SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="1088f-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="1088f-265">Designer de Fluxo de Trabalho do WF (Windows Workflow Foundation)</span><span class="sxs-lookup"><span data-stu-id="1088f-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="1088f-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1088f-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="1088f-267">**Melhorias do leitor de tela**</span><span class="sxs-lookup"><span data-stu-id="1088f-267">**Screen reader improvements**</span></span>

<span data-ttu-id="1088f-268">Se as melhorias de acessibilidade estiverem habilitadas, o .NET Framework 4.7.1 incluirá as seguintes melhorias que afetam os leitores de tela:</span><span class="sxs-lookup"><span data-stu-id="1088f-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="1088f-269">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.Expander> foram divulgados pelos leitores de tela como botões.</span><span class="sxs-lookup"><span data-stu-id="1088f-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="1088f-270">A partir do .NET Framework 4.7.1, eles são corretamente divulgados como grupos expansíveis/recolhíveis.</span><span class="sxs-lookup"><span data-stu-id="1088f-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="1088f-271">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.DataGridCell> foram divulgados pelos leitores de tela como “personalizados”.</span><span class="sxs-lookup"><span data-stu-id="1088f-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="1088f-272">A partir do .NET Framework 4.7.1, agora eles são corretamente divulgados como célula de grade de dados (localizada).</span><span class="sxs-lookup"><span data-stu-id="1088f-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="1088f-273">A partir do .NET Framework 4.7.1, os leitores de tela divulgam o nome de uma <xref:System.Windows.Controls.ComboBox> editável.</span><span class="sxs-lookup"><span data-stu-id="1088f-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="1088f-274">No .NET Framework 4.7 e em versões anteriores, os controles <xref:System.Windows.Controls.PasswordBox> eram divulgados como “nenhum item em exibição” ou, de outro modo, apresentavam um comportamento incorreto.</span><span class="sxs-lookup"><span data-stu-id="1088f-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="1088f-275">Esse problema é corrigido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="1088f-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="1088f-276">**Suporte a UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="1088f-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="1088f-277">Leitores de tela, como o Narrador, ajudam as pessoas a ler o conteúdo da interface do usuário de um aplicativo, normalmente, pela saída de conversão de texto em fala do conteúdo da interface do usuário que tem o foco.</span><span class="sxs-lookup"><span data-stu-id="1088f-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="1088f-278">No entanto, se um elemento da interface do usuário for alterado e não tiver o foco, o usuário poderá não ser notificado e perder informações importantes.</span><span class="sxs-lookup"><span data-stu-id="1088f-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="1088f-279">As regiões dinâmicas pretendem resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="1088f-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="1088f-280">Um desenvolvedor pode usá-las para informar o leitor de tela ou qualquer outro cliente de UIAutomation de que foi feita uma alteração importante em um elemento da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1088f-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="1088f-281">Em seguida, o leitor de tela pode decidir como e quando informar o usuário dessa alteração.</span><span class="sxs-lookup"><span data-stu-id="1088f-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="1088f-282">Para dar suporte a regiões dinâmicas, as seguintes APIs foram adicionadas ao WPF:</span><span class="sxs-lookup"><span data-stu-id="1088f-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="1088f-283">Os campos <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, que identificam a propriedade **LiveSetting** e o evento **LiveRegionChanged**.</span><span class="sxs-lookup"><span data-stu-id="1088f-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="1088f-284">Eles podem ser definidos com XAML.</span><span class="sxs-lookup"><span data-stu-id="1088f-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="1088f-285">A propriedade anexada **AutomationProperties.LiveSetting**, que informa o leitor de tela da importância da alteração da interface do usuário para o usuário.</span><span class="sxs-lookup"><span data-stu-id="1088f-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="1088f-286">A propriedade <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, que identifica a propriedade anexada **AutomationProperties.LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="1088f-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="1088f-287">O método <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, que pode ser substituído para fornecer um valor de **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="1088f-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="1088f-288">Os métodos <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> e <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, que obtêm e definem um valor de **LiveSetting**.</span><span class="sxs-lookup"><span data-stu-id="1088f-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="1088f-289">A enumeração <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, que define os seguintes possíveis valores de **LiveSetting**:</span><span class="sxs-lookup"><span data-stu-id="1088f-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="1088f-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1088f-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1088f-291">O elemento não envia notificações se o conteúdo da região dinâmica foi alterado.</span><span class="sxs-lookup"><span data-stu-id="1088f-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="1088f-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1088f-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1088f-293">O elemento enviará notificações não interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="1088f-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="1088f-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1088f-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1088f-295">O elemento enviará notificações interruptivas se o conteúdo da região dinâmica tiver sido alterado.</span><span class="sxs-lookup"><span data-stu-id="1088f-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="1088f-296">Crie uma LiveRegion configurar a propriedade **AutomationProperties.LiveSetting** no elemento de interesse, conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="1088f-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="1088f-297">Quando os dados da região dinâmica forem alterados e você precisar informar um leitor de tela, acione um evento explicitamente, conforme mostrado na amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="1088f-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="1088f-298">**Alto contraste**</span><span class="sxs-lookup"><span data-stu-id="1088f-298">**High contrast**</span></span>

<span data-ttu-id="1088f-299">A partir do .NET Framework 4.7.1, foram feitas melhorias de alto contraste em vários controles do WPF.</span><span class="sxs-lookup"><span data-stu-id="1088f-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="1088f-300">Agora eles estão visíveis quando o tema <xref:System.Windows.SystemParameters.HighContrast%2A> é definido.</span><span class="sxs-lookup"><span data-stu-id="1088f-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="1088f-301">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="1088f-301">These include:</span></span>

- <span data-ttu-id="1088f-302">Controle <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="1088f-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="1088f-303">O visual de foco do controle <xref:System.Windows.Controls.Expander> agora está visível.</span><span class="sxs-lookup"><span data-stu-id="1088f-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="1088f-304">Os visuais de teclado dos controles <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.RadioButton> também estão visíveis.</span><span class="sxs-lookup"><span data-stu-id="1088f-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="1088f-305">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1088f-305">For example:</span></span>

  <span data-ttu-id="1088f-306">Antes:</span><span class="sxs-lookup"><span data-stu-id="1088f-306">Before:</span></span> 

  ![Controle expansor com foco antes das melhorias de acessibilidade](media/expander-before.png)

  <span data-ttu-id="1088f-308">Depois:</span><span class="sxs-lookup"><span data-stu-id="1088f-308">After:</span></span> 

  ![Controle expansor com foco após as melhorias de acessibilidade](media/expander-after.png)

- <span data-ttu-id="1088f-310">Controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton></span><span class="sxs-lookup"><span data-stu-id="1088f-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="1088f-311">O texto nos controles <xref:System.Windows.Controls.CheckBox> e <xref:System.Windows.Controls.RadioButton> agora é de visualização mais fácil quando selecionado em temas de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="1088f-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="1088f-312">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1088f-312">For example:</span></span>

  <span data-ttu-id="1088f-313">Antes:</span><span class="sxs-lookup"><span data-stu-id="1088f-313">Before:</span></span> 

  ![Botão de opção de alto contraste com foco antes das melhorias de acessibilidade](media/radio-button-before.png)

  <span data-ttu-id="1088f-315">Depois:</span><span class="sxs-lookup"><span data-stu-id="1088f-315">After:</span></span> 

  ![Botão de opção de alto contraste com foco após as melhorias de acessibilidade](media/radio-button-after.png)

- <span data-ttu-id="1088f-317">Controle <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="1088f-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="1088f-318">A partir do .NET Framework 4.7.1, a borda de um controle <xref:System.Windows.Controls.ComboBox> desabilitado é da mesma cor do texto desabilitado.</span><span class="sxs-lookup"><span data-stu-id="1088f-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="1088f-319">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1088f-319">For example:</span></span>

  <span data-ttu-id="1088f-320">Antes:</span><span class="sxs-lookup"><span data-stu-id="1088f-320">Before:</span></span> 

  ![Borda e texto desabilitados da ComboBox antes das melhorias de acessibilidade](media/combo-disabled-before.png)

  <span data-ttu-id="1088f-322">Depois:</span><span class="sxs-lookup"><span data-stu-id="1088f-322">After:</span></span>   

  ![Borda e texto desabilitados da ComboBox após as melhorias de acessibilidade](media/combo-disabled-after.png)

  <span data-ttu-id="1088f-324">Além disso, os botões desabilitados e com foco usam a cor de tema correta.</span><span class="sxs-lookup"><span data-stu-id="1088f-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="1088f-325">Antes:</span><span class="sxs-lookup"><span data-stu-id="1088f-325">Before:</span></span>

  ![Cores de tema do botão antes das melhorias de acessibilidade](media/button-themes-before.png) 

  <span data-ttu-id="1088f-327">Depois:</span><span class="sxs-lookup"><span data-stu-id="1088f-327">After:</span></span> 

  ![Cores de tema do botão após as melhorias de acessibilidade](media/button-themes-after.png) 

  <span data-ttu-id="1088f-329">Por fim, no .NET Framework 4.7 e em versões anteriores, a configuração do estilo de um controle <xref:System.Windows.Controls.ComboBox> como `Toolbar.ComboBoxStyleKey` fazia com que a seta suspensa ficasse invisível.</span><span class="sxs-lookup"><span data-stu-id="1088f-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="1088f-330">Esse problema é corrigido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="1088f-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="1088f-331">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1088f-331">For example:</span></span>

  <span data-ttu-id="1088f-332">Antes:</span><span class="sxs-lookup"><span data-stu-id="1088f-332">Before:</span></span> 

  ![Toolbar.ComboBoxStyleKey antes das melhorias de acessibilidade](media/comboboxstylekey-before.png) 

  <span data-ttu-id="1088f-334">Depois:</span><span class="sxs-lookup"><span data-stu-id="1088f-334">After:</span></span> 

  ![Toolbar.ComboBoxStyleKey após as melhorias de acessibilidade](media/comboboxstylekey-after.png) 

- <span data-ttu-id="1088f-336">Controle <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="1088f-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="1088f-337">A partir do .NET Framework 4.7.1, a seta do indicador de classificação nos controles <xref:System.Windows.Controls.DataGrid> agora usa as cores de tema corretas.</span><span class="sxs-lookup"><span data-stu-id="1088f-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="1088f-338">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1088f-338">For example:</span></span>

  <span data-ttu-id="1088f-339">Antes:</span><span class="sxs-lookup"><span data-stu-id="1088f-339">Before:</span></span> 

  ![Seta do indicador de classificação antes das melhorias de acessibilidade](media/sort-indicator-before.png) 

  <span data-ttu-id="1088f-341">Depois:</span><span class="sxs-lookup"><span data-stu-id="1088f-341">After:</span></span>   

  ![Seta do indicador de classificação após as melhorias de acessibilidade](media/sort-indicator-after.png) 

  <span data-ttu-id="1088f-343">Além disso, no .NET Framework 4.7 e em versões anteriores, o estilo de link padrão era alterado para uma cor incorreta ao passar o mouse nos modos de alto contraste.</span><span class="sxs-lookup"><span data-stu-id="1088f-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="1088f-344">Isso é resolvido a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="1088f-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="1088f-345">Da mesma forma, as colunas da caixa de seleção <xref:System.Windows.Controls.DataGrid> usam as cores esperadas para os comentários do foco de teclado a partir do .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="1088f-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="1088f-346">Antes:</span><span class="sxs-lookup"><span data-stu-id="1088f-346">Before:</span></span> 

  ![Estilo de link padrão de DataGrid antes das melhorias de acessibilidade](media/default-link-style-before.png) 

  <span data-ttu-id="1088f-348">Depois:</span><span class="sxs-lookup"><span data-stu-id="1088f-348">After:</span></span>    

  ![Estilo de link padrão de DataGrid após as melhorias de acessibilidade](media/default-link-style-after.png) 

<span data-ttu-id="1088f-350">Para obter mais informações sobre as melhorias de acessibilidade do WPF no .NET Framework 4.7.1, consulte [Melhorias de acessibilidade no WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="1088f-350">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="1088f-351">Melhorias de acessibilidade do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1088f-351">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="1088f-352">No .NET Framework 4.7.1, o WinForms (Windows Forms) inclui alterações de acessibilidade nas áreas a seguir.</span><span class="sxs-lookup"><span data-stu-id="1088f-352">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="1088f-353">**Vídeo aprimorado no modo de Alto Contraste**</span><span class="sxs-lookup"><span data-stu-id="1088f-353">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="1088f-354">Do .NET Framework 4.7.1 em diante, vários controles do WinForms oferecem uma melhor renderização nos modos de HighContrast disponíveis no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="1088f-354">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="1088f-355">O Windows 10 alterou os valores de algumas cores do sistema de alto contraste e o Windows Forms é baseado na estrutura Win32 do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="1088f-355">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="1088f-356">Para obter a melhor experiência, execute a última versão do Windows e aceite as últimas alterações do sistema operacional adicionando um arquivo app.manifest a um aplicativo de teste e remova a marca de comentário da linha de sistema operacional com suporte do Windows 10, de modo que ela fique parecida com a seguinte:</span><span class="sxs-lookup"><span data-stu-id="1088f-356">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="1088f-357">Alguns exemplos de alterações de alto contraste incluem:</span><span class="sxs-lookup"><span data-stu-id="1088f-357">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="1088f-358">Marcas de seleção em itens <xref:System.Windows.Forms.MenuStrip> são mais fáceis de serem exibidas.</span><span class="sxs-lookup"><span data-stu-id="1088f-358">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="1088f-359">Quando selecionados, os itens <xref:System.Windows.Forms.MenuStrip> desabilitados são mais fáceis de serem exibidos.</span><span class="sxs-lookup"><span data-stu-id="1088f-359">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="1088f-360">O texto em um controle <xref:System.Windows.Forms.Button> selecionado contrasta com a cor da seleção.</span><span class="sxs-lookup"><span data-stu-id="1088f-360">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="1088f-361">O texto desabilitado é mais fácil de ser lido.</span><span class="sxs-lookup"><span data-stu-id="1088f-361">Disabled text is easier to read.</span></span> <span data-ttu-id="1088f-362">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1088f-362">For example:</span></span>

  <span data-ttu-id="1088f-363">Antes:</span><span class="sxs-lookup"><span data-stu-id="1088f-363">Before:</span></span>

  ![Texto desabilitado antes das melhorias de acessibilidade](media/wf-disabled-before.png) 

  <span data-ttu-id="1088f-365">Depois:</span><span class="sxs-lookup"><span data-stu-id="1088f-365">After:</span></span>

  ![Texto desabilitado após as melhorias de acessibilidade](media/wf-disabled-after.png) 

- <span data-ttu-id="1088f-367">Melhorias de alto contraste na caixa de diálogo Exceção de Thread.</span><span class="sxs-lookup"><span data-stu-id="1088f-367">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="1088f-368">**Melhor suporte ao Narrador**</span><span class="sxs-lookup"><span data-stu-id="1088f-368">**Improved Narrator support**</span></span>

<span data-ttu-id="1088f-369">O Windows Forms no .NET Framework 4.7.1 inclui as seguintes melhorias de acessibilidade para o Narrador:</span><span class="sxs-lookup"><span data-stu-id="1088f-369">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="1088f-370">O controle <xref:System.Windows.Forms.MonthCalendar> pode ser acessado pelo Narrador, bem como por outras ferramentas de automação da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1088f-370">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="1088f-371">O controle <xref:System.Windows.Forms.CheckedListBox> notifica o Narrador quando o estado de seleção do item foi alterado, para que o usuário seja notificado de que ele alterou o valor de um item de lista.</span><span class="sxs-lookup"><span data-stu-id="1088f-371">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="1088f-372">O controle <xref:System.Windows.Forms.DataGridViewCell> relata o status somente leitura correto para o Narrador.</span><span class="sxs-lookup"><span data-stu-id="1088f-372">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="1088f-373">O Narrador agora pode ler o texto <xref:System.Windows.Forms.ToolStripMenuItem> desabilitado, enquanto, anteriormente, ele ignorava itens de menu desabilitados.</span><span class="sxs-lookup"><span data-stu-id="1088f-373">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="1088f-374">**Suporte aprimorado para padrões de acessibilidade de UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="1088f-374">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="1088f-375">A partir do .NET Framework 4.7.1, os desenvolvedores de ferramentas de tecnologia de acessibilidade podem utilizar padrões comuns de acessibilidade de API e as propriedades de vários controles WinForms.</span><span class="sxs-lookup"><span data-stu-id="1088f-375">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="1088f-376">Essas melhorias de acessibilidade incluem:</span><span class="sxs-lookup"><span data-stu-id="1088f-376">These accessibility improvements include:</span></span>

- <span data-ttu-id="1088f-377">O <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.ToolStripSplitButton> agora dão suporte ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="1088f-377">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="1088f-378">O <xref:System.Windows.Forms.DataGridViewCheckBoxCell> agora dá suporte ao [padrão alternar](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="1088f-378">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="1088f-379">O controle <xref:System.Windows.Forms.ToolStripItem> dá suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> e ao [padrão expandir/recolher](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="1088f-379">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="1088f-380">Os controles <xref:System.Windows.Forms.NumericUpDown> e <xref:System.Windows.Forms.DomainUpDown> dão suporte à propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.</span><span class="sxs-lookup"><span data-stu-id="1088f-380">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="1088f-381">**Melhor experiência do navegador de propriedades**</span><span class="sxs-lookup"><span data-stu-id="1088f-381">**Improved property browser experience**</span></span>

<span data-ttu-id="1088f-382">A partir do .NET Framework 4.7.1, o Windows Forms inclui:</span><span class="sxs-lookup"><span data-stu-id="1088f-382">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="1088f-383">Melhor navegação de teclado por meio das várias janelas de seleção suspensa.</span><span class="sxs-lookup"><span data-stu-id="1088f-383">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="1088f-384">Uma redução de paradas de tabulação desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="1088f-384">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="1088f-385">Melhor relatório de tipos de controle.</span><span class="sxs-lookup"><span data-stu-id="1088f-385">Better reporting of control types.</span></span>
- <span data-ttu-id="1088f-386">Melhor comportamento do Narrador.</span><span class="sxs-lookup"><span data-stu-id="1088f-386">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="1088f-387">Controles da Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1088f-387">ASP.NET web controls</span></span>

<span data-ttu-id="1088f-388">Começando no .NET Framework 4.7.1 e no Visual Studio 2017 15.3, o ASP.NET melhorará o funcionamento dos controles da Web do ASP.NET com a tecnologia de acessibilidade no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1088f-388">Starting with .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="1088f-389">As alterações incluem as seguintes:</span><span class="sxs-lookup"><span data-stu-id="1088f-389">Changes include the following:</span></span>

- <span data-ttu-id="1088f-390">Alterações para implementar padrões de acessibilidade de interface do usuário ausentes em controles como a caixa de diálogo **Adicionar Campo** no assistente de **Exibição de Detalhes** ou a caixa de diálogo **Configurar ListView** do assistente **ListView**.</span><span class="sxs-lookup"><span data-stu-id="1088f-390">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="1088f-391">Alterações para melhorar a exibição no modo de Alto Contraste, como o **Editor de Campos do Pager de Dados**.</span><span class="sxs-lookup"><span data-stu-id="1088f-391">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="1088f-392">Alterações para melhorar as experiências de navegação por teclado para controles como a caixa de diálogo **Campos** no assistente **Editar Campos do Pager** do controle DataPager, a caixa de diálogo **Configurar ObjectContext** ou a caixa de diálogo **Configurar Seleção de Dados** do assistente **Configurar Fonte de Dados**.</span><span class="sxs-lookup"><span data-stu-id="1088f-392">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="1088f-393">Ferramentas do SDK do .NET</span><span class="sxs-lookup"><span data-stu-id="1088f-393">.NET SDK Tools</span></span>

<span data-ttu-id="1088f-394">A [Ferramenta Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) e a [Ferramenta Service Trace Viewer (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) foram aprimoradas com a correção de problemas variados de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="1088f-394">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="1088f-395">A maioria eram problemas pequenos, como um nome que não está definido ou certos padrões de automação de interface do usuário implementados incorretamente.</span><span class="sxs-lookup"><span data-stu-id="1088f-395">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="1088f-396">Embora muitos usuários não estejam cientes desses valores incorretos, os clientes que usam tecnologias adaptativas como leitores de tela considerarão essas ferramentas de SDK mais acessíveis.</span><span class="sxs-lookup"><span data-stu-id="1088f-396">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="1088f-397">Essas melhorias alteram alguns comportamentos anteriores, como a ordem de foco do teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-397">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="1088f-398">Designer de Fluxo de Trabalho do WF (Windows Workflow Foundation)</span><span class="sxs-lookup"><span data-stu-id="1088f-398">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="1088f-399">As alterações de acessibilidade no Designer de Fluxo de Trabalho incluem as seguintes:</span><span class="sxs-lookup"><span data-stu-id="1088f-399">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="1088f-400">A ordem de tabulação é alterada para a esquerda para a direita e de cima para baixo em alguns controles:</span><span class="sxs-lookup"><span data-stu-id="1088f-400">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="1088f-401">A janela de inicialização de correlação para definir dados de correlação para a atividade <xref:System.ServiceModel.Activities.InitializeCorrelation>.</span><span class="sxs-lookup"><span data-stu-id="1088f-401">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="1088f-402">A janela de definição de conteúdo para as atividades <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>.</span><span class="sxs-lookup"><span data-stu-id="1088f-402">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="1088f-403">Mais funções estão disponíveis por meio do teclado:</span><span class="sxs-lookup"><span data-stu-id="1088f-403">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="1088f-404">Ao editar as propriedades de uma atividade, grupos de propriedades podem ser recolhidos pelo teclado na primeira vez em que são colocados em foco.</span><span class="sxs-lookup"><span data-stu-id="1088f-404">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="1088f-405">Ícones de aviso podem ser acessados por teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-405">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="1088f-406">O botão **Mais Propriedades** na janela **Propriedades** pode ser acessado pelo teclado.</span><span class="sxs-lookup"><span data-stu-id="1088f-406">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="1088f-407">Usuários do teclado podem acessar os itens de cabeçalho nos painéis **Argumentos** e **Variáveis** do Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="1088f-407">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="1088f-408">Melhor visibilidade de itens com foco, como ao:</span><span class="sxs-lookup"><span data-stu-id="1088f-408">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="1088f-409">Adicionar linhas às grades de dados usadas pelo Designer de Fluxo de Trabalho e por designers de atividades.</span><span class="sxs-lookup"><span data-stu-id="1088f-409">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="1088f-410">Percorrer campos nas atividades <xref:System.ServiceModel.Activities.ReceiveReply> e <xref:System.ServiceModel.Activities.SendReply>.</span><span class="sxs-lookup"><span data-stu-id="1088f-410">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="1088f-411">Definir valores padrão para variáveis ou argumentos</span><span class="sxs-lookup"><span data-stu-id="1088f-411">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="1088f-412">Agora, leitores de tela podem reconhecer corretamente:</span><span class="sxs-lookup"><span data-stu-id="1088f-412">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="1088f-413">Pontos de interrupção definidos no Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="1088f-413">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="1088f-414">As atividades <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision> e <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="1088f-414">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="1088f-415">O conteúdo da atividade <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="1088f-415">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="1088f-416">O Tipo de Destino da atividade <xref:System.Activities.Statements.InvokeMethod>.</span><span class="sxs-lookup"><span data-stu-id="1088f-416">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="1088f-417">A caixa de combinação Exceção e a seção Finalmente na atividade <xref:System.Activities.Statements.TryCatch>.</span><span class="sxs-lookup"><span data-stu-id="1088f-417">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="1088f-418">A caixa de combinação Tipo de Mensagem, o divisor na janela Adicionar Inicializadores de Correlação, a janela Definição de Conteúdo e a janela de Definição de CorrelatesOn nas atividades de mensagens (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="1088f-418">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="1088f-419">Transições de máquinas de estado e destinos de transição.</span><span class="sxs-lookup"><span data-stu-id="1088f-419">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="1088f-420">Anotações e conectores em atividades <xref:System.Activities.Statements.FlowDecision>.</span><span class="sxs-lookup"><span data-stu-id="1088f-420">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="1088f-421">Os menus de contexto (clique com o botão direito do mouse) para atividades.</span><span class="sxs-lookup"><span data-stu-id="1088f-421">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="1088f-422">Os editores de valor de propriedade, o botão Limpar Pesquisa, os botões de classificação Por Categoria e Ordem Alfabética e a caixa de diálogo Editor de Expressão na grade de propriedades.</span><span class="sxs-lookup"><span data-stu-id="1088f-422">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="1088f-423">A porcentagem de zoom no Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="1088f-423">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="1088f-424">O separador nas atividades <xref:System.Activities.Statements.Parallel> e <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="1088f-424">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="1088f-425">A atividade <xref:System.Activities.Statements.InvokeDelegate>.</span><span class="sxs-lookup"><span data-stu-id="1088f-425">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="1088f-426">A janela Selecionar Tipos para atividades de dicionário (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` etc.).</span><span class="sxs-lookup"><span data-stu-id="1088f-426">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="1088f-427">A janela Procurar e Selecionar um Tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="1088f-427">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="1088f-428">Trilhas de navegação no Designer de Fluxo de Trabalho.</span><span class="sxs-lookup"><span data-stu-id="1088f-428">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="1088f-429">Usuários que escolherem temas de Alto Contraste verão muitas melhorias na visibilidade do Designer de Fluxo de Trabalho e em seus controles, como melhores taxas de contraste entre elementos e caixas de seleção mais perceptíveis usadas para elementos de foco.</span><span class="sxs-lookup"><span data-stu-id="1088f-429">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="1088f-430">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1088f-430">See also</span></span>

- [<span data-ttu-id="1088f-431">Novidades do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1088f-431">What's new in the .NET Framework</span></span>](whats-new.md)

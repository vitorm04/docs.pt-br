---
title: Suporte a alto DPI no Windows Forms
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbf2d7b61b34a2cd4641a77ee1f2fcdff7f3c3fe
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34483535"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="32bdc-102">Suporte a alto DPI no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32bdc-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="32bdc-103">Começando com o .NET Framework 4.7, formulários do Windows inclui aprimoramentos de alto DPI comuns e cenários DPI dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="32bdc-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="32bdc-104">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="32bdc-104">These include:</span></span> 

- <span data-ttu-id="32bdc-105">Melhorias no layout de um número de formulários do Windows e dimensionando controles, como o <xref:System.Windows.Forms.MonthCalendar> controle e o <xref:System.Windows.Forms.CheckedListBox> controle.</span><span class="sxs-lookup"><span data-stu-id="32bdc-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> 

- <span data-ttu-id="32bdc-106">Passagem única escala.</span><span class="sxs-lookup"><span data-stu-id="32bdc-106">Single-pass scaling.</span></span>  <span data-ttu-id="32bdc-107">No .NET Framework 4.6 e versões anteriores, o dimensionamento foi realizada por meio de várias passagens, o que causou alguns controles será dimensionada mais do que era necessária.</span><span class="sxs-lookup"><span data-stu-id="32bdc-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="32bdc-108">Suporte para cenários DPI dinâmicos no qual o usuário altera o fator de escala ou DPI depois que um aplicativo Windows Forms foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="32bdc-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="32bdc-109">Nas versões do .NET Framework, começando com o .NET Framework 4.7, suporte aprimorado de alto DPI é um recurso de aceitação.</span><span class="sxs-lookup"><span data-stu-id="32bdc-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="32bdc-110">Você deve configurar seu aplicativo para tirar proveito dele.</span><span class="sxs-lookup"><span data-stu-id="32bdc-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="32bdc-111">Configuração do aplicativo do Windows Forms para suporte a alto DPI</span><span class="sxs-lookup"><span data-stu-id="32bdc-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="32bdc-112">Os novos recursos do Windows Forms que dão suporte ao reconhecimento DPI alto estão disponíveis apenas em aplicativos que o .NET Framework 4.7 de destino e estão em execução em sistemas operacionais Windows com a atualização de criadores do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="32bdc-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span> 

<span data-ttu-id="32bdc-113">Além disso, para configurar o suporte DPI alto em seu aplicativo de formulários do Windows, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="32bdc-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="32bdc-114">Declare a compatibilidade com o Windows 10.</span><span class="sxs-lookup"><span data-stu-id="32bdc-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="32bdc-115">Para fazer isso, adicione o seguinte arquivo de manifesto:</span><span class="sxs-lookup"><span data-stu-id="32bdc-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="32bdc-116">Habilitar o reconhecimento DPI por monitor no *App. config* arquivo.</span><span class="sxs-lookup"><span data-stu-id="32bdc-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="32bdc-117">Windows Forms apresenta um novo [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) elemento para dar suporte a novos recursos e as personalizações adicionadas começando com o .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="32bdc-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="32bdc-118">Para tirar proveito dos novos recursos que oferecem suporte a alto DPI, adicione o seguinte arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="32bdc-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > <span data-ttu-id="32bdc-119">Nas versões anteriores do .NET Framework, você usou o manifesto para adicionar suporte a alto DPI.</span><span class="sxs-lookup"><span data-stu-id="32bdc-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="32bdc-120">Essa abordagem não é recomendada, pois ela substitui as configurações definidas no arquivo App. config.</span><span class="sxs-lookup"><span data-stu-id="32bdc-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>
   
- <span data-ttu-id="32bdc-121">Chamar estático <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método.</span><span class="sxs-lookup"><span data-stu-id="32bdc-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>
   
  <span data-ttu-id="32bdc-122">Isso deve ser a primeira chamada de método no seu ponto de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="32bdc-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="32bdc-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="32bdc-123">For example:</span></span>
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="32bdc-124">Recusando recursos individuais de DPI alto</span><span class="sxs-lookup"><span data-stu-id="32bdc-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="32bdc-125">Definindo o `DpiAwareness` valor `PerMonitorV2` permite alta de todos os recursos de reconhecimento DPI compatíveis com versões do .NET Framework começando com o .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="32bdc-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="32bdc-126">Normalmente, isso é adequado para a maioria dos aplicativos de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="32bdc-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="32bdc-127">No entanto, você talvez queira recusar uma ou mais recursos individuais.</span><span class="sxs-lookup"><span data-stu-id="32bdc-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="32bdc-128">O motivo mais importante para fazer isso é que o código do aplicativo existente já trata esse recurso.</span><span class="sxs-lookup"><span data-stu-id="32bdc-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="32bdc-129">Por exemplo, se seu aplicativo manipula AutoEscala, convém desabilitar o recurso de redimensionamento automático da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="32bdc-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

<span data-ttu-id="32bdc-130">Para obter uma lista de chaves individuais e seus valores, consulte [adicionar elemento de configuração de formulários do Windows](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="32bdc-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="32bdc-131">Novos eventos de alteração DPI</span><span class="sxs-lookup"><span data-stu-id="32bdc-131">New DPI change events</span></span>

<span data-ttu-id="32bdc-132">Começando com o .NET Framework 4.7, três novos eventos permitem manipular programaticamente alterações dinâmicas de DPI:</span><span class="sxs-lookup"><span data-stu-id="32bdc-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="32bdc-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, que é disparado quando a configuração de DPI para um controle é alterada de forma programática após um evento de alteração DPI para seu controle pai ou ao formulário.</span><span class="sxs-lookup"><span data-stu-id="32bdc-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="32bdc-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, que é disparado quando a configuração de DPI para um controle é alterada de forma programática antes de um evento de alteração DPI para seu controle pai ou ao formulário.</span><span class="sxs-lookup"><span data-stu-id="32bdc-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="32bdc-135"><xref:System.Windows.Forms.Form.DpiChanged>, que é disparado quando a configuração de DPI é alterado no dispositivo de exibição em que o formulário é exibido no momento.</span><span class="sxs-lookup"><span data-stu-id="32bdc-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="32bdc-136">Propriedades e métodos de auxiliar novo</span><span class="sxs-lookup"><span data-stu-id="32bdc-136">New helper methods and properties</span></span>

<span data-ttu-id="32bdc-137">O .NET Framework 4.7 também adiciona um número de novos métodos auxiliares e propriedades que fornecem informações sobre o dimensionamento de DPI e permitem que você execute o dimensionamento de DPI.</span><span class="sxs-lookup"><span data-stu-id="32bdc-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="32bdc-138">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="32bdc-138">These include:</span></span>

- <span data-ttu-id="32bdc-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, que converte um valor de lógica em pixels do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="32bdc-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="32bdc-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, que dimensiona uma imagem de bitmap para o DPI lógico para um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="32bdc-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="32bdc-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, que retorna o DPI do dispositivo atual.</span><span class="sxs-lookup"><span data-stu-id="32bdc-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="32bdc-142">Considerações sobre o controle de versão</span><span class="sxs-lookup"><span data-stu-id="32bdc-142">Versioning considerations</span></span>

<span data-ttu-id="32bdc-143">Além de executar no .NET Framework 4.7 e criadores de atualização do Windows 10, também pode executar seu aplicativo em um ambiente no qual ele não é compatível com melhorias de DPI alto.</span><span class="sxs-lookup"><span data-stu-id="32bdc-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="32bdc-144">Nesse caso, você precisará desenvolver um fallback para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="32bdc-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="32bdc-145">Você pode fazer isso para executar [desenho personalizado](./controls/user-drawn-controls.md) para manipular o dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="32bdc-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="32bdc-146">Para fazer isso, você também precisa determinar o sistema operacional no qual o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="32bdc-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="32bdc-147">Você pode fazer isso com o código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="32bdc-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="32bdc-148">Observe que seu aplicativo com êxito não detecta o Windows 10 se ele não estava listado como um sistema operacional com suporte no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="32bdc-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="32bdc-149">Você também pode verificar a versão do .NET Framework que o aplicativo foi compilado com:</span><span class="sxs-lookup"><span data-stu-id="32bdc-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="32bdc-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32bdc-150">See also</span></span>

[<span data-ttu-id="32bdc-151">Windows Forms adicionar elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="32bdc-151">Windows Forms Add Configuration Element</span></span>](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[<span data-ttu-id="32bdc-152">Ajustando o tamanho e a escala dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="32bdc-152">Adjusting the Size and Scale of Windows Forms</span></span>](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)

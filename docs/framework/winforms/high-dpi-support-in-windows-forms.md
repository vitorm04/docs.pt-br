---
title: Suporte a alto DPI no Windows Forms
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: f9183b15da24f70b6fceaa90f718c5af93a3cdda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139071"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="933ef-102">Suporte a alto DPI no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="933ef-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="933ef-103">A partir do .NET Framework 4,7, Windows Forms inclui aprimoramentos para cenários comuns de dpi e DPI dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="933ef-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="933ef-104">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="933ef-104">These include:</span></span>

- <span data-ttu-id="933ef-105">Melhorias no dimensionamento e layout de vários controles de Windows Forms, como o controle de <xref:System.Windows.Forms.MonthCalendar> e o controle de <xref:System.Windows.Forms.CheckedListBox>.</span><span class="sxs-lookup"><span data-stu-id="933ef-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span>

- <span data-ttu-id="933ef-106">Escala de passagem única.</span><span class="sxs-lookup"><span data-stu-id="933ef-106">Single-pass scaling.</span></span>  <span data-ttu-id="933ef-107">No .NET Framework 4,6 e versões anteriores, o dimensionamento foi realizado por meio de várias passagens, o que fazia com que alguns controles fosse escalado mais do que o necessário.</span><span class="sxs-lookup"><span data-stu-id="933ef-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="933ef-108">Suporte para cenários de DPI dinâmico em que o usuário altera o fator de escala ou DPI depois que um aplicativo de Windows Forms foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="933ef-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="933ef-109">Nas versões do .NET Framework a partir do .NET Framework 4,7, o suporte a alto DPI avançado é um recurso opcional.</span><span class="sxs-lookup"><span data-stu-id="933ef-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="933ef-110">Você deve configurar seu aplicativo para tirar proveito dele.</span><span class="sxs-lookup"><span data-stu-id="933ef-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="933ef-111">Configurando seu aplicativo Windows Forms para suporte a alto DPI</span><span class="sxs-lookup"><span data-stu-id="933ef-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="933ef-112">Os novos recursos Windows Forms que dão suporte a reconhecimento de DPI alta estão disponíveis somente em aplicativos direcionados para o .NET Framework 4,7 e estão em execução em sistemas operacionais Windows, começando com a atualização do Windows 10 para criadores.</span><span class="sxs-lookup"><span data-stu-id="933ef-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span>

<span data-ttu-id="933ef-113">Além disso, para configurar o suporte de DPI alto no seu aplicativo Windows Forms, você deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="933ef-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="933ef-114">Declare a compatibilidade com o Windows 10.</span><span class="sxs-lookup"><span data-stu-id="933ef-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="933ef-115">Para fazer isso, adicione o seguinte ao seu arquivo de manifesto:</span><span class="sxs-lookup"><span data-stu-id="933ef-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="933ef-116">Habilite o reconhecimento de DPI por monitor no arquivo *app. config* .</span><span class="sxs-lookup"><span data-stu-id="933ef-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="933ef-117">Windows Forms introduz um novo elemento [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) para dar suporte a novos recursos e personalizações adicionadas a partir do .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="933ef-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="933ef-118">Para aproveitar os novos recursos que dão suporte a DPI alto, adicione o seguinte ao arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="933ef-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > <span data-ttu-id="933ef-119">Nas versões anteriores do .NET Framework, você usou o manifesto para adicionar suporte a DPI alto.</span><span class="sxs-lookup"><span data-stu-id="933ef-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="933ef-120">Essa abordagem não é mais recomendada, já que ela substitui as configurações definidas no arquivo app. config.</span><span class="sxs-lookup"><span data-stu-id="933ef-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>

- <span data-ttu-id="933ef-121">Chame o método de <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> estático.</span><span class="sxs-lookup"><span data-stu-id="933ef-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>

  <span data-ttu-id="933ef-122">Deve ser a primeira chamada de método no ponto de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="933ef-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="933ef-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="933ef-123">For example:</span></span>

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="933ef-124">Recusando recursos de DPI alta individuais</span><span class="sxs-lookup"><span data-stu-id="933ef-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="933ef-125">Definir o valor de `DpiAwareness` como `PerMonitorV2` habilita todos os recursos de reconhecimento de DPI alto suportados pelas versões .NET Framework começando com o .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="933ef-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="933ef-126">Normalmente, isso é adequado para a maioria dos aplicativos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="933ef-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="933ef-127">No entanto, talvez você queira recusar um ou mais recursos individuais.</span><span class="sxs-lookup"><span data-stu-id="933ef-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="933ef-128">O motivo mais importante para fazer isso é que o código do aplicativo existente já lida com esse recurso.</span><span class="sxs-lookup"><span data-stu-id="933ef-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="933ef-129">Por exemplo, se seu aplicativo lida com o dimensionamento automático, talvez você queira desabilitar o recurso de redimensionamento automático da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="933ef-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

<span data-ttu-id="933ef-130">Para obter uma lista de chaves individuais e seus valores, consulte [Windows Forms adicionar elemento de configuração](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="933ef-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="933ef-131">Novos eventos de alteração de DPI</span><span class="sxs-lookup"><span data-stu-id="933ef-131">New DPI change events</span></span>

<span data-ttu-id="933ef-132">A partir do .NET Framework 4,7, três novos eventos permitem que você manipule programaticamente alterações de DPI dinâmicas:</span><span class="sxs-lookup"><span data-stu-id="933ef-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="933ef-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, que é disparado quando a configuração de DPI de um controle é alterada programaticamente após um evento de alteração de DPI para o controle pai ou formulário ter ocorrido.</span><span class="sxs-lookup"><span data-stu-id="933ef-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="933ef-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, que é acionado quando a configuração de DPI de um controle é alterada programaticamente antes de um evento de alteração de DPI para seu controle pai ou formulário ter ocorrido.</span><span class="sxs-lookup"><span data-stu-id="933ef-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="933ef-135"><xref:System.Windows.Forms.Form.DpiChanged>, que é disparado quando a configuração de DPI é alterada no dispositivo de vídeo onde o formulário está atualmente exibido.</span><span class="sxs-lookup"><span data-stu-id="933ef-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="933ef-136">Novos métodos auxiliares e propriedades</span><span class="sxs-lookup"><span data-stu-id="933ef-136">New helper methods and properties</span></span>

<span data-ttu-id="933ef-137">O .NET Framework 4,7 também adiciona uma série de novos métodos auxiliares e propriedades que fornecem informações sobre o dimensionamento de DPI e permitem que você execute o dimensionamento de DPI.</span><span class="sxs-lookup"><span data-stu-id="933ef-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="933ef-138">Elas incluem:</span><span class="sxs-lookup"><span data-stu-id="933ef-138">These include:</span></span>

- <span data-ttu-id="933ef-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, que converte um valor dos pixels lógicos para de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="933ef-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="933ef-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, que dimensiona uma imagem de bitmap para o DPI lógico de um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="933ef-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="933ef-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, que retorna o DPI para o dispositivo atual.</span><span class="sxs-lookup"><span data-stu-id="933ef-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="933ef-142">Considerações sobre controle de versão</span><span class="sxs-lookup"><span data-stu-id="933ef-142">Versioning considerations</span></span>

<span data-ttu-id="933ef-143">Além de ser executado na atualização do .NET Framework 4,7 e do Windows 10 para criadores, seu aplicativo também pode ser executado em um ambiente no qual não é compatível com melhorias de DPI alto.</span><span class="sxs-lookup"><span data-stu-id="933ef-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="933ef-144">Nesse caso, você precisará desenvolver um fallback para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="933ef-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="933ef-145">Você pode fazer isso para executar o [desenho personalizado](./controls/user-drawn-controls.md) para lidar com o dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="933ef-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="933ef-146">Para fazer isso, você também precisa determinar o sistema operacional no qual seu aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="933ef-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="933ef-147">Você pode fazer isso com um código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="933ef-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="933ef-148">Observe que seu aplicativo não detectará com êxito o Windows 10 se ele não estiver listado como um sistema operacional com suporte no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="933ef-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="933ef-149">Você também pode verificar a versão do .NET Framework em que o aplicativo foi criado:</span><span class="sxs-lookup"><span data-stu-id="933ef-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="933ef-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="933ef-150">See also</span></span>

- [<span data-ttu-id="933ef-151">Windows Forms adicionar elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="933ef-151">Windows Forms Add Configuration Element</span></span>](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="933ef-152">Ajustando o tamanho e a escala dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="933ef-152">Adjusting the Size and Scale of Windows Forms</span></span>](adjusting-the-size-and-scale-of-windows-forms.md)

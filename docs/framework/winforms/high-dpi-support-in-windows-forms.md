---
title: Suporte para DPI alto nos Windows Forms
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1641702c7b1c3d3b0e83c59a96529de70f699d17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966921"
---
# <a name="high-dpi-support-in-windows-forms"></a>Suporte para DPI alto nos Windows Forms

Começando com o .NET Framework 4.7, o Windows Forms inclui aprimoramentos para DPI alto comuns e cenários DPI dinâmicos. Elas incluem:

- Controles de melhorias no dimensionamento e layout de um número de formulários do Windows, como o <xref:System.Windows.Forms.MonthCalendar> controle e o <xref:System.Windows.Forms.CheckedListBox> controle.

- Passagem única escala.  No .NET Framework 4.6 e versões anteriores, o dimensionamento foi executado por meio de várias passagens, o que causou alguns controles sejam escalonados de mais do que era necessário.

- Suporte para cenários DPI dinâmicos em que o usuário altera o fator de escala de DPI após um aplicativo do Windows Forms foi iniciado.

Nas versões do .NET Framework começando com o .NET Framework 4.7, suporte para DPI alto aprimorado é um recurso de aceitação. Você deve configurar seu aplicativo para tirar proveito dela.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Configurar um aplicativo Windows Forms para suporte ao DPI alto

Os novos recursos do Windows Forms que dão suporte ao reconhecimento de DPI alta estão disponíveis somente em aplicativos que se destinam ao .NET Framework 4.7 e estão em execução em sistemas operacionais Windows com o Windows 10 Creators Update.

Além disso, para configurar o suporte para DPI alto no seu aplicativo de formulários do Windows, você deve fazer o seguinte:

- Declare a compatibilidade com o Windows 10.

  Para fazer isso, adicione o seguinte ao seu arquivo de manifesto:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- Habilitar o reconhecimento de DPI por monitor na *App. config* arquivo.

  Windows Forms apresenta uma nova [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../configure-apps/file-schema/winforms/index.md) elemento para oferecer suporte a novos recursos e as personalizações adicionadas começando com o .NET Framework 4.7. Para tirar proveito dos novos recursos que dão suporte a DPI alta, adicione o seguinte ao arquivo de configuração de aplicativo.

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > Nas versões anteriores do .NET Framework, você usou o manifesto para adicionar suporte a alto DPI. Essa abordagem não é mais recomendada, já que ela substitui as configurações definidas no arquivo App. config.

- Chamar estático <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método.

  Isso deve ser a primeira chamada de método em seu ponto de entrada do aplicativo. Por exemplo:

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Recusando a recursos individuais de alto DPI

Definindo o `DpiAwareness` valor `PerMonitorV2` permite alta de todos os recursos de reconhecimento DPI compatíveis com versões do .NET Framework começando com o .NET Framework 4.7. Normalmente, isso é adequado para a maioria dos aplicativos de formulários do Windows. No entanto, você talvez queira recusar um ou mais recursos individuais. O motivo mais importante para fazer isso é que o código do aplicativo existente já lida com esse recurso.  Por exemplo, se seu aplicativo lida com dimensionamento automático, você talvez queira desabilitar o recurso de redimensionamento automático da seguinte maneira:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

Para obter uma lista de chaves individuais e seus valores, consulte [adicionar elemento de configuração de formulários do Windows](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Novos eventos de alteração DPI

Começando com o .NET Framework 4.7, três novos eventos permitem manipular programaticamente as alterações DPI dinâmicas:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, que é acionado quando a configuração de DPI para um controle é alterada por meio de programação após um evento de alteração DPI para o controle pai ou formulário ocorreu.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, que é acionado quando a configuração de DPI para um controle é alterada por meio de programação antes de um evento de alteração DPI para o seu controle pai ou formulário.
- <xref:System.Windows.Forms.Form.DpiChanged>, que é disparado quando a configuração de DPI muda no dispositivo de vídeo em que o formulário está sendo exibido.

## <a name="new-helper-methods-and-properties"></a>Propriedades e novos métodos auxiliares

O .NET Framework 4.7 também adiciona um número de novos métodos de auxiliar e propriedades que fornecem informações sobre ajuste de DPI e permitem que você execute o ajuste de DPI. Elas incluem:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, que converte um valor de coordenadas lógicas em pixels do dispositivo.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, que dimensiona uma imagem de bitmap para o DPI lógico para um dispositivo.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, que retorna o DPI para o dispositivo atual.

## <a name="versioning-considerations"></a>Considerações sobre o controle de versão

Além de ser executado no .NET Framework 4.7 e Windows 10 Creators Update, seu aplicativo também pode ser executado em um ambiente no qual ele não é compatível com melhorias de DPI alta. Nesse caso, você precisará desenvolver um fallback para o seu aplicativo. Você pode fazer isso para realizar [desenho personalizado](./controls/user-drawn-controls.md) para manipular o dimensionamento.

Para fazer isso, você também precisa determinar o sistema operacional no qual o aplicativo é executado. Você pode fazer isso com código semelhante ao seguinte:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Observe que seu aplicativo não detecta com êxito o Windows 10 se ele não estava listado como um sistema operacional no manifesto do aplicativo.

Você também pode verificar a versão do .NET Framework que o aplicativo foi compilado:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Consulte também

- [Windows Forms adicionar elemento de configuração](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [Ajustando o tamanho e a escala dos Windows Forms](adjusting-the-size-and-scale-of-windows-forms.md)

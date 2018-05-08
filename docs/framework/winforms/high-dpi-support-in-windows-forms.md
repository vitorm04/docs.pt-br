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
ms.openlocfilehash: a085658579c8cd3ba43fd07a7816581e03c3d64a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="high-dpi-support-in-windows-forms"></a>Suporte a alto DPI no Windows Forms

Começando com o .NET Framework 4.7, formulários do Windows inclui aprimoramentos de alto DPI comuns e cenários DPI dinâmicos. Elas incluem: 

- Melhorias no layout de um número de formulários do Windows e dimensionando controles, como o <xref:System.Windows.Forms.MonthCalendar> controle e o <xref:System.Windows.Forms.CheckedListBox> controle. 

- Passagem única escala.  No .NET Framework 4.6 e versões anteriores, o dimensionamento foi realizada por meio de várias passagens, o que causou alguns controles será dimensionada mais do que era necessária.

- Suporte para cenários DPI dinâmicos no qual o usuário altera o fator de escala ou DPI depois que um aplicativo Windows Forms foi iniciado.

Nas versões do .NET Framework, começando com o .NET Framework 4.7, suporte aprimorado de alto DPI é um recurso de aceitação. Você deve configurar seu aplicativo para tirar proveito dele.

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>Configuração do aplicativo do Windows Forms para suporte a alto DPI

Os novos recursos do Windows Forms que dão suporte ao reconhecimento DPI alto estão disponíveis apenas em aplicativos que o .NET Framework 4.7 de destino e estão em execução em sistemas operacionais Windows com a atualização de criadores do Windows 10. 

Além disso, para configurar o suporte DPI alto em seu aplicativo de formulários do Windows, faça o seguinte:

- Declare a compatibilidade com o Windows 10.

  Para fazer isso, adicione o seguinte arquivo de manifesto:

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.comn:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- Habilitar o reconhecimento DPI por monitor no *App. config* arquivo.

  Windows Forms apresenta um novo [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) elemento para dar suporte a novos recursos e as personalizações adicionadas começando com o .NET Framework 4.7. Para tirar proveito dos novos recursos que oferecem suporte a alto DPI, adicione o seguinte arquivo de configuração de aplicativo.   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > Nas versões anteriores do .NET Framework, você usou o manifesto para adicionar suporte a alto DPI. Essa abordagem não é recomendada, pois ela substitui as configurações definidas no arquivo App. config.
   
- Chamar estático <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método.
   
  Isso deve ser a primeira chamada de método no seu ponto de entrada do aplicativo. Por exemplo:
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>Recusando recursos individuais de DPI alto

Definindo o `DpiAwareness` valor `PerMonitorV2` permite alta de todos os recursos de reconhecimento DPI compatíveis com versões do .NET Framework começando com o .NET Framework 4.7. Normalmente, isso é adequado para a maioria dos aplicativos de formulários do Windows. No entanto, você talvez queira recusar uma ou mais recursos individuais. O motivo mais importante para fazer isso é que o código do aplicativo existente já trata esse recurso.  Por exemplo, se seu aplicativo manipula AutoEscala, convém desabilitar o recurso de redimensionamento automático da seguinte maneira:

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

Para obter uma lista de chaves individuais e seus valores, consulte [adicionar elemento de configuração de formulários do Windows](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).

## <a name="new-dpi-change-events"></a>Novos eventos de alteração DPI

Começando com o .NET Framework 4.7, três novos eventos permitem manipular programaticamente alterações dinâmicas de DPI:

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, que é disparado quando a configuração de DPI para um controle é alterada de forma programática após um evento de alteração DPI para seu controle pai ou ao formulário.
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, que é disparado quando a configuração de DPI para um controle é alterada de forma programática antes de um evento de alteração DPI para seu controle pai ou ao formulário.
- <xref:System.Windows.Forms.Form.DpiChanged>, que é disparado quando a configuração de DPI é alterado no dispositivo de exibição em que o formulário é exibido no momento.

## <a name="new-helper-methods-and-properties"></a>Propriedades e métodos de auxiliar novo

O .NET Framework 4.7 também adiciona um número de novos métodos auxiliares e propriedades que fornecem informações sobre o dimensionamento de DPI e permitem que você execute o dimensionamento de DPI. Elas incluem:

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, que converte um valor de lógica em pixels do dispositivo.

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, que dimensiona uma imagem de bitmap para o DPI lógico para um dispositivo.

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>, que retorna o DPI do dispositivo atual.

## <a name="versioning-considerations"></a>Considerações sobre o controle de versão

Além de executar no .NET Framework 4.7 e criadores de atualização do Windows 10, também pode executar seu aplicativo em um ambiente no qual ele não é compatível com melhorias de DPI alto. Nesse caso, você precisará desenvolver um fallback para o seu aplicativo. Você pode fazer isso para executar [desenho personalizado](./controls/user-drawn-controls.md) para manipular o dimensionamento.

Para fazer isso, você também precisa determinar o sistema operacional no qual o aplicativo está em execução. Você pode fazer isso com o código semelhante ao seguinte:

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

Observe que seu aplicativo com êxito não detecta o Windows 10 se ele não estava listado como um sistema operacional com suporte no manifesto do aplicativo.

Você também pode verificar a versão do .NET Framework que o aplicativo foi compilado com:

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>Consulte também

[Windows Forms adicionar elemento de configuração](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[Ajustando o tamanho e a escala dos Windows Forms](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)

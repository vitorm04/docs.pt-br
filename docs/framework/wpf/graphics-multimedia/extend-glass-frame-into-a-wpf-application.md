---
title: Estender quadro com efeito de transparência em um aplicativo WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
ms.openlocfilehash: a702456895cfdbd44a58059befefb69deee5afa3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636192"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Estender quadro com efeito de transparência em um aplicativo WPF

Este tópico demonstra como estender o quadro de vidro do Windows Vista para a área do cliente de um aplicativo Windows Presentation Foundation (WPF).

> [!NOTE]
> Este exemplo só funcionará em um computador com Windows Vista executando o Gerenciador de Janelas da Área de Trabalho (DWM) com o vidro habilitado. O Windows Vista Home Basic Edition não dá suporte ao efeito de vidro transparente. As áreas que normalmente renderizariam com o efeito de vidro transparente em outras edições do Windows Vista são processadas de forma opaca.

## <a name="example"></a>Exemplo

A imagem a seguir ilustra o quadro de vidro estendido na barra de endereços do Internet Explorer 7:

![Captura de tela mostrando o quadro de vidro estendido atrás da barra de endereços do IE7.](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

Para estender o quadro de vidro em um aplicativo do WPF, é necessário o acesso à API não gerenciada. O exemplo de código a seguir faz uma invocação de plataforma (PInvoke) para as duas APIs necessárias para estender o quadro para a área do cliente. Cada uma dessas APIs é declarada em uma classe chamada **NonClientRegionAPI**.

```csharp
[StructLayout(LayoutKind.Sequential)]
public struct MARGINS
{
    public int cxLeftWidth;      // width of left border that retains its size
    public int cxRightWidth;     // width of right border that retains its size
    public int cyTopHeight;      // height of top border that retains its size
    public int cyBottomHeight;   // height of bottom border that retains its size
};

[DllImport("DwmApi.dll")]
public static extern int DwmExtendFrameIntoClientArea(
    IntPtr hwnd,
    ref MARGINS pMarInset);
```

```vb
<StructLayout(LayoutKind.Sequential)>
Public Structure MARGINS
    Public cxLeftWidth As Integer ' width of left border that retains its size
    Public cxRightWidth As Integer ' width of right border that retains its size
    Public cyTopHeight As Integer ' height of top border that retains its size
    Public cyBottomHeight As Integer ' height of bottom border that retains its size
End Structure

<DllImport("DwmApi.dll")>
Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer
End Function
```

[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) é a função de DWM que estende o quadro para a área de cliente. Ela recebe dois parâmetros: um identificador de janela e uma estrutura [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins). [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) é usado para instruir o DWM sobre quanto a mais o quadro deve ser estendido para a área de cliente.

## <a name="example"></a>Exemplo

Para usar a função [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea), é necessário obter um identificador de janela. No WPF, o identificador de janela pode ser obtido na propriedade <xref:System.Windows.Interop.HwndSource.Handle%2A> de um <xref:System.Windows.Interop.HwndSource>. No exemplo a seguir, o quadro é estendido para a área do cliente no evento <xref:System.Windows.FrameworkElement.Loaded> da janela.

```csharp
void OnLoaded(object sender, RoutedEventArgs e)
{
   try
   {
      // Obtain the window handle for WPF application
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);

      // Get System Dpi
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);
      float DesktopDpiX = desktop.DpiX;
      float DesktopDpiY = desktop.DpiY;

      // Set Margins
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();

      // Extend glass frame into client area
      // Note that the default desktop Dpi is 96dpi. The  margins are
      // adjusted for the system Dpi.
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));

      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);
      //
      if (hr < 0)
      {
         //DwmExtendFrameIntoClientArea Failed
      }
   }
   // If not Vista, paint background white.
   catch (DllNotFoundException)
   {
      Application.Current.MainWindow.Background = Brushes.White;
   }
}
```

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma janela simples em que o quadro é estendido para a área de cliente. O quadro é estendido para trás da borda superior que contém os dois objetos <xref:System.Windows.Controls.TextBox>.

```xaml
<Window x:Class="SDKSample.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Extended Glass in WPF" Height="300" Width="400"
    Loaded="OnLoaded" Background="Transparent"
    >
  <Grid ShowGridLines="True">
    <DockPanel Name="mainDock">
      <!-- The border is used to compute the rendered height with margins.
           topBar contents will be displayed on the extended glass frame.-->
      <Border Name="topBar" DockPanel.Dock="Top" >
        <Grid Name="grid">
          <Grid.ColumnDefinitions>
            <ColumnDefinition MinWidth="100" Width="*"/>
            <ColumnDefinition Width="Auto"/>
          </Grid.ColumnDefinitions>
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>
        </Grid>
      </Border>
      <Grid DockPanel.Dock="Top" >
        <Grid.ColumnDefinitions>
          <ColumnDefinition/>
        </Grid.ColumnDefinitions>
        <TextBox Grid.Column="0" AcceptsReturn="True"/>
      </Grid>
    </DockPanel>
  </Grid>
</Window>
```

A imagem a seguir ilustra o quadro de vidro estendido em um aplicativo WPF:

![Captura de tela mostrando um quadro de vidro estendido em um aplicativo WPF.](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a>Veja também

- [Visão geral de Gerenciador de Janelas da Área de Trabalho](/windows/desktop/dwm/dwm-overview)
- [Visão geral do Desfoque Gerenciador de Janelas da Área de Trabalho](/windows/desktop/dwm/blur-ovw)
- [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)

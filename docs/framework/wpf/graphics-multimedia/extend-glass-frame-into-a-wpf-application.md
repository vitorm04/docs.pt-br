---
title: "Estender quadro com efeito de transparência em um aplicativo WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aad070bca408fc608eb000948c1b942d08f02018
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Estender quadro com efeito de transparência em um aplicativo WPF
Este tópico demonstra como estender o quadro com efeito de transparência do [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] para a área de cliente de um aplicativo [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
> [!NOTE]
>  Este exemplo só funcionará em um computador [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] que executa o DWM (Gerenciador de Janelas da Área de Trabalho) com efeito de transparência habilitado. O [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Home Basic edition não dá suporte ao efeito de transparência. Áreas que normalmente seriam renderizadas com efeito de transparência nas outras edições do [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] são renderizadas opacas.  
  
## <a name="example"></a>Exemplo  
 A imagem a seguir ilustra o quadro com efeito de transparência estendido na barra de endereços do Internet Explorer 7.  
  
 **Internet Explorer com quadro com efeito de transparência estendido atrás da barra de endereços.**  
  
 ![IE7 com quadro com efeito de transparência estendido por trás da barra de endereços.](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")  
  
 Para estender o quadro com efeito de transparência em um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], é necessário obter acesso ao [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] não gerenciado. O exemplo de código a seguir faz uma invocação de plataforma (pinvoke) para os dois [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] necessários para estender o quadro para a área de cliente. Cada um desses [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] são declarados em uma classe chamada **NonClientRegionAPI**.  
  
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
  
 [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) é a função de DWM que estende o quadro para a área de cliente. Ela recebe dois parâmetros: um identificador de janela e uma estrutura [MARGINS](https://msdn.microsoft.com/library/bb773244.aspx). [MARGINS](https://msdn.microsoft.com/library/bb773244.aspx) é usado para instruir o DWM sobre quanto a mais o quadro deve ser estendido para a área de cliente.  
  
## <a name="example"></a>Exemplo  
 Para usar a função [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx), é necessário obter um identificador de janela. Em [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], o identificador de janela pode ser obtido o <xref:System.Windows.Interop.HwndSource.Handle%2A> propriedade de um <xref:System.Windows.Interop.HwndSource>. No exemplo a seguir, o quadro é estendido para a área cliente sobre o <xref:System.Windows.FrameworkElement.Loaded> eventos da janela.  
  
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
 O exemplo a seguir mostra uma janela simples em que o quadro é estendido para a área de cliente. O quadro é estendido por trás da borda superior que contém os dois <xref:System.Windows.Controls.TextBox> objetos.  
  
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
  
 A imagem a seguir ilustra o quadro com efeito de transparência estendido em um aplicativo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 **Quadro com efeito de transparência estendido para um**  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  **aplicativo.**  
  
 ![Quadro com efeito de transparência estendido em um aplicativo WPF.](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do Gerenciador de janelas da área de trabalho](https://msdn.microsoft.com/library/aa969540.aspx)  
 [Visão geral do Gerenciador de janelas da área de trabalho Desfoque](https://msdn.microsoft.com/library/aa969537.aspx)  
 [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx)

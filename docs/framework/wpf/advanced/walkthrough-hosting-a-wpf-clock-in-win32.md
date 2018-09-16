---
title: 'Instruções passo a passo: hospedando um relógio do WPF em Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: ce8209c89430988f57c211d388c6e73b2dc17004
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674540"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Instruções passo a passo: hospedando um relógio do WPF em Win32
Para colocar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativos, usam <xref:System.Windows.Interop.HwndSource>, que fornece o HWND que contém seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo. Primeiro, você cria o <xref:System.Windows.Interop.HwndSource>, dando a ele parâmetros semelhantes a CreateWindow.  Em seguida, você informa o <xref:System.Windows.Interop.HwndSource> sobre o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo que você deseja dentro dele.  Finalmente, você obtém o HWND do <xref:System.Windows.Interop.HwndSource>. Este passo a passo ilustra como criar um misto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo que reimplementa o sistema operacional **Date and Time Properties** caixa de diálogo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Consulte [Interoperação Win32 e WPF](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="how-to-use-this-tutorial"></a>Como usar esse tutorial  
 Este tutorial mostra as etapas importantes de produção de um aplicativo de interoperação. O tutorial é feito por uma amostra [exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051), mas esse exemplo é reflete o produto final. Este tutorial documenta as etapas como se você estivesse iniciando com um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto de sua preferência, talvez um projeto pré-existente e você estivesse adicionando hospedado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ao seu aplicativo. Você pode comparar seu produto final com [exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Um passo a passo do Windows Presentation Framework no Win32 (HwndSource)  
 O gráfico a seguir mostra o produto final desejado deste tutorial:  
  
 ![Caixa de diálogo Propriedades de Data e Hora](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")  
  
 Você pode recriar esta caixa de diálogo com a criação de C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project no [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]e usando o editor de caixa de diálogo para criar o seguinte:  
  
 ![Caixa de diálogo Propriedades de Data e Hora](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")  
  
 (Não é necessário usar [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] usar <xref:System.Windows.Interop.HwndSource>, e você não precisará usar C++ para escrever [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programas, mas isso é uma maneira bastante comum de fazê-lo e funciona bem para uma explicação do tutorial em passos).  
  
 Você precisa realizar cinco subpassos para colocar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio na caixa de diálogo:  
  
1.  Habilitar seu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto para chamar código gerenciado (**/clr**) alterando as configurações de projeto no [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
2.  Criar uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> em uma DLL separada.  
  
3.  Colocar isso [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> dentro de um <xref:System.Windows.Interop.HwndSource>.  
  
4.  Obtenha um HWND para que <xref:System.Windows.Controls.Page> usando o <xref:System.Windows.Interop.HwndSource.Handle%2A> propriedade.  
  
5.  Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] para decidir onde colocar a HWND dentro maior [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo  
  
## <a name="clr"></a>/clr  
 A primeira etapa é transformar esse unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto em um que pode chamar o código gerenciado.  Você usa a opção de compilador /clr, que vinculará as DLLs necessárias que você deseja usar e ajustará o método principal para uso com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Para habilitar o uso de código gerenciado dentro do projeto C++: clique com botão direito no projeto win32clock e selecione **propriedades**.  Sobre o **gerais** página de propriedades (o padrão), altere o suporte a Common Language Runtime para `/clr`.  
  
 Em seguida, adicionar referências às DLLs necessárias para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll e UIAutomationTypes. dll. (Seguir as instruções pressupõe que o sistema operacional está instalado na unidade C:.)  
  
1.  Clique em projeto win32clock e selecione **referências...** e dentro desse diálogo:  
  
2.  Clique em projeto win32clock e selecione **referências...** .  
  
3.  Clique em **adicionar nova referência**, clique na guia Procurar, digite C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll e clique em Okey.  
  
4.  Repita para PresentationFramework.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\PresentationFramework.dll.  
  
5.  Repita para WindowsBase.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\WindowsBase.dll.  
  
6.  Repita para UIAutomationTypes.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\UIAutomationTypes.dll.  
  
7.  Repita para UIAutomationProvider.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\UIAutomationProvider.dll.  
  
8.  Clique em **adicionar nova referência**, selecione System. dll e clique em **Okey**.  
  
9. Clique em **Okey** para as páginas de propriedades do win32clock para adicionar referências de saída.  
  
 Por fim, adicione a `STAThreadAttribute` para o `_tWinMain` método para uso com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 Esse atributo instrui o [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] que quando ele inicializa [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], ele deve usar um modelo de compartimento de único thread (STA), que é necessário para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).  
  
## <a name="create-a-windows-presentation-framework-page"></a>Criar uma página do Windows Presentation Framework  
 Em seguida, crie uma DLL que define uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>. Geralmente é mais fácil criar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> como um aplicativo autônomo e a gravação e a depuração de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] parte dessa forma.  Depois disso, o que o projeto pode ser convertido em uma DLL clicando com o projeto, clicando em **propriedades**, indo para o aplicativo e alterar o tipo de saída para a biblioteca de classes do Windows.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projeto de dll, em seguida, pode ser combinado com o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto (uma solução que contém dois projetos) – clique com o botão direito na solução, selecione **Adicionar\projeto**.  
  
 Para usá-la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto, você precisa adicionar uma referência:  
  
1.  Clique em projeto win32clock e selecione **referências...** .  
  
2.  Clique em **adicionar nova referência**.  
  
3.  Clique na guia **Projetos**.  Selecione WPFClock, clique em OK.  
  
4.  Clique em **Okey** para as páginas de propriedades do win32clock para adicionar referências de saída.  
  
## <a name="hwndsource"></a>HwndSource  
 Em seguida, use <xref:System.Windows.Interop.HwndSource> para fazer a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> se parecer com um HWND.  Você adiciona este bloco de código a um arquivo C++:  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
  
    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
        HwndSource^ source = gcnew HwndSource(  
            0, // class style  
            WS_VISIBLE | WS_CHILD, // style  
            0, // exstyle  
            x, y, width, height,  
            "hi", // NAME  
            IntPtr(parent)        // parent window   
            );  
  
        UIElement^ page = gcnew WPFClock::Clock();  
        source->RootVisual = page;  
        return (HWND) source->Handle.ToPointer();  
    }  
}  
}  
```  
  
 Esse é uma parte grande do código que poderia ser explicada.  A primeira parte é composta por várias cláusulas para que você não precise qualificar totalmente todas as chamadas:  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 Em seguida, você define uma função que cria o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de conteúdo, coloca um <xref:System.Windows.Interop.HwndSource> ao redor e retorna o HWND:  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 Primeiro, você cria um <xref:System.Windows.Interop.HwndSource>, cujos parâmetros são semelhantes do CreateWindow:  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 Em seguida, você cria o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classe de conteúdo chamando seu construtor:  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 Em seguida, conecte-se a página para o <xref:System.Windows.Interop.HwndSource>:  
  
```  
source->RootVisual = page;  
```  
  
 E na linha final, retorne o HWND para o <xref:System.Windows.Interop.HwndSource>:  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a>Posicionamento do Hwnd  
 Agora que você tem um HWND que contém o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio, você precisará colocar esse HWND dentro de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] caixa de diálogo.  Se você soubesse onde colocar a HWND, você apenas passaria tamanho e o local para o `GetHwnd` função que você definiu anteriormente.  Mas você usou um arquivo de recurso para definir a caixa de diálogo, então não tem muita certeza sobre onde os HWNDs estão posicionados.  Você pode usar o [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] editor de caixa de diálogo para colocar uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] estático controlar onde você deseja que o relógio fique ("Inserir relógio aqui") e usá-lo para posicionar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio.  
  
 Lidar com WM_INITDIALOG, você usa `GetDlgItem` para recuperar o HWND para o espaço reservado STATIC:  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 Você, em seguida, calcula o tamanho e posição do espaço reservado STATIC, portanto, você pode colocar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio naquele local:  
  
 Retângulo RECT;  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 Em seguida, oculte o espaço reservado STATIC:  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 E crie o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio HWND neste local:  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 Para tornar o tutorial interessante e produzir um real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio, você precisará criar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neste ponto de controle de relógio. Você pode fazer isso basicamente na marcação, com apenas alguns manipuladores de eventos no code-behind. Como este tutorial é sobre a interoperação e não sobre design de controle, o código completo para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio é fornecido aqui como um bloco de código, sem instruções distintas para compilá-lo ou o que significa que cada parte. Fique à vontade para testar este código para alterar a aparência ou a funcionalidade do controle.  
  
 Aqui está a marcação:  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 E aqui está o code-behind que acompanha:  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 O resultado final se parece com:  
  
 ![Caixa de diálogo Propriedades de Data e Hora](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")  
  
 Para comparar seu resultado final com o código que produziu a captura de tela, consulte [exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Interop.HwndSource>  
 [Interoperação do WPF e do Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051)

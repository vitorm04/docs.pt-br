---
title: 'Instruções passo a passo: hospedando um relógio do WPF em Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 42ed51a1a1ce59b6a3cc3319d86d3a7445403ce4
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919738"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Instruções passo a passo: hospedando um relógio do WPF em Win32

Para colocar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro de aplicativos [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], use <xref:System.Windows.Interop.HwndSource>, que fornece o HWND que contém o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Primeiro, você cria o <xref:System.Windows.Interop.HwndSource>, dando a ele parâmetros semelhantes à CreateWindow. Em seguida, você informa o <xref:System.Windows.Interop.HwndSource> sobre o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que você deseja dentro dele. Por fim, você obtém o HWND fora do <xref:System.Windows.Interop.HwndSource>. Este tutorial ilustra como criar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] misto dentro de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo que reimplementa a caixa de diálogo **Propriedades de data e hora** do sistema operacional.

## <a name="prerequisites"></a>Prerequisites

Consulte [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md).

## <a name="how-to-use-this-tutorial"></a>Como usar esse tutorial

Este tutorial mostra as etapas importantes de produção de um aplicativo de interoperação. O tutorial é apoiado por um exemplo de exemplo de [interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051), mas esse exemplo é refletido do produto final. Este tutorial documenta as etapas como se você estivesse começando com um projeto [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] existente, talvez um projeto pré-existente, e estivesse adicionando um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedado ao seu aplicativo. Você pode comparar seu produto final com o [exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Um passo a passo do Windows Presentation Framework no Win32 (HwndSource)

O gráfico a seguir mostra o produto final desejado deste tutorial:

![Captura de tela que mostra a caixa de diálogo Propriedades de data e hora.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

Você pode recriar essa caixa de diálogo criando C++ um projeto Win32 no Visual Studio e usando o editor de caixa de diálogo para criar o seguinte:

![Caixa de diálogo Propriedades de data e hora recriadas](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(Você não precisa usar o Visual Studio para usar <xref:System.Windows.Interop.HwndSource>e não precisa usar C++ o para escrever[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]programas, mas essa é uma maneira bastante comum de fazer isso e se presta bem a uma explicação do tutorial do gradual).

Você precisa realizar cinco subetapas específicas para colocar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio na caixa de diálogo:

1. Habilite seu projeto de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] para chamar o código gerenciado ( **/CLR**) alterando as configurações do projeto no Visual Studio.

2. Crie um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> em uma DLL separada.

3. Coloque esse [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> dentro de um <xref:System.Windows.Interop.HwndSource>.

4. Obtenha um HWND para esse <xref:System.Windows.Controls.Page> usando a propriedade <xref:System.Windows.Interop.HwndSource.Handle%2A>.

5. Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] para decidir onde posicionar o HWND dentro do aplicativo de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] maior

## <a name="clr"></a>/clr

A primeira etapa é transformar esse projeto de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] não gerenciado em um que possa chamar código gerenciado. Você usa a opção de compilador/CLR, que será vinculada às DLLs necessárias que você deseja usar e ajustará o método Main para uso com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Para habilitar o uso de código gerenciado dentro do C++ projeto: clique com o botão direito do mouse no projeto win32clock e selecione **Propriedades**. Na página de propriedades **geral** (o padrão), altere o suporte ao Common Language Runtime para `/clr`.

Em seguida, adicione referências às DLLs necessárias para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll e UIAutomationTypes. dll. (Seguir as instruções pressupõe que o sistema operacional está instalado na unidade C:.)

1. Clique com o botão direito do mouse em projeto win32clock e selecione **referências...** e dentro dessa caixa de diálogo:

2. Clique com o botão direito do mouse em projeto win32clock e selecione **referências...** .

3. Clique em **Adicionar nova referência**, clique na guia procurar, digite C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll e clique em OK.

4. Repita para PresentationFramework.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\PresentationFramework.dll.

5. Repita para WindowsBase.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\WindowsBase.dll.

6. Repita para UIAutomationTypes.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\UIAutomationTypes.dll.

7. Repita para UIAutomationProvider.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\UIAutomationProvider.dll.

8. Clique em **Adicionar nova referência**, selecione System. dll e clique em **OK**.

9. Clique em **OK** para sair das páginas de propriedades win32clock para adicionar referências.

 Por fim, adicione o `STAThreadAttribute` ao método `_tWinMain` para uso com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Esse atributo informa ao Common Language Runtime (CLR) que quando ele é inicializado Component Object Model (COM), ele deve usar um STA (modelo de apartamento de thread único), que é necessário para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).

## <a name="create-a-windows-presentation-framework-page"></a>Criar uma página do Windows Presentation Framework

Em seguida, você cria uma DLL que define um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>. Geralmente, é mais fácil criar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> como um aplicativo autônomo e escrever e depurar a parte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dessa maneira. Depois de concluído, esse projeto pode ser transformado em uma DLL clicando com o botão direito do mouse no projeto, clicando em **Propriedades**, indo para o aplicativo e alterando o tipo de saída para a biblioteca de classes do Windows.

O projeto DLL [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode então ser combinado com o projeto [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] (uma solução que contém dois projetos) – clique com o botão direito do mouse na solução, selecione **projeto Add\Existing**.

Para usar essa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll do projeto [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], você precisa adicionar uma referência:

1. Clique com o botão direito do mouse em projeto win32clock e selecione **referências...** .

2. Clique em **Adicionar nova referência**.

3. Clique na guia **projetos** . Selecione WPFClock e clique em OK.

4. Clique em **OK** para sair das páginas de propriedades win32clock para adicionar referências.

## <a name="hwndsource"></a>HwndSource

Em seguida, você usa <xref:System.Windows.Interop.HwndSource> para fazer com que o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> seja semelhante a um HWND. Você adiciona este bloco de código a um arquivo C++:

```cpp
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

 Esse é uma parte grande do código que poderia ser explicada. A primeira parte é composta por várias cláusulas para que você não precise qualificar totalmente todas as chamadas:

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 Em seguida, você define uma função que cria o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], coloca um <xref:System.Windows.Interop.HwndSource> em volta dele e retorna o HWND:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

Primeiro, você cria uma <xref:System.Windows.Interop.HwndSource>, cujos parâmetros são semelhantes à CreateWindow:

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

Em seguida, você cria a classe de conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamando seu construtor:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Em seguida, conecte a página à <xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 E na linha final, retorne o HWND para o <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Posicionamento do Hwnd

Agora que você tem um HWND que contém o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio, você precisa colocar esse HWND dentro da caixa de diálogo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Se você sabia apenas onde colocar o HWND, basta passar esse tamanho e o local para a função `GetHwnd` que você definiu anteriormente. Mas você usou um arquivo de recurso para definir a caixa de diálogo, então não tem muita certeza sobre onde os HWNDs estão posicionados. Você pode usar o editor de caixa de diálogo do Visual Studio para colocar um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controle estático no qual deseja que o relógio fique ("Inserir relógio aqui") e usá-lo para posicionar o relógio de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Onde você lida com o WM_INITDIALOG, você usa `GetDlgItem` para recuperar o HWND para o espaço reservado estático:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Em seguida, você calcula o tamanho e a posição desse espaço reservado estático, para que você possa colocar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio nesse local:

Retângulo RECT;

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

Em seguida, oculte o espaço reservado STATIC:

```cpp
ShowWindow(placeholder, SW_HIDE);
```

E crie o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do relógio HWND nesse local:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

Para tornar o tutorial interessante e produzir um relógio de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] real, você precisará criar um controle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio neste ponto. Você pode fazer isso basicamente na marcação, com apenas alguns manipuladores de eventos no code-behind. Como este tutorial é sobre interoperação e não sobre design de controle, o código completo para o relógio de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é fornecido aqui como um bloco de código, sem instruções discretas para criá-lo ou o que significa cada parte. Fique à vontade para testar este código para alterar a aparência ou a funcionalidade do controle.

Aqui está a marcação:

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

E aqui está o code-behind que acompanha:

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

O resultado final se parece com:

![Caixa de diálogo Propriedades da data e hora final do resultado](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

Para comparar o resultado final ao código que produziu esta captura de tela, consulte [exemplo de interoperação de relógio Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Interop.HwndSource>
- [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md)
- [Exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051)

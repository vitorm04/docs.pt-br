---
title: 'Passo a passo: criar o primeiro aplicativo sensível ao toque'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
ms.openlocfilehash: 53ae737394d76d9f293f6e03fbf04cbb46d2adbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778814"
---
# <a name="walkthrough-creating-your-first-touch-application"></a>Passo a passo: criar o primeiro aplicativo sensível ao toque
O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possibilita que os aplicativos respondam ao toque. Por exemplo, você pode interagir com um aplicativo usando um ou mais dedos em um dispositivo sensível ao toque, como uma tela sensível ao toque. Este passo a passo cria um aplicativo que possibilita ao usuário mover, redimensionar ou girar um único objeto usando toque.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
- Visual Studio.  
  
- Um dispositivo que aceita entrada de toque, como uma tela sensível ao toque, que dá suporte a Windows Touch.  
  
 Além disso, você deve ter um entendimento básico de como criar um aplicativo em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especialmente como assinar um evento e manipulá-lo. Para obter mais informações, confira [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="creating-the-application"></a>Criando o aplicativo  
  
#### <a name="to-create-the-application"></a>Para criar o aplicativo  
  
1. Crie um novo projeto de aplicativo do WPF no Visual Basic ou no Visual C#, chamado `BasicManipulation`. Para obter mais informações, confira [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
2. Substitua o conteúdo de MainWindow.xaml pelo XAML a seguir.  
  
     Essa marcação cria um aplicativo simples que contém um vermelho <xref:System.Windows.Shapes.Rectangle> em um <xref:System.Windows.Controls.Canvas>. O <xref:System.Windows.UIElement.IsManipulationEnabled%2A> propriedade do <xref:System.Windows.Shapes.Rectangle> for definido como true para que ele receba eventos de manipulação. O aplicativo assina os <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, e <xref:System.Windows.UIElement.ManipulationInertiaStarting> eventos. Esses eventos contêm a lógica para mover o <xref:System.Windows.Shapes.Rectangle> quando o usuário o manipula.  
  
     [!code-xaml[BasicManipulation#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3. Se você estiver usando o Visual Basic, na primeira linha de MainWindow.xaml, substitua `x:Class="BasicManipulation.MainWindow"` por `x:Class="MainWindow"`.  
  
4. No `MainWindow` da classe, adicione o seguinte <xref:System.Windows.UIElement.ManipulationStarting> manipulador de eventos.  
  
     O <xref:System.Windows.UIElement.ManipulationStarting> evento ocorre quando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detecta que toque entrada começa a manipular um objeto. O código especifica que a posição da manipulação de deve ser relativo a <xref:System.Windows.Window> definindo o <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> propriedade.  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]

5. No `MainWindow` da classe, adicione o seguinte <xref:System.Windows.Input.ManipulationDelta> manipulador de eventos.

     O <xref:System.Windows.Input.ManipulationDelta> evento ocorre quando o toque muda de posição de entrada e pode ocorrer várias vezes durante uma manipulação. O evento também pode ocorrer depois que um dedo for retirado da tela. Por exemplo, se o usuário arrasta um dedo pela tela, o <xref:System.Windows.Input.ManipulationDelta> evento ocorre várias vezes conforme o dedo é movido. Quando o usuário retira um dedo na tela, o <xref:System.Windows.Input.ManipulationDelta> evento continua ocorrendo para simular inércia.

     O código se aplica a <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> para o <xref:System.Windows.UIElement.RenderTransform%2A> da <xref:System.Windows.Shapes.Rectangle> para movê-lo conforme o usuário move o toque de entrada. Ele também verifica se o <xref:System.Windows.Shapes.Rectangle> está fora dos limites do <xref:System.Windows.Window> quando o evento ocorre durante a inércia. Se assim, o aplicativo chama o <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> método para encerrar a manipulação.

     [!code-csharp[BasicManipulation#ManipulationDelta](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]

6. No `MainWindow` da classe, adicione o seguinte <xref:System.Windows.UIElement.ManipulationInertiaStarting> manipulador de eventos.

     O <xref:System.Windows.UIElement.ManipulationInertiaStarting> evento ocorre quando o usuário retira todos os dedos da tela. O código define a velocidade inicial e a desaceleração para a movimentação, a expansão e a rotação do retângulo.

     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]

7. Compile e execute o projeto.

     Você deve ver um quadrado vermelho aparecer na janela.

## <a name="testing-the-application"></a>Testando o aplicativo
 Para testar o aplicativo, tente as seguintes manipulações. Observe que você pode fazer mais de uma das seguintes opções ao mesmo tempo.

- Para mover o <xref:System.Windows.Shapes.Rectangle>, coloque um dedo no <xref:System.Windows.Shapes.Rectangle> e mova o dedo na tela.

- Para redimensionar o <xref:System.Windows.Shapes.Rectangle>, coloque dois dedos no <xref:System.Windows.Shapes.Rectangle> e mova os dedos aproxime ou afaste uns aos outros.

- Para girar o <xref:System.Windows.Shapes.Rectangle>, coloque dois dedos no <xref:System.Windows.Shapes.Rectangle> e gire os dedos em torno do outro.

 Para causar inércia, retire seus dedos da tela enquanto realiza as manipulações anteriores. O <xref:System.Windows.Shapes.Rectangle> continuará a mover, redimensionar ou girar por alguns segundos antes de parar.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
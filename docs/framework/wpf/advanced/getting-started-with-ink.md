---
title: Criar um InkCanvas em um aplicativo do WPF no Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: d633111c5abc572b0fc27c1a5b32050681504073
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807953"
---
# <a name="get-started-with-ink-in-wpf"></a>Introdução a tinta no WPF

Windows Presentation Foundation (WPF) tem um recurso de tinta que facilita a incorporar tinta digital em seu aplicativo.

## <a name="prerequisites"></a>Pré-requisitos

Para usar os exemplos a seguir, primeiro instale [Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Ele também ajuda a saber como escrever aplicativos básicos do WPF. Para obter ajuda na introdução ao WPF, consulte [passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>Início rápido

Esta seção ajuda você a escrever um aplicativo WPF simple que coleta tinta.

### <a name="got-ink"></a>Tem tinta?

Para criar um aplicativo WPF que dê suporte a tinta:

1. Abra o Visual Studio.

2. Criar um novo **aplicativo WPF**.

   No **novo projeto** caixa de diálogo, expanda o **instalado** > **Visual C#** ou **Visual Basic**  >   **Área de trabalho do Windows** categoria. Em seguida, selecione a **aplicativo WPF (.NET Framework)** modelo de aplicativo. Insira um nome e, em seguida, selecione **Okey**.

   O Visual Studio cria o projeto, e *MainWindow. XAML* abre no designer.

3. Tipo de `<InkCanvas/>` entre o `<Grid>` marcas.

   ![Designer XAML com marca InkCanvas](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. Pressione **F5** para iniciar o aplicativo no depurador.

5. Usando um mouse ou caneta, escrever **Olá, mundo** na janela.

Você escreveu o equivalente em tinta de um aplicativo "Olá, Mundo" com apenas 12 pressionamentos de tecla!

### <a name="spice-up-your-app"></a>Aprimore seu aplicativo

Vamos aproveitar alguns recursos do WPF. Substitua tudo entre a abertura e fechamento \<Janela > marcas com a seguinte marcação:

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

Esse XAML cria um plano de fundo de pincel de gradiente na superfície de tinta.

![Cores de gradiente na superfície no aplicativo WPF de tinta](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>Adicionar algum código por trás de XAML

Embora XAML torne muito fácil projetar a interface do usuário, qualquer aplicativo do mundo real precisa adicionar código para manipular eventos. Aqui está um exemplo simples que ampliará a tinta em resposta a um clique com botão direito do mouse.

1. Defina o `MouseRightButtonUp` manipulador no seu XAML:

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. Na **Gerenciador de soluções**, expanda MainWindow. XAML e abra o arquivo code-behind (MainWindow.xaml.cs ou. XAML. vb). Adicione o seguinte código do manipulador de eventos:

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Execute o aplicativo. Adicione alguma tinta e, em seguida, clique com o mouse ou executar uma ação de pressionar e segurar equivalente com uma caneta.

   A exibição amplia cada vez que você clicar com o botão direito do mouse.

### <a name="use-procedural-code-instead-of-xaml"></a>Use o código de procedimento em vez de XAML

Você pode acessar todos os recursos do WPF do código de procedimento. Siga estas etapas para criar um aplicativo "Olá, mundo da tinta" para o WPF que não usa qualquer XAML em todos os.

1. Crie um novo projeto de aplicativo de console no Visual Studio.

   No **novo projeto** caixa de diálogo, expanda o **instalado** > **Visual C#** ou **Visual Basic**  >   **Área de trabalho do Windows** categoria. Em seguida, selecione a **aplicativo de Console (.NET Framework)** modelo de aplicativo. Insira um nome e, em seguida, selecione **Okey**.

1. Cole o código a seguir no arquivo Program.cs ou Program. vb:

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Adicione referências aos assemblies PresentationCore, PresentationFramework e WindowsBase clicando **referências** na **Gerenciador de soluções** e escolhendo **Add Reference**.

   ![Gerenciador de referências mostrando PresentationCore e PresentationFramework](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. Compile o aplicativo pressionando **F5**.

## <a name="see-also"></a>Consulte também

- [Tinta digital](digital-ink.md)
- [Coletando tinta](collecting-ink.md)
- [Reconhecimento de manuscrito](handwriting-recognition.md)
- [Armazenando a tinta](storing-ink.md)

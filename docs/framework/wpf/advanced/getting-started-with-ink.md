---
title: Criar um InkCanvas em um aplicativo WPF no Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: ebbf25037921e7802b2bfcb6ffa562d16a849ffa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920247"
---
# <a name="get-started-with-ink-in-wpf"></a>Introdução à tinta no WPF

O Windows Presentation Foundation (WPF) tem um recurso de tinta que facilita a incorporação de tinta digital em seu aplicativo.

## <a name="prerequisites"></a>Prerequisites

Para usar os exemplos a seguir, primeiro instale o [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Também ajuda a saber como escrever aplicativos básicos do WPF. Para obter ajuda sobre como começar a usar o WPF, consulte [Walkthrough: meu primeiro aplicativo de área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>Início rápido

Esta seção ajuda você a escrever um aplicativo simples do WPF que coleta tinta.

### <a name="got-ink"></a>Tem tinta?

Para criar um aplicativo do WPF que dá suporte à tinta:

1. Abra o Visual Studio.

2. Crie um novo **aplicativo do WPF**.

   Na caixa de diálogo **novo projeto** , expanda a categoria **instalação** do > **Visual C#**  ou **Visual Basic** > **área de trabalho do Windows** . Em seguida, selecione o modelo de aplicativo do **aplicativo WPF (.NET Framework)** . Insira um nome e, em seguida, selecione **OK**.

   O Visual Studio cria o projeto e *MainWindow. XAML* é aberto no designer.

3. Digite `<InkCanvas/>` entre as marcas de `<Grid>`.

   ![Designer XAML com marca InkCanvas](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. Pressione **F5** para iniciar o aplicativo no depurador.

5. Usando uma caneta ou um mouse, escreva **Olá, mundo** na janela.

Você escreveu o equivalente em tinta de um aplicativo "Olá, Mundo" com apenas 12 pressionamentos de tecla!

### <a name="spice-up-your-app"></a>Melhorar seu aplicativo

Vamos aproveitar alguns recursos do WPF. Substitua tudo entre a janela de \<de abertura e fechamento > marcações com a seguinte marcação:

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

Esse XAML cria um plano de fundo de pincel de gradiente em sua superfície de tinta.

![Cores de gradiente na superfície de tinta no aplicativo WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>Adicionar algum código por trás do XAML

Embora XAML torne muito fácil projetar a interface do usuário, qualquer aplicativo do mundo real precisa adicionar código para manipular eventos. Aqui está um exemplo simples que amplia a tinta em resposta a um clique com o botão direito do mouse.

1. Defina o manipulador de `MouseRightButtonUp` em seu XAML:

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. Em **Gerenciador de soluções**, expanda MainWindow. XAML e abra o arquivo code-behind (MainWindow.XAML.cs ou MainWindow. XAML. vb). Adicione o seguinte código do manipulador de eventos:

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Execute o aplicativo. Adicione uma tinta e, em seguida, clique com o botão direito do mouse ou execute um equivalente de pressionar e segurar com uma caneta.

   A exibição é ampliada quando você clica com o botão direito do mouse.

### <a name="use-procedural-code-instead-of-xaml"></a>Usar código de procedimento em vez de XAML

Você pode acessar todos os recursos do WPF do código de procedimento. Siga estas etapas para criar um aplicativo "Olá, mundo da tinta" para o WPF que não usa nenhum XAML.

1. Crie um novo projeto de aplicativo de console no Visual Studio.

   Na caixa de diálogo **novo projeto** , expanda a categoria **instalação** do > **Visual C#**  ou **Visual Basic** > **área de trabalho do Windows** . Em seguida, selecione o modelo de aplicativo do **aplicativo de console (.NET Framework)** . Insira um nome e, em seguida, selecione **OK**.

1. Cole o código a seguir no arquivo Program.cs ou Program. vb:

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Adicione referências aos assemblies PresentationCore, PresentationFramework e WindowsBase clicando com o botão direito do mouse em **referências** em **Gerenciador de soluções** e escolhendo **Adicionar referência**.

   ![Gerenciador de referências mostrando PresentationCore e PresentationFramework](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. Crie o aplicativo pressionando **F5**.

## <a name="see-also"></a>Consulte também

- [Tinta digital](digital-ink.md)
- [Coletando tinta](collecting-ink.md)
- [Reconhecimento de manuscrito](handwriting-recognition.md)
- [Armazenando a tinta](storing-ink.md)

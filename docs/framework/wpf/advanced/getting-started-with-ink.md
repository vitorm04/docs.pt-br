---
title: "Introdução à tinta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 74227ebe815e971087569ff39ac0a3479c1b0d14
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="getting-started-with-ink"></a>Introdução à tinta
Incorporar tinta digital a seus aplicativos ficou ainda mais fácil. A tinta evolui de ser corolário para os métodos de programação de COM e os Windows Forms para atingir integração total com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Você não precisa instalar SDKs nem bibliotecas de tempo de execução separados.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para usar os exemplos a seguir, você deve primeiro instalar o Microsoft Visual Studio 2005 e o [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Você também deve compreender como escrever aplicativos para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações sobre como começar com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [passo a passo: meu primeiro aplicativo de área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="quick-start"></a>Início rápido  
 Esta seção ajuda a escrever um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simples que coleta tinta.  
  
 Se você ainda não tiver feito isso, instale o Microsoft Visual Studio 2005 e o [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]. Os aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geralmente devem ser compilados antes que você possa exibi-los, mesmo que consistem inteiramente em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. No entanto, o [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] inclui um aplicativo, XamlPad, projetado para acelerar o processo de implementar uma interface do usuário baseada em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Você pode usar esse aplicativo para exibir e ajustar os primeiros exemplos neste documento. O processo de criação de aplicativos compilados com base em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é abordado mais adiante neste documento.  
  
 Para iniciar XAMLPad, clique o **iniciar** , aponte para **todos os programas**, aponte para **SDK do Microsoft Windows**, aponte para **ferramentas**e clique em **XAMLPad**. No painel de renderização, XAMLPad processa o código XAML escrito no painel de código. Você pode editar o código XAML e as alterações imediatamente aparecerão no painel de renderização.  
  
#### <a name="got-ink"></a>Tem tinta?  
 Para iniciar seu primeiro aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que dê suporte a tinta:  
  
1.  Abra o Microsoft Visual Studio 2005  
  
2.  Criar novos **Aplicativos do Windows (WPF)**  
  
3.  Digite `<InkCanvas/>` entre as marcas `<Grid>`  
  
4.  Pressione **F5** para inicializar o aplicativo no depurador  
  
5.  Usando uma caneta ou o mouse, escreva **Olá, Mundo** na janela  
  
 Você escreveu o equivalente em tinta de um aplicativo "Olá, Mundo" com apenas 12 pressionamentos de tecla!  
  
#### <a name="spice-up-your-application"></a>Aprimore seu aplicativo  
 Vamos aproveitar alguns recursos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Substitua tudo entre as marcas de abertura \<Window> e fechamento \</Window> marcas com a marcação a seguir para obter uma tela de fundo de pincel de gradiente na superfície de tinta.  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a>Usando animação  
 Por diversão, vamos animar as cores do pincel do gradiente. Adicione o seguinte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] após a marca `</InkCanvas>` de fechamento, mas antes da marca `</Page>` de fechamento.  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a>Adicionando algum código por trás de XAML  
 Embora XAML torne muito fácil projetar a interface do usuário, qualquer aplicativo do mundo real precisa adicionar código para manipular eventos. Aqui está um exemplo simples que ampliará a tinta em resposta a um clique com o botão direito do mouse:  
  
 Definir o manipulador `MouseRightButtonUp` no seu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 No Gerenciador de Soluções do Visual Studio, expanda Windows1.xaml e abra o arquivo code-behind, Window1.xaml.cs ou Window1.xaml.vb, se você estiver usando Visual Basic. Adicione o seguinte código do manipulador de eventos:  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 Agora execute seu aplicativo. Adicione alguma tinta e clique com o botão direito do mouse ou execute uma ação de pressionar e segurar equivalente com uma caneta.  
  
#### <a name="using-procedural-code-instead-of-xaml"></a>Usando código de procedimento, em vez de XAML  
 Você pode acessar todos os recursos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do código de procedimento. Aqui está um aplicativo "Olá, Mundo da Tinta" para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que não usa nenhum [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Cole o código abaixo em um Aplicativo de Console vazio no Visual Studio. Adicione referências aos assemblies PresentationCore, PresentationFramework e WindowsBase e compile o aplicativo pressionando **F5**:  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Tinta digital](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [Coletando tinta](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [Reconhecimento de manuscrito](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [Armazenando a tinta](../../../../docs/framework/wpf/advanced/storing-ink.md)

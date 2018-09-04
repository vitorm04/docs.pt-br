---
title: Criando um controle de entrada de tinta
ms.date: 03/30/2017
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
ms.openlocfilehash: 3113b953c1c547035883a4f4b51f53e4aefdf0a6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43537867"
---
# <a name="creating-an-ink-input-control"></a>Criando um controle de entrada de tinta
Você pode criar um controle personalizado que renderiza a tinta de forma dinâmica e estática. Ou seja, é possível renderizar a tinta conforme um usuário desenha um traço, fazendo com que a tinta apareça "fluindo" da caneta eletrônica e exibi-la depois de adicionada ao controle, tanto pela caneta eletrônica, colada da área de transferência ou carregada de um arquivo. Para renderizar a tinta dinamicamente, o controle deve usar um <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Para renderizar a tinta estaticamente, você deve substituir os métodos de evento de caneta (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, e <xref:System.Windows.UIElement.OnStylusUp%2A>) para coletar <xref:System.Windows.Input.StylusPoint> dados, criar traços e adicioná-los para um <xref:System.Windows.Controls.InkPresenter> (que renderiza a tinta no controle).  
  
 Este tópico contém as seguintes subseções:  
  
-   [Como coletar dados de ponto da caneta e criar traços de tinta](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [Como habilitar o controle para aceitar a entrada do mouse](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [Juntando as peças](#PuttingItTogether)  
  
-   [Usando plug-ins adicionais e o DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [Conclusão](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Como coletar dados de ponto da caneta e criar traços de tinta  
 Para criar um controle que coleta e gerencia traços de tinta, faça o seguinte:  
  
1.  Derive uma classe de <xref:System.Windows.Controls.Control> ou uma das classes derivadas de <xref:System.Windows.Controls.Control>, como <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  Adicionar um <xref:System.Windows.Controls.InkPresenter> para a classe e defina a <xref:System.Windows.Controls.ContentControl.Content%2A> propriedade para o novo <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  Anexar a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> do <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> para o <xref:System.Windows.Controls.InkPresenter> chamando o <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> método e adicione o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> para o <xref:System.Windows.UIElement.StylusPlugIns%2A> coleção. Isso permite que o <xref:System.Windows.Controls.InkPresenter> exiba a tinta conforme os dados de ponto da caneta são coletados pelo seu controle.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  Substituir o método <xref:System.Windows.UIElement.OnStylusDown%2A>.  Nesse método, capture a caneta com uma chamada para <xref:System.Windows.Input.Stylus.Capture%2A>. Ao capturar a caneta, o controle será para continuar a receber <xref:System.Windows.UIElement.StylusMove> e <xref:System.Windows.UIElement.StylusUp> eventos mesmo se a caneta sai dos limites do controle. Isso não é estritamente obrigatório, mas quase sempre desejado para uma boa experiência do usuário. Criar um novo <xref:System.Windows.Input.StylusPointCollection> reunir <xref:System.Windows.Input.StylusPoint> dados. Por fim, adicione o conjunto inicial de <xref:System.Windows.Input.StylusPoint> dados para o <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  Substituir a <xref:System.Windows.UIElement.OnStylusMove%2A> método e adicione o <xref:System.Windows.Input.StylusPoint> dados para o <xref:System.Windows.Input.StylusPointCollection> objeto que você criou anteriormente.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  Substituir a <xref:System.Windows.UIElement.OnStylusUp%2A> método e crie um novo <xref:System.Windows.Ink.Stroke> com o <xref:System.Windows.Input.StylusPointCollection> dados. Adicione a nova <xref:System.Windows.Ink.Stroke> você criou para o <xref:System.Windows.Controls.InkPresenter.Strokes%2A> coleção da <xref:System.Windows.Controls.InkPresenter> e solte a captura da caneta.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Como habilitar o controle para aceitar a entrada do mouse  
 Se você adicionar o controle anterior ao seu aplicativo, executá-lo e usar o mouse como um dispositivo de entrada, você notará que os traços não serão preservados. Para manter os traços quando o mouse for usado como o dispositivo de entrada, faça o seguinte:  
  
1.  Substituir a <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> e crie um novo <xref:System.Windows.Input.StylusPointCollection> Obtenha a posição do mouse quando o evento ocorreu e crie um <xref:System.Windows.Input.StylusPoint> usando os dados de ponto e adicione o <xref:System.Windows.Input.StylusPoint> para o <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  Substituir o método <xref:System.Windows.UIElement.OnMouseMove%2A>. Obtenha a posição do mouse quando o evento ocorreu e crie um <xref:System.Windows.Input.StylusPoint> usando os dados de ponto.  Adicione a <xref:System.Windows.Input.StylusPoint> para o <xref:System.Windows.Input.StylusPointCollection> objeto que você criou anteriormente.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  Substituir o método <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>.  Criar um novo <xref:System.Windows.Ink.Stroke> com o <xref:System.Windows.Input.StylusPointCollection> dados e adicione a nova <xref:System.Windows.Ink.Stroke> você criou para o <xref:System.Windows.Controls.InkPresenter.Strokes%2A> coleção do <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Juntando as peças  
 O exemplo a seguir é um controle personalizado que coleta tinta quando o usuário utiliza o mouse ou a caneta.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Usando plug-ins adicionais e o DynamicRenderers  
 Como o InkCanvas, o controle personalizado pode ter personalizado <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> adicionais e <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objetos. Adicione-os para o <xref:System.Windows.UIElement.StylusPlugIns%2A> coleção. A ordem dos <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objetos no <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> afeta a aparência da tinta quando ela é renderizada. Suponha que você tenha um <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> chamado `dynamicRenderer` e um personalizado <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> chamado `translatePlugin` que desloca a tinta da caneta eletrônica. Se `translatePlugin` é o primeiro <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> na <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, e `dynamicRenderer` é o segundo, a tinta que "flui" será deslocada conforme o usuário move a caneta. Se `dynamicRenderer` for primeiro e `translatePlugin` for o segundo, a tinta não será deslocada até que o usuário levante a caneta.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Conclusão  
 Você pode criar um controle que coleta e renderiza a tinta, substituindo os métodos de evento da caneta. Ao criar seu próprio controle, derivando suas próprias <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes e inserindo-o em <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, você pode implementar praticamente qualquer comportamento imaginável com tinta digital. Você tem acesso a <xref:System.Windows.Input.StylusPoint> dados como ele são gerados, dando a você a oportunidade de personalizar <xref:System.Windows.Input.Stylus> de entrada e renderizá-lo na tela, conforme apropriado para seu aplicativo. Porque você tem tal acesso de baixo nível para o <xref:System.Windows.Input.StylusPoint> dados, você pode implementar a coleção de tinta e renderizá-la com um desempenho ideal para seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Tratamento avançado de tinta](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Acessar e manipular a entrada à caneta](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)

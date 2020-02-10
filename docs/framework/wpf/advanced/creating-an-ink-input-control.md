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
ms.openlocfilehash: 98b2abf813a232e36b80683254174b12b97659bb
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095210"
---
# <a name="creating-an-ink-input-control"></a>Criando um controle de entrada de tinta
Você pode criar um controle personalizado que renderiza a tinta de forma dinâmica e estática. Ou seja, é possível renderizar a tinta conforme um usuário desenha um traço, fazendo com que a tinta apareça "fluindo" da caneta eletrônica e exibi-la depois de adicionada ao controle, tanto pela caneta eletrônica, colada da área de transferência ou carregada de um arquivo. Para renderizar a tinta dinamicamente, seu controle deve usar um <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Para renderizar de forma estática a tinta, você deve substituir os métodos de evento da caneta (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>e <xref:System.Windows.UIElement.OnStylusUp%2A>) para coletar <xref:System.Windows.Input.StylusPoint> dados, criar traços e adicioná-los a um <xref:System.Windows.Controls.InkPresenter> (que renderiza a tinta no controle).  
  
 Este tópico contém as seguintes subseções:  
  
- [Como coletar dados de ponto da caneta e criar traços de tinta](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Como habilitar o controle para aceitar a entrada do mouse](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Juntando as peças](#PuttingItTogether)  
  
- [Usando plug-ins adicionais e o DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Conclusão](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Como coletar dados de ponto da caneta e criar traços de tinta  
 Para criar um controle que coleta e gerencia traços de tinta, faça o seguinte:  
  
1. Derive uma classe de <xref:System.Windows.Controls.Control> ou uma das classes derivadas de <xref:System.Windows.Controls.Control>, como <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Adicione um <xref:System.Windows.Controls.InkPresenter> à classe e defina a propriedade <xref:System.Windows.Controls.ContentControl.Content%2A> para o novo <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. Anexe o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> do <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ao <xref:System.Windows.Controls.InkPresenter> chamando o método <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> e adicione o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à coleção de <xref:System.Windows.UIElement.StylusPlugIns%2A>. Isso permite que o <xref:System.Windows.Controls.InkPresenter> exiba a tinta à medida que os dados do ponto da caneta são coletados pelo seu controle.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Substituir o método <xref:System.Windows.UIElement.OnStylusDown%2A>.  Nesse método, Capture a caneta com uma chamada para <xref:System.Windows.Input.Stylus.Capture%2A>. Ao capturar a caneta, seu controle continuará a receber <xref:System.Windows.UIElement.StylusMove> e <xref:System.Windows.UIElement.StylusUp> eventos, mesmo que a caneta saia dos limites do controle. Isso não é estritamente obrigatório, mas quase sempre desejado para uma boa experiência do usuário. Crie um novo <xref:System.Windows.Input.StylusPointCollection> para coletar dados de <xref:System.Windows.Input.StylusPoint>. Por fim, adicione o conjunto inicial de dados de <xref:System.Windows.Input.StylusPoint> à <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Substitua o método <xref:System.Windows.UIElement.OnStylusMove%2A> e adicione os dados de <xref:System.Windows.Input.StylusPoint> ao objeto <xref:System.Windows.Input.StylusPointCollection> que você criou anteriormente.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Substitua o método <xref:System.Windows.UIElement.OnStylusUp%2A> e crie um novo <xref:System.Windows.Ink.Stroke> com os dados de <xref:System.Windows.Input.StylusPointCollection>. Adicione o novo <xref:System.Windows.Ink.Stroke> criado à coleção de <xref:System.Windows.Controls.InkPresenter.Strokes%2A> do <xref:System.Windows.Controls.InkPresenter> e libere a captura da caneta.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Como habilitar o controle para aceitar a entrada do mouse  
 Se você adicionar o controle anterior ao seu aplicativo, executá-lo e usar o mouse como um dispositivo de entrada, você notará que os traços não serão preservados. Para manter os traços quando o mouse for usado como o dispositivo de entrada, faça o seguinte:  
  
1. Substitua o <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> e crie um novo <xref:System.Windows.Input.StylusPointCollection> obter a posição do mouse quando o evento ocorreu e criar um <xref:System.Windows.Input.StylusPoint> usando os dados do ponto e adicionar o <xref:System.Windows.Input.StylusPoint> ao <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Substituir o método <xref:System.Windows.UIElement.OnMouseMove%2A>. Obtenha a posição do mouse quando o evento ocorreu e crie um <xref:System.Windows.Input.StylusPoint> usando os dados do ponto.  Adicione o <xref:System.Windows.Input.StylusPoint> ao objeto <xref:System.Windows.Input.StylusPointCollection> que você criou anteriormente.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Substituir o método <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>.  Crie um novo <xref:System.Windows.Ink.Stroke> com os dados de <xref:System.Windows.Input.StylusPointCollection> e adicione o novo <xref:System.Windows.Ink.Stroke> criado à coleção de <xref:System.Windows.Controls.InkPresenter.Strokes%2A> do <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Juntando as peças  
 O exemplo a seguir é um controle personalizado que coleta tinta quando o usuário utiliza o mouse ou a caneta.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Usando plug-ins adicionais e o DynamicRenderers  
 Como o InkCanvas, seu controle personalizado pode ter <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personalizados e objetos <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> adicionais. Adicione-os à coleção de <xref:System.Windows.UIElement.StylusPlugIns%2A>. A ordem dos objetos de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> no <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> afeta a aparência da tinta quando ela é renderizada. Suponha que você tenha uma <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> chamada `dynamicRenderer` e uma <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personalizada chamada `translatePlugin` que desloca a tinta da caneta eletrônica. Se `translatePlugin` for a primeira <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> no <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>e `dynamicRenderer` for a segunda, a tinta que "flui" será deslocada quando o usuário mover a caneta. Se `dynamicRenderer` for primeiro e `translatePlugin` for o segundo, a tinta não será deslocada até que o usuário levante a caneta.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Conclusão  
 Você pode criar um controle que coleta e renderiza a tinta, substituindo os métodos de evento da caneta. Ao criar seu próprio controle, derivar suas próprias classes de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> e inseri-las no <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, você pode implementar praticamente qualquer comportamento que possa ser imaginado com tinta digital. Você tem acesso aos dados de <xref:System.Windows.Input.StylusPoint> conforme eles são gerados, oferecendo a oportunidade de personalizar <xref:System.Windows.Input.Stylus> entrada e renderizá-lo na tela, conforme apropriado para seu aplicativo. Como você tem esse acesso de baixo nível aos dados de <xref:System.Windows.Input.StylusPoint>, você pode implementar a coleta de tinta e renderizá-la com um desempenho ideal para seu aplicativo.  
  
## <a name="see-also"></a>Confira também

- [Tratamento avançado de tinta](advanced-ink-handling.md)
- [Acessar e manipular a entrada à caneta](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))

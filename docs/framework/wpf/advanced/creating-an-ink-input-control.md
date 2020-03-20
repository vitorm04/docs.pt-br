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
ms.openlocfilehash: 394318488b0afb8e043389e0abc3f51dce8604c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186288"
---
# <a name="creating-an-ink-input-control"></a>Criando um controle de entrada de tinta
Você pode criar um controle personalizado que renderiza a tinta de forma dinâmica e estática. Ou seja, é possível renderizar a tinta conforme um usuário desenha um traço, fazendo com que a tinta apareça "fluindo" da caneta eletrônica e exibi-la depois de adicionada ao controle, tanto pela caneta eletrônica, colada da área de transferência ou carregada de um arquivo. Para renderizar dinamicamente tinta, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>seu controle deve usar um . Para renderizar estáticamente a tinta, você deve substituir<xref:System.Windows.UIElement.OnStylusDown%2A>os <xref:System.Windows.UIElement.OnStylusMove%2A>métodos de evento stylus ( , e <xref:System.Windows.UIElement.OnStylusUp%2A>) para coletar <xref:System.Windows.Input.StylusPoint> dados, criar traçados e adicioná-los a um <xref:System.Windows.Controls.InkPresenter> (que renderiza a tinta no controle).  
  
 Este tópico contém as seguintes subseções:  
  
- [Como coletar dados de ponto da caneta e criar traços de tinta](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Como habilitar o controle para aceitar a entrada do mouse](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Juntando as peças](#PuttingItTogether)  
  
- [Usando plug-ins adicionais e o DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Conclusão](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Como coletar dados de ponto da caneta e criar traços de tinta  
 Para criar um controle que coleta e gerencia traços de tinta, faça o seguinte:  
  
1. Derivar uma <xref:System.Windows.Controls.Control> classe de ou uma <xref:System.Windows.Controls.Control>das <xref:System.Windows.Controls.Label>classes derivadas, tais como .  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Adicione <xref:System.Windows.Controls.InkPresenter> um à classe <xref:System.Windows.Controls.ContentControl.Content%2A> e defina <xref:System.Windows.Controls.InkPresenter>a propriedade para o novo .  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. Anexar <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do <xref:System.Windows.Controls.InkPresenter> ao chamando o <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> método <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> e <xref:System.Windows.UIElement.StylusPlugIns%2A> adicionar o à coleção. Isso permite <xref:System.Windows.Controls.InkPresenter> exibir a tinta à medida que os dados do ponto de estilete são coletados pelo seu controle.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Substituir o método <xref:System.Windows.UIElement.OnStylusDown%2A>.  Neste método, capture o estilete <xref:System.Windows.Input.Stylus.Capture%2A>com uma chamada para . Ao capturar a caneta, seu controle continuará <xref:System.Windows.UIElement.StylusMove> recebendo e <xref:System.Windows.UIElement.StylusUp> eventos mesmo que o estilete deixe os limites do controle. Isso não é estritamente obrigatório, mas quase sempre desejado para uma boa experiência do usuário. Crie um <xref:System.Windows.Input.StylusPointCollection> novo <xref:System.Windows.Input.StylusPoint> para coletar dados. Por fim, adicione <xref:System.Windows.Input.StylusPoint> o conjunto <xref:System.Windows.Input.StylusPointCollection>inicial de dados ao .  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Anular o <xref:System.Windows.UIElement.OnStylusMove%2A> método e <xref:System.Windows.Input.StylusPoint> adicionar <xref:System.Windows.Input.StylusPointCollection> os dados ao objeto que você criou anteriormente.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Anular o <xref:System.Windows.UIElement.OnStylusUp%2A> método e <xref:System.Windows.Ink.Stroke> criar <xref:System.Windows.Input.StylusPointCollection> um novo com os dados. Adicione o <xref:System.Windows.Ink.Stroke> novo que <xref:System.Windows.Controls.InkPresenter.Strokes%2A> você criou <xref:System.Windows.Controls.InkPresenter> para a coleção da captura de stylus e libere.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Como habilitar o controle para aceitar a entrada do mouse  
 Se você adicionar o controle anterior ao seu aplicativo, executá-lo e usar o mouse como um dispositivo de entrada, você notará que os traços não serão preservados. Para manter os traços quando o mouse for usado como o dispositivo de entrada, faça o seguinte:  
  
1. Anular o <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> e criar <xref:System.Windows.Input.StylusPointCollection> um novo Obtenha a posição do mouse <xref:System.Windows.Input.StylusPoint> quando o evento <xref:System.Windows.Input.StylusPoint> ocorreu <xref:System.Windows.Input.StylusPointCollection>e crie um usando os dados de ponto e adicione o .  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Substituir o método <xref:System.Windows.UIElement.OnMouseMove%2A>. Obtenha a posição do mouse quando o <xref:System.Windows.Input.StylusPoint> evento ocorreu e crie um usando os dados de ponto.  Adicione <xref:System.Windows.Input.StylusPoint> o <xref:System.Windows.Input.StylusPointCollection> objeto que você criou anteriormente.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Substituir o método <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>.  Crie um <xref:System.Windows.Ink.Stroke> novo <xref:System.Windows.Input.StylusPointCollection> com os dados <xref:System.Windows.Ink.Stroke> e adicione <xref:System.Windows.Controls.InkPresenter.Strokes%2A> o novo <xref:System.Windows.Controls.InkPresenter>que você criou à coleção do .  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>
## <a name="putting-it-together"></a>Juntando as peças  
 O exemplo a seguir é um controle personalizado que coleta tinta quando o usuário utiliza o mouse ou a caneta.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Usando plug-ins adicionais e o DynamicRenderers  
 Como o InkCanvas, seu controle <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personalizado <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> pode ter objetos personalizados e adicionais. Adicione isso <xref:System.Windows.UIElement.StylusPlugIns%2A> à coleção. A ordem <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> dos objetos no <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> afeta o aparecimento da tinta quando ela é renderizada. Suponha <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> que `dynamicRenderer` você <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> tenha `translatePlugin` um chamado e um costume chamado que compensa a tinta da caneta do tablet. Se `translatePlugin` for <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>primeira `dynamicRenderer` no , e for a segunda, a tinta que "flui" será compensada à medida que o usuário move a caneta. Se `dynamicRenderer` for primeiro e `translatePlugin` for o segundo, a tinta não será deslocada até que o usuário levante a caneta.  
  
<a name="AdvancedInkHandling_Conclusion"></a>
## <a name="conclusion"></a>Conclusão  
 Você pode criar um controle que coleta e renderiza a tinta, substituindo os métodos de evento da caneta. Ao criar seu próprio controle, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> derivando suas próprias <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>classes e inserindo-as em , você pode implementar praticamente qualquer comportamento imaginável com tinta digital. Você tem acesso <xref:System.Windows.Input.StylusPoint> aos dados como eles são gerados, dando-lhe a oportunidade de personalizar <xref:System.Windows.Input.Stylus> a entrada e torná-los na tela conforme apropriado para sua aplicação. Como você tem um acesso <xref:System.Windows.Input.StylusPoint> tão baixo aos dados, você pode implementar a coleta de tinta e torná-la com o desempenho ideal para sua aplicação.  
  
## <a name="see-also"></a>Confira também

- [Tratamento de Tinta Avançado](advanced-ink-handling.md)
- [Acessar e manipular a entrada à caneta](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))

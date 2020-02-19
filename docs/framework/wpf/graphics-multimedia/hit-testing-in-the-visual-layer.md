---
title: Teste de clique na camada visual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit testing functionality [WPF]
- visual layer [WPF], hit testing functionality
ms.assetid: b1a64b61-14be-4d75-b89a-5c67bebb2c7b
ms.openlocfilehash: 28ae983923c985050ac589166023e483721028d3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452611"
---
# <a name="hit-testing-in-the-visual-layer"></a>Teste de clique na camada visual
Este tópico fornece uma visão geral da funcionalidade de teste de clique fornecida pela camada visual. O suporte a testes de clique permite que você determine se um valor de geometria ou de ponto cai dentro do conteúdo renderizado de um <xref:System.Windows.Media.Visual>, permitindo que você implemente o comportamento da interface do usuário, como um retângulo de seleção para selecionar vários objetos.  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Cenários de teste de clique  
 A classe <xref:System.Windows.UIElement> fornece o método <xref:System.Windows.UIElement.InputHitTest%2A>, que permite que você clique no teste em um elemento usando um determinado valor de coordenado. Em muitos casos, o método <xref:System.Windows.UIElement.InputHitTest%2A> fornece a funcionalidade desejada para implementar testes de ocorrências de elementos. No entanto, há várias situações em que talvez seja necessário implementar o teste de clique na camada visual.  
  
- Testes de clique em objetos não<xref:System.Windows.UIElement>: isso se aplica se você estiver testando objetos não<xref:System.Windows.UIElement>, como <xref:System.Windows.Media.DrawingVisual> ou objetos gráficos.  
  
- Testes de clique usando uma geometria: isso se aplica se você precisa realizar teste de clique usando um objeto de geometria em vez do valor de coordenada de um ponto.  
  
- Testes de clique em vários objetos: isso se aplica quando você precisa realizar teste de clique em vários objetos, como objetos sobrepostos. Você pode obter resultados para todos os elementos visuais que interceptam uma geometria ou ponto e não apenas o primeiro deles.  
  
- Ignorando <xref:System.Windows.UIElement> política de teste de clique: isso se aplica quando você precisa ignorar a política de teste de <xref:System.Windows.UIElement> clique, que leva em consideração esses fatores como se um elemento está desabilitado ou invisível.  
  
> [!NOTE]
> Para um exemplo de código completo ilustrando o teste de clique na camada visual, consulte [Exemplo de teste de clique usando DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) e [Exemplo de teste de clique com interoperação do Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Suporte de teste de clique  
 A finalidade dos métodos de <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> na classe <xref:System.Windows.Media.VisualTreeHelper> é determinar se um valor de coordenadas de geometria ou de ponto está dentro do conteúdo renderizado de um determinado objeto, como um controle ou elemento gráfico. Por exemplo, você poderia usar o teste de clique para determinar se um clique do mouse, dentro do retângulo delimitador de um objeto, cai dentro da geometria de um círculo. Você também pode optar por substituir a implementação padrão de teste de clique para realizar seus próprios cálculos personalizados de teste de clique.  
  
 A ilustração a seguir mostra a relação entre a região não retangular de um objeto e seu retângulo delimitador.  
  
 ![Diagrama de região de teste de clique válida](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagrama de região de teste de clique válida  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Teste de clique e ordem z  
 A camada visual do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferece suporte ao teste de clique em todos os objetos sob um ponto ou geometria e não apenas no objeto mais alto. Os resultados são retornados em ordem z. No entanto, o objeto visual que você passa como parâmetro para o método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> determina qual parte da árvore visual que será o teste de clique. Você pode fazer teste de clique em toda a árvore visual ou em qualquer parte dela.  
  
 Na ilustração a seguir, o objeto circular está por cima dos objetos quadrado e triângulo. Se você estiver interessado apenas em testar novamente o objeto visual cujo valor de ordem z é superior, você pode definir a enumeração de teste de clique Visual para retornar <xref:System.Windows.Media.HitTestResultBehavior.Stop> da <xref:System.Windows.Media.HitTestResultCallback> para interromper a passagem de teste de clique após o primeiro item.  
  
 ![Diagrama da ordem z- de uma árvore visual](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagrama da ordem z- de uma árvore visual  
  
 Se você quiser enumerar todos os objetos visuais em um ponto ou geometria específico, retorne <xref:System.Windows.Media.HitTestResultBehavior.Continue> da <xref:System.Windows.Media.HitTestResultCallback>. Isso significa que você pode realizar teste de clique de objetos visuais que estão sob outros objetos, mesmo que eles estejam totalmente encobertos. Consulte o código de exemplo na seção "Usando um retorno de chamada de resultados do teste de clique" para obter mais informações.  
  
> [!NOTE]
> Um objeto visual que é transparente também pode passar por teste de clique.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Usando o teste de clique padrão  
 Você pode identificar se um ponto está dentro da geometria de um objeto visual, usando o método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> para especificar um objeto visual e um valor de coordenada de ponto para testar. O parâmetro de objeto visual identifica o ponto de partida para a pesquisa de teste de clique na árvore visual. Se um objeto visual for encontrado na árvore visual cuja geometria contém a coordenada, ele será definido como a propriedade <xref:System.Windows.Media.HitTestResult.VisualHit%2A> de um objeto <xref:System.Windows.Media.HitTestResult>. Em seguida, o <xref:System.Windows.Media.HitTestResult> é retornado do método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>. Se o ponto não estiver contido na subárvore Visual em que você está testando, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> retornará `null`.  
  
> [!NOTE]
> O teste de clique padrão sempre retorna o objeto mais alto na ordem z. Para identificar todos os objetos visuais, mesmo aqueles que podem estar totalmente ou parcialmente encobertos, use um retorno de chamada de resultado do teste de clique.  
  
 O valor de coordenado que você passa como o parâmetro de ponto para o método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> deve ser relativo ao espaço de coordenadas do objeto visual em que você está testando. Por exemplo, se você tem objetos visuais aninhados definidos em (100, 100) no espaço de coordenadas do pai, o teste de clique de um objeto visual filho em (0, 0) é equivalente ao teste de clique em (100, 100) no espaço de coordenadas do pai.  
  
 O código a seguir mostra como configurar manipuladores de eventos do mouse para um objeto <xref:System.Windows.UIElement> que é usado para capturar eventos usados para teste de clique.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Como a árvore visual afeta testes de clique  
 O ponto de partida na árvore visual determina quais objetos são retornados durante a enumeração de teste de clique de objetos. Se você tem vários objetos nos quais deseja realizar o teste de clique, o objeto visual usado como o ponto de partida na árvore visual deve ser o ancestral comum de todos os objetos de interesse. Por exemplo, se estiver interessado em realizar testes de clique no elemento botão e no objeto visual de desenho no diagrama a seguir, você terá que definir o ancestral comum de ambos como o ponto de partida na árvore visual. Nesse caso, o elemento tela é o ancestral comum do elemento botão e do objeto visual de desenho.  
  
 ![Diagrama de uma hierarquia de árvore visual](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagrama de uma hierarquia de árvore visual  
  
> [!NOTE]
> A propriedade <xref:System.Windows.UIElement.IsHitTestVisible%2A> Obtém ou define um valor que declara se um objeto derivado <xref:System.Windows.UIElement>pode ser retornado como um resultado de teste de clique de alguma parte de seu conteúdo renderizado. Isso permite que você altere seletivamente a árvore visual para determinar quais objetos visuais estão envolvidos em um teste de clique.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Usando um retorno de chamada de resultado do teste de clique  
 Você pode enumerar todos os objetos visuais em uma árvore visual cuja geometria contém um valor de coordenada especificado. Isso permite que você identifique todos os objetos visuais, mesmo aqueles que podem estar totalmente ou parcialmente encobertos por outros objetos visuais. Para enumerar objetos visuais em uma árvore visual, use o método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> com uma função de retorno de chamada de teste de clique. A função de retorno de chamada de teste de clique é chamada pelo sistema quando o valor de coordenada especificado está contido em um objeto visual.  
  
 Durante a enumeração de resultados do teste de clique, você não deve realizar nenhuma operação que modifica a árvore visual. A adição ou remoção de objetos da árvore visual enquanto ela está sendo percorrida poderá resultar em comportamento imprevisível. Você pode modificar a árvore visual com segurança após o retorno do método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>. Você pode desejar fornecer uma estrutura de dados, como uma <xref:System.Collections.ArrayList>, para armazenar valores durante a enumeração de resultados de teste de clique.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 O método do retorno de chamada do teste de clique define as ações que são realizadas quando um teste de clique é identificado em um determinado objeto visual na árvore visual. Depois de executar as ações, você retorna um valor <xref:System.Windows.Media.HitTestResultBehavior> que determina se deseja continuar a enumeração de quaisquer outros objetos visuais ou não.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> A ordem de enumeração de objetos visuais de ocorrência é pela ordem z. O objeto visual no nível mais alto da ordem z é o primeiro objeto enumerado. Quaisquer outros objetos visuais enumerados estão em níveis decrescentes da ordem z. Esta ordem de enumeração corresponde à ordem de renderização dos elementos visuais.  
  
 Você pode interromper a enumeração de objetos visuais a qualquer momento na função de retorno de chamada de teste de clique, retornando <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Usando um retorno de chamada de filtro de teste de clique  
 Você pode usar um filtro de teste de clique opcional para restringir os objetos que são passados aos resultados do teste de clique. Isso permite que você ignore as partes da árvore visual que você não está interessado em processar nos seus resultados do teste de clique. Para implementar um filtro de teste de clique, defina uma função de retorno de chamada de filtro de teste de clique e passe-a como um valor de parâmetro ao chamar o método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Se você não quiser fornecer a função de retorno de chamada do filtro de teste de clique opcional, passe um valor `null` como seu parâmetro para o método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Aparando uma árvore visual usando um filtro de teste de clique](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Aparando uma árvore visual  
  
 A função de retorno de chamada de filtro de teste de clique permite que você enumere através de todos os elementos visuais cujo conteúdo renderizado contém as coordenadas especificadas. No entanto, você talvez queira ignorar determinadas ramificações da árvore visual, que você não está interessado em processar em sua função de retorno de chamada de resultados do teste de clique. O valor retornado da função de retorno de chamada do filtro de teste de clique determina o tipo de ação que a enumeração dos objetos visuais deve tomar. Por exemplo, se você retornar o valor, <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, você poderá remover o objeto visual atual e seus filhos da enumeração de resultados de teste de clique. Isso significa que a função de retorno de chamada de resultados do teste de clique não verá esses objetos em sua enumeração. Aparar a árvore visual de objetos diminui a quantidade de processamento durante a passagem da enumeração de resultados do teste de clique. No exemplo de código a seguir, o filtro ignora os rótulos e seus descendentes e faz testes de clique de todo o resto.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> O retorno de chamada de filtro do teste de clique às vezes será chamado em casos nos quais o retorno de chamada de resultados do teste de clique não é chamado.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Substituindo o teste de clique padrão  
 Você pode substituir o suporte de teste de clique padrão de um objeto visual substituindo o método <xref:System.Windows.Media.Visual.HitTestCore%2A>. Isso significa que, quando você invoca o método <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>, sua implementação substituída de <xref:System.Windows.Media.Visual.HitTestCore%2A> é chamada. O método substituído é chamado quando um teste de clique cair dentro do retângulo delimitador do objeto visual, mesmo que a coordenada ficar fora do conteúdo renderizado do objeto visual.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Pode haver ocasiões em que você deseja realizar teste de clique no retângulo delimitador e no conteúdo renderizado de um objeto visual. Usando o valor do parâmetro `PointHitTestParameters` no método <xref:System.Windows.Media.Visual.HitTestCore%2A> substituído como o parâmetro para o método base <xref:System.Windows.Media.Visual.HitTestCore%2A>, você pode executar ações com base em um pressionamento do retângulo delimitador de um objeto visual e, em seguida, executar um segundo teste de clique em relação ao conteúdo renderizado do objeto visual.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Teste de clique usando o exemplo de DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)
- [Teste de clique com o exemplo de interoperação do Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Teste de clique de geometria em um visual](how-to-hit-test-geometry-in-a-visual.md)
- [Teste de clique usando um contêiner de host Win32](how-to-hit-test-using-a-win32-host-container.md)

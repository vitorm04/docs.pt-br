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
ms.openlocfilehash: 92b7e8ffab001af4dba6c571fd06c64f2865b1e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962116"
---
# <a name="hit-testing-in-the-visual-layer"></a>Teste de clique na camada visual
Este tópico fornece uma visão geral da funcionalidade de teste de clique fornecida pela camada visual. O suporte a testes de clique permite determinar se um valor de geometria ou de ponto cai dentro do conteúdo <xref:System.Windows.Media.Visual>renderizado de um, permitindo que você implemente o comportamento da interface do usuário, como um retângulo de seleção, para selecionar vários objetos.  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>Cenários de teste de clique  
 A <xref:System.Windows.UIElement> classe fornece o <xref:System.Windows.UIElement.InputHitTest%2A> método, que permite que você clique no teste em um elemento usando um determinado valor de coordenada. Em muitos casos, o <xref:System.Windows.UIElement.InputHitTest%2A> método fornece a funcionalidade desejada para implementar testes de clique de elementos. No entanto, há várias situações em que talvez seja necessário implementar o teste de clique na camada visual.  
  
- Testes de clique em relação<xref:System.Windows.UIElement> a não objetos: Isso se aplicará se você estiver testando<xref:System.Windows.UIElement> os <xref:System.Windows.Media.DrawingVisual> não objetos, como ou objetos gráficos.  
  
- Teste de clique usando uma geometria: Isso se aplicará se você precisar fazer um teste de clique usando um objeto Geometry em vez do valor de coordenadas de um ponto.  
  
- Teste de clique em vários objetos: Isso se aplica quando você precisa clicar em testar em vários objetos, como objetos sobrepostos. Você pode obter resultados para todos os elementos visuais que interceptam uma geometria ou ponto e não apenas o primeiro deles.  
  
- Ignorando <xref:System.Windows.UIElement> a política de teste de clique: Isso se aplica quando você precisa ignorar a <xref:System.Windows.UIElement> política de teste de clique, que leva em consideração esses fatores como se um elemento está desabilitado ou invisível.  
  
> [!NOTE]
> Para um exemplo de código completo ilustrando o teste de clique na camada visual, consulte [Exemplo de teste de clique usando DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994) e [Exemplo de teste de clique com interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>Suporte de teste de clique  
 A finalidade dos <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> métodos <xref:System.Windows.Media.VisualTreeHelper> na classe é determinar se um valor de coordenadas de geometria ou de ponto está dentro do conteúdo renderizado de um determinado objeto, como um controle ou elemento gráfico. Por exemplo, você poderia usar o teste de clique para determinar se um clique do mouse, dentro do retângulo delimitador de um objeto, cai dentro da geometria de um círculo. Você também pode optar por substituir a implementação padrão de teste de clique para realizar seus próprios cálculos personalizados de teste de clique.  
  
 A ilustração a seguir mostra a relação entre a região não retangular de um objeto e seu retângulo delimitador.  
  
 ![Diagrama de região de teste de clique válido](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Diagrama de região de teste de clique válida  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>Teste de clique e ordem z  
 A camada visual do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferece suporte ao teste de clique em todos os objetos sob um ponto ou geometria e não apenas no objeto mais alto. Os resultados são retornados em ordem z. No entanto, o objeto visual que você passa como o parâmetro <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> para o método determina qual parte da árvore visual será o teste de clique. Você pode fazer teste de clique em toda a árvore visual ou em qualquer parte dela.  
  
 Na ilustração a seguir, o objeto circular está por cima dos objetos quadrado e triângulo. Se você estiver interessado apenas em testar novamente o objeto visual cujo valor de ordem z é superior, você pode definir a enumeração de teste de clique Visual para retornar <xref:System.Windows.Media.HitTestResultBehavior.Stop> <xref:System.Windows.Media.HitTestResultCallback> de para parar a passagem de teste de clique após o primeiro item.  
  
 ![Diagrama da ordem z&#45;de uma árvore visual](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Diagrama da ordem z- de uma árvore visual  
  
 Se você quiser enumerar todos os objetos visuais em um ponto ou geometria específico, <xref:System.Windows.Media.HitTestResultBehavior.Continue> retorne <xref:System.Windows.Media.HitTestResultCallback>do. Isso significa que você pode realizar teste de clique de objetos visuais que estão sob outros objetos, mesmo que eles estejam totalmente encobertos. Consulte o código de exemplo na seção "Usando um retorno de chamada de resultados do teste de clique" para obter mais informações.  
  
> [!NOTE]
> Um objeto visual que é transparente também pode passar por teste de clique.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Usando o teste de clique padrão  
 Você pode identificar se um ponto está dentro da geometria de um objeto visual, usando o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método para especificar um objeto visual e um valor de coordenada de ponto para testar. O parâmetro de objeto visual identifica o ponto de partida para a pesquisa de teste de clique na árvore visual. Se um objeto visual for encontrado na árvore visual cuja geometria contém a coordenada, ele será definido como a <xref:System.Windows.Media.HitTestResult.VisualHit%2A> propriedade de um <xref:System.Windows.Media.HitTestResult> objeto. O <xref:System.Windows.Media.HitTestResult> é então retornado <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> do método. Se o ponto não estiver contido na subárvore Visual, você será o teste de clique <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> , `null`retornará.  
  
> [!NOTE]
> O teste de clique padrão sempre retorna o objeto mais alto na ordem z. Para identificar todos os objetos visuais, mesmo aqueles que podem estar totalmente ou parcialmente encobertos, use um retorno de chamada de resultado do teste de clique.  
  
 O valor de coordenado que você passa como o parâmetro <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> de ponto para o método deve ser relativo ao espaço de coordenadas do objeto visual em que você está testando. Por exemplo, se você tem objetos visuais aninhados definidos em (100, 100) no espaço de coordenadas do pai, o teste de clique de um objeto visual filho em (0, 0) é equivalente ao teste de clique em (100, 100) no espaço de coordenadas do pai.  
  
 O código a seguir mostra como configurar manipuladores de eventos do mouse para <xref:System.Windows.UIElement> um objeto que é usado para capturar eventos usados para teste de clique.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Como a árvore visual afeta testes de clique  
 O ponto de partida na árvore visual determina quais objetos são retornados durante a enumeração de teste de clique de objetos. Se você tem vários objetos nos quais deseja realizar o teste de clique, o objeto visual usado como o ponto de partida na árvore visual deve ser o ancestral comum de todos os objetos de interesse. Por exemplo, se estiver interessado em realizar testes de clique no elemento botão e no objeto visual de desenho no diagrama a seguir, você terá que definir o ancestral comum de ambos como o ponto de partida na árvore visual. Nesse caso, o elemento tela é o ancestral comum do elemento botão e do objeto visual de desenho.  
  
 ![Diagrama de uma hierarquia de árvore visual](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Diagrama de uma hierarquia de árvore visual  
  
> [!NOTE]
> A <xref:System.Windows.UIElement.IsHitTestVisible%2A> propriedade Obtém ou define um valor que declara se um <xref:System.Windows.UIElement>objeto derivado pode possivelmente ser retornado como um resultado de teste de clique de alguma parte de seu conteúdo renderizado. Isso permite que você altere seletivamente a árvore visual para determinar quais objetos visuais estão envolvidos em um teste de clique.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Usando um retorno de chamada de resultado do teste de clique  
 Você pode enumerar todos os objetos visuais em uma árvore visual cuja geometria contém um valor de coordenada especificado. Isso permite que você identifique todos os objetos visuais, mesmo aqueles que podem estar totalmente ou parcialmente encobertos por outros objetos visuais. Para enumerar objetos visuais em uma árvore visual, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> use o método com uma função de retorno de chamada de teste de clique. A função de retorno de chamada de teste de clique é chamada pelo sistema quando o valor de coordenada especificado está contido em um objeto visual.  
  
 Durante a enumeração de resultados do teste de clique, você não deve realizar nenhuma operação que modifica a árvore visual. A adição ou remoção de objetos da árvore visual enquanto ela está sendo percorrida poderá resultar em comportamento imprevisível. Você pode modificar a árvore visual com segurança após o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> retorno do método. Você pode desejar fornecer uma estrutura de dados, como um <xref:System.Collections.ArrayList>, para armazenar valores durante a enumeração de resultados de teste de clique.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 O método do retorno de chamada do teste de clique define as ações que são realizadas quando um teste de clique é identificado em um determinado objeto visual na árvore visual. Depois de executar as ações, você retorna um <xref:System.Windows.Media.HitTestResultBehavior> valor que determina se deseja continuar a enumeração de quaisquer outros objetos visuais ou não.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> A ordem de enumeração de objetos visuais de ocorrência é pela ordem z. O objeto visual no nível mais alto da ordem z é o primeiro objeto enumerado. Quaisquer outros objetos visuais enumerados estão em níveis decrescentes da ordem z. Esta ordem de enumeração corresponde à ordem de renderização dos elementos visuais.  
  
 Você pode interromper a enumeração de objetos visuais a qualquer momento na função de retorno de chamada de teste <xref:System.Windows.Media.HitTestResultBehavior.Stop>de clique retornando.  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Usando um retorno de chamada de filtro de teste de clique  
 Você pode usar um filtro de teste de clique opcional para restringir os objetos que são passados aos resultados do teste de clique. Isso permite que você ignore as partes da árvore visual que você não está interessado em processar nos seus resultados do teste de clique. Para implementar um filtro de teste de clique, defina uma função de retorno de chamada de filtro de teste de clique e passe-a <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> como um valor de parâmetro ao chamar o método.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 Se você não quiser fornecer a função de retorno de chamada de filtro de teste de clique `null` opcional, passe um valor como <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> seu parâmetro para o método.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Removendo uma árvore visual usando um filtro de teste de clique](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Aparando uma árvore visual  
  
 A função de retorno de chamada de filtro de teste de clique permite que você enumere através de todos os elementos visuais cujo conteúdo renderizado contém as coordenadas especificadas. No entanto, você talvez queira ignorar determinadas ramificações da árvore visual, que você não está interessado em processar em sua função de retorno de chamada de resultados do teste de clique. O valor retornado da função de retorno de chamada do filtro de teste de clique determina o tipo de ação que a enumeração dos objetos visuais deve tomar. Por exemplo, se você retornar o valor, <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, poderá remover o objeto visual atual e seus filhos da enumeração de resultados de teste de clique. Isso significa que a função de retorno de chamada de resultados do teste de clique não verá esses objetos em sua enumeração. Aparar a árvore visual de objetos diminui a quantidade de processamento durante a passagem da enumeração de resultados do teste de clique. No exemplo de código a seguir, o filtro ignora os rótulos e seus descendentes e faz testes de clique de todo o resto.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> O retorno de chamada de filtro do teste de clique às vezes será chamado em casos nos quais o retorno de chamada de resultados do teste de clique não é chamado.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Substituindo o teste de clique padrão  
 Você pode substituir o suporte de teste de clique padrão de um objeto visual <xref:System.Windows.Media.Visual.HitTestCore%2A> substituindo o método. Isso significa que, quando você invoca <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> o método, sua implementação substituída do <xref:System.Windows.Media.Visual.HitTestCore%2A> é chamada. O método substituído é chamado quando um teste de clique cair dentro do retângulo delimitador do objeto visual, mesmo que a coordenada ficar fora do conteúdo renderizado do objeto visual.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Pode haver ocasiões em que você deseja realizar teste de clique no retângulo delimitador e no conteúdo renderizado de um objeto visual. Usando o valor `PointHitTestParameters` do parâmetro em seu método <xref:System.Windows.Media.Visual.HitTestCore%2A> substituído como o parâmetro para o método <xref:System.Windows.Media.Visual.HitTestCore%2A>base, você pode executar ações com base em um pressionamento do retângulo delimitador de um objeto visual e, em seguida, executar um segundo teste de clique em relação ao conteúdo renderizado do objeto visual.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Teste de clique usando o exemplo de DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994)
- [Teste de clique com o exemplo de interoperação do Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Teste de clique de geometria em um visual](how-to-hit-test-geometry-in-a-visual.md)
- [Teste de clique usando um contêiner de host Win32](how-to-hit-test-using-a-win32-host-container.md)

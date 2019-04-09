---
title: Diretrizes para criar controles com estilo
ms.date: 03/30/2017
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
ms.openlocfilehash: 756cc821b1a9fe20741e390a1fe6e84d12cc6363
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148155"
---
# <a name="guidelines-for-designing-stylable-controls"></a>Diretrizes para criar controles com estilo
Este documento resume um conjunto de práticas recomendadas a serem consideradas ao criar um controle que você deseja que seja fácil de criar estilos e modelos. Nós chegamos a este conjunto de práticas recomendadas por meio de muitas tentativas e erros ao trabalhar nos estilos de controle de tema do conjunto de controles internos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aprendemos que uma definição de estilo bem-sucedida é tanto uma função de um modelo de objeto com um bom design quanto é do próprio estilo. O público-alvo deste documento é o autor do controle, não os autores de estilo.  
  
  <a name="Terminology"></a>   
## <a name="terminology"></a>Terminologia  
 "Definição de estilo e de modelo" refere-se ao conjunto de tecnologias que permitem que um autor de controle adie os aspectos visuais do controle para o estilo e o modelo do controle. Este conjunto de tecnologias inclui:  
  
-   Estilos (incluindo setters de propriedade, gatilhos e storyboards).  
  
-   Recursos.  
  
-   Modelos de controle.  
  
-   Modelos de dados.  
  
 Para obter uma introdução à definição de estilo e de modelo, consulte [Styling and Templating](styling-and-templating.md) (Definição de estilo e de modelo).  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## <a name="before-you-start-understanding-your-control"></a>Antes de começar: Entendendo seu controle  
 Antes de começarmos com essas diretrizes, é importante compreender e definir o uso comum do seu controle. A definição de estilo expõe um conjunto geralmente irregular de possibilidades. Controles que são escritos para serem usados amplamente (em vários aplicativos, por vários desenvolvedores) enfrentam o desafio de que os estilos possam ser usados para fazer alterações de grande alcance na aparência visual do controle. Na verdade, o controle com estilo aplicado nem sempre se parece com a intenção do autor do controle. Como a flexibilidade oferecida pela definição de estilo é essencialmente ilimitada, você pode usar o conceito de uso comum para ajudá-lo a definir o escopo de suas decisões.  
  
 Para entender o uso comum do controle, é bom pensar sobre a proposta de valor do controle. O que seu controle tem de especial que nenhum outro controle pode oferecer? O uso comum não implica nenhuma aparência visual específica, mas sim a filosofia do controle e um conjunto razoável de expectativas sobre seu uso. Essa compreensão permite que você faça algumas suposições sobre o modelo de composição e os comportamentos definidos pelo estilo do controle no caso comum. No caso de <xref:System.Windows.Controls.ComboBox>, por exemplo, Noções básicas sobre o uso comum não dará nenhuma informação sobre se um determinado <xref:System.Windows.Controls.ComboBox> tem cantos arredondados, mas ele fornecerá informações sobre o fato de que o <xref:System.Windows.Controls.ComboBox> provavelmente precisa de uma janela pop-up e alguma forma de alternância se ele é aberto.  
  
<a name="General_Guidelines"></a>   
## <a name="general-guidelines"></a>Diretrizes gerais  
  
-   **Não imponha rigorosamente os contratos de modelos.** O contrato de modelo de um controle pode consistir em elementos, comandos, associações, gatilhos ou mesmo configurações de propriedade que são necessários ou esperados para que um controle funcione corretamente.  
  
    -   Minimize os contratos o máximo possível.  
  
    -   Crie em torno da expectativa de que durante o tempo de design (ou seja, ao usar uma ferramenta de design) é comum que um modelo de controle esteja em um estado incompleto. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não oferece uma infra-estrutura de estado "composição", portanto, os controles precisam ser criados com a expectativa de que tal estado pode ser válido.  
  
    -   Não lance exceções quando algum aspecto de um contrato de modelo não é seguido. Da mesma forma, os painéis não deverão lançar exceções se tiverem muitos ou poucos filhos.  
  
-   **Fatore funcionalidades periféricas em elementos auxiliares de modelo.** Cada controle deve ser focado em sua funcionalidade principal e em sua real proposta de valor e deve ser definido pelo uso comum do controle. Para essa finalidade, use elementos de composição e auxiliares dentro do modelo para habilitar comportamentos e visualizações periféricos, ou seja, os comportamentos e as visualizações que não contribuem para a funcionalidade principal do controle. Os elementos auxiliares enquadram-se em três categorias:  
  
    -   Os tipos auxiliares **autônomos** são controles públicos e reutilizáveis ou primitivos que são usados "anonimamente" em um modelo, o que significa que nem o elemento auxiliar nem o controle com estilo está ciente um do outro. Tecnicamente, qualquer elemento pode ser um tipo anônimo, mas nesse contexto o termo descreve os tipos que encapsulam funcionalidades especializadas para habilitar cenários de destino.  
  
    -   Os elementos auxiliares **baseados em tipo** são novos tipos que encapsulam funcionalidades especializadas. Esses elementos são normalmente criados com um intervalo mais estreito de funcionalidade do que os controles comuns ou primitivos. Diferentemente dos elementos auxiliares autônomos, os elementos auxiliares baseados em tipo conseguem reconhecer o contexto no qual são usados e geralmente devem compartilhar dados com o controle a cujo modelo pertencem.  
  
    -   Elementos auxiliares **nomeados** são controles comuns ou primitivos que um controle espera encontrar em seu modelo, por nome. Esses elementos recebem um nome conhecido dentro do modelo, tornando possível que um controle encontre o elemento e interaja com ele de forma programática. Pode haver apenas um elemento com um determinado nome em qualquer modelo.  
  
     A tabela a seguir mostra elementos auxiliares empregados por estilos de controle atualmente (essa lista não está completa):  
  
    |Elemento|Tipo|Usado por|  
    |-------------|----------|-------------|  
    |<xref:System.Windows.Controls.ContentPresenter>|Baseado em tipo|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>e assim por diante (todos os <xref:System.Windows.Controls.ContentControl> tipos)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|Baseado em tipo|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>e assim por diante (todos os <xref:System.Windows.Controls.ItemsControl> tipos)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Nomeado|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|Autônomo|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>e assim por diante|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|Nomeado|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>e assim por diante|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|Nomeado|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|Autônomo|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>e assim por diante|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|Autônomo|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|Nomeado|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|Baseado em tipo|<xref:System.Windows.Controls.Slider>|  
  
-   **Minimize as associações ou configurações de propriedade especificadas pelo usuário necessárias nos elementos auxiliares**. É comum que um elemento auxiliar exija determinadas associações ou configurações de propriedade para funcionar corretamente no modelo do controle. O elemento auxiliar e o controle de modelo devem, tanto quanto possível, estabelecer essas configurações. Ao definir propriedades ou estabelecer associações, tome cuidado para não substituir os valores definidos pelo usuário. As práticas recomendadas específicas são as seguintes:  
  
    -   Os elementos auxiliares nomeados devem ser identificados pelo pai e o pai deve estabelecer qualquer configuração necessária no elemento auxiliar.  
  
    -   Os elementos auxiliares baseados em tipo devem estabelecer as configurações necessárias diretamente neles mesmos. Isso pode exigir que o elemento auxiliar consulte o contexto de informações no qual está sendo usado, incluindo seu `TemplatedParent` (o tipo de controle do modelo no qual ele está sendo usado). Por exemplo, <xref:System.Windows.Controls.ContentPresenter> associa automaticamente a `Content` propriedade de seus `TemplatedParent` para sua <xref:System.Windows.Controls.ContentPresenter.Content%2A> propriedade quando usado em um <xref:System.Windows.Controls.ContentControl> tipo derivado.  
  
    -   Os elementos auxiliares autônomos não podem ser otimizados dessa maneira porque, por definição, nem o elemento auxiliar nem o pai sabem da existência um do outro.  
  
-   **Use a propriedade Name para sinalizar elementos em um modelo**. Um controle que precisa localizar um elemento no seu estilo para acessá-lo de forma programática deve fazer isso usando a propriedade `Name` e o paradigma `FindName`. Um controle não deve lançar uma exceção quando um elemento não for encontrado, mas desabilitar silenciosamente e cuidadosamente a funcionalidade que exigia esse elemento.  
  
-   **Use as práticas recomendadas para expressar o estado do controle e comportamento em um estilo.** O seguinte é uma lista ordenada de práticas recomendadas para expressar alterações de estado e o comportamento do controle em um estilo. Você deve usar o primeiro item na lista que permite seu cenário.  
  
    1.  Associação de propriedade. Exemplo: associação entre <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> e <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.  
  
    2.  Alterações de propriedade ou animações de propriedade disparadas. Exemplo: o estado de focalização de uma <xref:System.Windows.Controls.Button>.  
  
    3.  Comando. Exemplo: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand>  /  <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> em <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
    4.  Elementos auxiliares autônomos. Exemplo: <xref:System.Windows.Controls.Primitives.TabPanel> em <xref:System.Windows.Controls.TabControl>.  
  
    5.  Tipos auxiliares baseados em tipo. Exemplo: <xref:System.Windows.Controls.ContentPresenter> na <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> em <xref:System.Windows.Controls.Slider>.  
  
    6.  Elementos auxiliares nomeados. Exemplo: <xref:System.Windows.Controls.TextBox> em <xref:System.Windows.Controls.ComboBox>.  
  
    7.  Eventos de bolhas de tipos auxiliares nomeados. Se você escutar eventos de bolhas de um elemento de estilo, exija que o elemento que gera o evento seja identificado exclusivamente. Exemplo: <xref:System.Windows.Controls.Primitives.Thumb> em <xref:System.Windows.Controls.ToolBar>.  
  
    8.  Comportamento de `OnRender` personalizado. Exemplo: <xref:Microsoft.Windows.Themes.ButtonChrome> em <xref:System.Windows.Controls.Button>.  
  
-   **Use gatilhos de estilo (em vez de gatilhos de modelo) com moderação**. Os gatilhos que afetam propriedades em elementos de modelo devem ser declarados no modelo. Os gatilhos que afetam propriedades no controle (sem `TargetName`) podem ser declarados no estilo, a menos que você saiba que a alteração do modelo também deverá destruir o gatilho.  
  
-   **Seja consistente com os padrões de estilo existente.** Muitas vezes existem várias maneiras de resolver um problema. Esteja atento a isso e, quando possível, consistente com os padrões existentes de definição de estilo de controle. Isso é especialmente importante para controles que derivam do mesmo tipo base (por exemplo, <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>e assim por diante).  
  
-   **Exponha propriedades para habilitar cenários comuns de personalização sem redefinição de modelo**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não oferece suporte a partes plugáveis/personalizáveis, portanto, um usuário de controle é deixado com apenas dois métodos de personalização: definir propriedades diretamente ou definir propriedades usando estilos. Com isso em mente, é apropriado definir um número limitado de propriedades direcionadas a cenários de personalização muito comuns e de alta prioridade que normalmente exigiriam a redefinição de modelo. Aqui estão as práticas recomendadas para quando e como habilitar cenários de personalização:  
  
    -   As personalizações muito comuns devem ser expostas como propriedades no controle e consumidas pelo modelo.  
  
    -   As personalizações menos comuns (embora não raras) devem ser expostas como propriedades anexadas e consumidas pelo modelo.  
  
    -   É aceitável que as personalizações conhecidas, mas raras exijam redefinição de modelo.  
  
<a name="Theme_Considerations"></a>   
## <a name="theme-considerations"></a>Considerações de tema  
  
-   **Os estilos de tema devem tentar ter uma semântica de propriedade consistente em todos os temas, mas não oferecer garantia**. Como parte de sua documentação, o controle deve ter um documento que descreva a semântica de propriedade do controle, ou seja, o "significado" de uma propriedade para um controle. Por exemplo, o <xref:System.Windows.Controls.ComboBox> controle deve definir o significado do <xref:System.Windows.Controls.Control.Background%2A> propriedade dentro de <xref:System.Windows.Controls.ComboBox>. Os estilos padrão do controle devem tentar seguir a semântica definida nesse documento para todos os temas. Por outro lado, os usuários do controle devem estar cientes de que a semântica de propriedade pode mudar de tema para tema. Em alguns casos, uma determinada propriedade talvez não possa ser expressada sob as restrições visuais exigidas por um tema específico. (O tema clássico, por exemplo, não tem uma borda única para que `Thickness` possa ser aplicado a vários controles.)  
  
-   **Os estilos de tema não precisam ter a semântica de gatilho consistente entre todos os temas**. O comportamento exposto por um estilo de controle por meio de gatilhos ou animações pode variar de tema para tema. Os usuários do controle devem estar cientes de que um controle não vai necessariamente empregar o mesmo mecanismo para atingir um determinado comportamento em todos os temas. Um tema, por exemplo, pode usar uma animação para expressar o comportamento de focalização enquanto outro tema usa um gatilho. Isso pode resultar em inconsistências na preservação do comportamento em controles personalizados. (Alterar a propriedade de tela de fundo, por exemplo, poderá não afetar o estado de focalização do controle se esse estado for expresso usando um gatilho. No entanto, se o estado de focalização for implementado usando uma animação, alterar a tela de fundo poderá interromper irremediavelmente a animação e, portanto, a transição de estado.)  
  
-   **Os estilos de tema não precisam ter a semântica de "layout" consistente entre todos os temas**. Por exemplo, o estilo padrão não precisa garantir que um controle ocupará a mesma quantidade de tamanho em todos os temas ou garantir que um controle terá as mesmas margens de conteúdo/preenchimento em todos os temas.  
  
## <a name="see-also"></a>Consulte também

- [Estilo e modelagem](styling-and-templating.md)
- [Visão geral da criação de controle](control-authoring-overview.md)

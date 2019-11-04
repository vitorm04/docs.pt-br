---
title: Metadados de propriedade de estrutura
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 3e40dfbcbe88f424337ee5a32fb3e3aaaddd68d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460458"
---
# <a name="framework-property-metadata"></a>Metadados de propriedade de estrutura
Opções de metadados de propriedades de Framework são relatadas para as propriedades dos elementos de objeto consideradas a nível de estrutura do WPF na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] arquitetura. Em geral, a designação no nível de estrutura do WPF envolve que recursos como renderização, vinculação de dados e refinamentos do sistema de propriedades são tratados pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de APIs de apresentação e executáveis. Metadados de propriedade de estrutura é consultado por esses sistemas para determinar características específicas de recurso de propriedades de elemento específico.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Este tópico pressupõe que você entende as propriedades de dependência da perspectiva de um consumidor de propriedades de dependência existentes em classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e leu a [Visão geral das propriedades de dependência](dependency-properties-overview.md). Você também deve ter lido [metadados de propriedade de dependência](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>O que é comunicado por metadados de propriedades de estrutura  
 Metadados de propriedade de estrutura podem ser divididos nas seguintes categorias:  
  
- Propriedades de layout de relatório que afetam um elemento (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Você pode definir esses sinalizadores nos metadados se a propriedade afetar esses respectivos aspectos, e se você também estiver implementando os métodos <xref:System.Windows.FrameworkElement.MeasureOverride%2A> / <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> em sua classe para fornecer comportamento de renderização e informações específicas para o sistema de layout. Normalmente, tal implementação deve verificar para invalidações de propriedade nas propriedades de dependência em que qualquer uma dessas propriedades de layout eram "verdadeiras" nos metadados de propriedade e somente essas exigiriam uma solicitação de uma nova passagem de layout.  
  
- Propriedades de layout de relatório que afetam o elemento pai de um elemento (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Alguns exemplos em que esses sinalizadores são definidos por padrão são <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> e <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> Por padrão, as propriedades de dependência não herdam valores. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> permite que o caminho da herança também viaje em uma árvore visual, o que é necessário para alguns cenários de composição de controle.  
  
    > [!NOTE]
    > O termo "herda" no contexto de valores de propriedade significa algo específico para propriedades de dependência; Isso significa que elementos filho podem herdar o valor da propriedade de dependência real de elementos pai por causa de uma funcionalidade de nível de estrutura WPF do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de propriedade. Não tem nada a ver diretamente com herança de tipo e membros de código gerenciado por tipos derivados. Para obter detalhes, consulte [Herança do valor da propriedade](property-value-inheritance.md).  
  
- Características de associação de dados de relatório (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Por padrão, as propriedades de dependência na estrutura dão suporte à vinculação de dados, com um comportamento de associação unidirecional. Você pode desabilitar a vinculação de dados se não houvesse nenhum cenário para ela (porque elas devem ser flexíveis e extensíveis, não há muitos exemplos dessas propriedades nas APIs de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão). Você pode definir a associação para ter um padrão bidirecional para propriedades que unem os comportamentos de um controle entre suas partes de componente (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> é um exemplo) ou onde a associação bidirecional é o cenário comum e esperado para os usuários (<xref:System.Windows.Controls.TextBox.Text%2A> é um exemplo). Alterar os metadados relacionados a vinculação de dados somente influencia o padrão; em uma base por associação esse padrão sempre pode ser alterado. Para obter detalhes sobre modos de associação e associação em geral, consulte [visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Relatando se as propriedades devem ser registradas em diário por aplicativos ou serviços que dão suporte ao registro em diário (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Para elementos gerais, o registro no diário não está habilitado por padrão, mas ele é habilitado seletivamente para certos controles de entrada do usuário. Esta propriedade destina-se a ser lida pelos serviços de diário incluindo a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementação do registro no diário e normalmente é definida em controles de usuário, como seleções pelo usuário em listas que devem ser persistentes entre etapas de navegação. Para obter informações sobre o diário, consulte [visão geral da navegação](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Leitura do FrameworkPropertyMetadata  
 Cada uma das propriedades vinculadas acima são as propriedades específicas que o <xref:System.Windows.FrameworkPropertyMetadata> adiciona à sua classe base imediata <xref:System.Windows.UIPropertyMetadata>. Cada uma dessas propriedades será `false`, por padrão. Uma solicitação de metadados para uma propriedade em que saber o valor dessas propriedades é importante deve tentar converter os metadados retornados para <xref:System.Windows.FrameworkPropertyMetadata>e, em seguida, verificar os valores das propriedades individuais, conforme necessário.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Especificação dos metadados  
 Quando você cria uma nova instância de metadados para fins de aplicação de metadados a um novo registro de propriedade de dependência, você tem a opção de qual classe de metadados usar: o <xref:System.Windows.PropertyMetadata> base ou alguma classe derivada, como <xref:System.Windows.FrameworkPropertyMetadata>. Em geral, você deve usar <xref:System.Windows.FrameworkPropertyMetadata>, especialmente se sua propriedade tiver qualquer interação com o sistema de propriedades e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funções como layout e vinculação de dados. Outra opção para cenários mais sofisticados é derivar de <xref:System.Windows.FrameworkPropertyMetadata> para criar sua própria classe de relatórios de metadados com informações extras transportadas em seus membros. Ou você pode usar <xref:System.Windows.PropertyMetadata> ou <xref:System.Windows.UIPropertyMetadata> para comunicar o grau de suporte para recursos de sua implementação.  
  
 Para propriedades existentes (<xref:System.Windows.DependencyProperty.AddOwner%2A> ou <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> chamada), você sempre deve substituir pelo tipo de metadados usado pelo registro original.  
  
 Se você estiver criando uma instância de <xref:System.Windows.FrameworkPropertyMetadata>, há duas maneiras de popular os metadados com valores para as propriedades específicas que comunicam as características da propriedade da estrutura:  
  
1. Use a assinatura do Construtor <xref:System.Windows.FrameworkPropertyMetadata> que permite um parâmetro `flags`. Esse parâmetro deve ser preenchido com todos os valores combinados desejados dos sinalizadores de enumeração <xref:System.Windows.FrameworkPropertyMetadataOptions>.  
  
2. Use uma das assinaturas sem um parâmetro `flags` e, em seguida, defina cada propriedade booliana de relatório em <xref:System.Windows.FrameworkPropertyMetadata> como `true` para cada alteração de característica desejada. Se você fizer isso, você deverá definir essas propriedades antes de quaisquer elementos com esta propriedade de dependência sejam construídos; as propriedades boolianas são leitura / gravação para permitir que esse comportamento de evitar o `flags` parâmetro e ainda preencher os metadados, mas os metadados devem ficar efetivamente selados antes de usar a propriedade. Assim, a tentativa de definir as propriedades, depois de solicitar os metadados, será uma operação inválida.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Comportamento de mesclagem de metadados de propriedades de estrutura  
 Quando você substitui metadados de propriedade de estrutura, as diferentes características dos metadados são mescladas ou substituídas.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> é mesclado. Se você adicionar um novo <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, esse retorno de chamada será armazenado nos metadados. Se você não especificar um <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> na substituição, o valor de <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> será promovido como uma referência do ancestral mais próximo que o especificou nos metadados.  
  
- O comportamento real do sistema de propriedades para <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> é que as implementações de todos os proprietários de metadados na hierarquia são retidas e adicionadas a uma tabela, com a ordem de execução pelo sistema de propriedades sendo que os retornos de chamada da classe derivada mais profunda são invocados primeiro. Retornos de chamada herdados são executados somente uma vez, contando como sendo pertencente a classe que colocou-os nos metadados.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A> é substituído. Se você não especificar um <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> na substituição, o valor de <xref:System.Windows.PropertyMetadata.DefaultValue%2A> será proveniente do ancestral mais próximo que o especificou nos metadados.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementações são substituídas. Se você adicionar um novo <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, esse retorno de chamada será armazenado nos metadados. Se você não especificar um <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> na substituição, o valor de <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> será promovido como uma referência do ancestral mais próximo que o especificou nos metadados.  
  
- O comportamento do sistema de propriedades é que apenas o <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> nos metadados imediatos é invocado. Nenhuma referência a outras implementações de <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> na hierarquia é mantida.  
  
- Os sinalizadores de enumeração de <xref:System.Windows.FrameworkPropertyMetadataOptions> são combinados como uma operação OR bit a bit.  Se você especificar <xref:System.Windows.FrameworkPropertyMetadataOptions>, as opções originais não serão substituídas.  Para alterar uma opção, defina a propriedade correspondente em <xref:System.Windows.FrameworkPropertyMetadata>. Por exemplo, se o objeto <xref:System.Windows.FrameworkPropertyMetadata> original definir o sinalizador <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType>, você poderá alterar isso definindo <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> como `false`.  
  
 Esse comportamento é implementado por <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>e pode ser substituído em classes de metadados derivadas.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadados de propriedade da dependência](dependency-property-metadata.md)
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)

---
title: Metadados de propriedade de estrutura
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 8fb6e1b4cf6aed9454e9e9f1a77277d2f3611ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186648"
---
# <a name="framework-property-metadata"></a>Metadados de propriedade de estrutura
Opções de metadados de propriedades de Framework são relatadas para as propriedades dos elementos de objeto consideradas a nível de estrutura do WPF na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] arquitetura. Em geral, a designação em nível de quadro do WPF implica que recursos como renderização, vinculação de dados e refinamentos do sistema de propriedade são tratados pelas APIs de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apresentação e executáveis. Metadados de propriedade de estrutura é consultado por esses sistemas para determinar características específicas de recurso de propriedades de elemento específico.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você entende as propriedades de dependência da perspectiva de um consumidor de propriedades de dependência existentes nas classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e que leu a [Visão geral das propriedades de dependência](dependency-properties-overview.md). Você também deve ter lido [metadados de propriedade de dependência](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>
## <a name="what-is-communicated-by-framework-property-metadata"></a>O que é comunicado por metadados de propriedades de estrutura  
 Metadados de propriedade de estrutura podem ser divididos nas seguintes categorias:  
  
- Emissão de relatórios<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>de <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>propriedades de layout que afetam um elemento ( , , ). Você pode definir esses sinalizadores em metadados se a propriedade afetar esses <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> respectivos aspectos, e também está implementando os métodos em sua classe para fornecer comportamento de renderização e informações específicos para o sistema de layout. Normalmente, tal implementação deve verificar para invalidações de propriedade nas propriedades de dependência em que qualquer uma dessas propriedades de layout eram "verdadeiras" nos metadados de propriedade e somente essas exigiriam uma solicitação de uma nova passagem de layout.  
  
- Emissão de relatórios de propriedades<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>de <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>layout que afetam o elemento pai de um elemento ( ). Alguns exemplos em que essas <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> bandeiras são definidas por padrão são e <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Por padrão, as propriedades de dependência não herdam valores. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>permite que o caminho da herança também viaje para uma árvore visual, o que é necessário para alguns cenários de composição de controle.  
  
    > [!NOTE]
    > O termo "herda" no contexto de valores de propriedade significa algo específico para propriedades de dependência; Isso significa que elementos filho podem herdar o valor da propriedade de dependência real de elementos pai por causa de uma funcionalidade de nível de estrutura WPF do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de propriedade. Não tem nada a ver diretamente com herança de tipo e membros de código gerenciado por tipos derivados. Para obter detalhes, consulte [Herança do valor da propriedade](property-value-inheritance.md).  
  
- Relatório de características<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A> <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>de vinculação de dados ( , ). Por padrão, as propriedades de dependência na estrutura dão suporte à vinculação de dados, com um comportamento de associação unidirecional. Você pode desativar a vinculação de dados se não houver qualquer cenário para ele (porque eles são destinados a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ser flexíveis e extensíveis, não há muitos exemplos de tais propriedades nas APIs padrão). Você pode definir vinculação para ter um padrão bidirecional para propriedades que unem os comportamentos de um controle entre suas peças componentes (é<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> um exemplo) ou onde a vinculação bidirecional é o cenário comum e esperado para os usuários (é<xref:System.Windows.Controls.TextBox.Text%2A> um exemplo). Alterar os metadados relacionados a vinculação de dados somente influencia o padrão; em uma base por associação esse padrão sempre pode ser alterado. Para obter detalhes sobre modos de associação e associação em geral, consulte [visão geral de vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Informando se as propriedades devem ser revistas por<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>aplicativos ou serviços que suportam o journaling ( ). Para elementos gerais, o registro no diário não está habilitado por padrão, mas ele é habilitado seletivamente para certos controles de entrada do usuário. Esta propriedade destina-se a ser lida pelos serviços de diário incluindo a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementação do registro no diário e normalmente é definida em controles de usuário, como seleções pelo usuário em listas que devem ser persistentes entre etapas de navegação. Para obter informações sobre o diário, consulte [visão geral da navegação](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>
## <a name="reading-frameworkpropertymetadata"></a>Leitura do FrameworkPropertyMetadata  
 Cada uma das propriedades vinculadas acima <xref:System.Windows.FrameworkPropertyMetadata> são as propriedades <xref:System.Windows.UIPropertyMetadata>específicas que o adiciona à sua classe base imediata . Cada uma dessas propriedades será `false`, por padrão. Uma solicitação de metadados para uma propriedade onde saber o valor dessas propriedades <xref:System.Windows.FrameworkPropertyMetadata>é importante deve tentar lançar os metadados devolvidos e, em seguida, verificar os valores das propriedades individuais conforme necessário.  
  
<a name="Specifying_Metadata"></a>
## <a name="specifying-metadata"></a>Especificação dos metadados  
 Quando você cria uma nova instância de metadados para fins de aplicação de metadados a um novo registro <xref:System.Windows.PropertyMetadata> de propriedade de <xref:System.Windows.FrameworkPropertyMetadata>dependência, você tem a escolha de qual classe de metadados usar: a base ou alguma classe derivada, como . Em geral, você <xref:System.Windows.FrameworkPropertyMetadata>deve usar, especialmente se sua [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedade tiver alguma interação com o sistema de propriedade e funções como layout e vinculação de dados. Outra opção para cenários mais <xref:System.Windows.FrameworkPropertyMetadata> sofisticados é derivar para criar sua própria classe de relatórios de metadados com informações extras transportadas em seus membros. Ou você <xref:System.Windows.PropertyMetadata> pode <xref:System.Windows.UIPropertyMetadata> usar ou comunicar o grau de suporte para recursos de sua implementação.  
  
 Para propriedades existentes<xref:System.Windows.DependencyProperty.AddOwner%2A> <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> (ou chamada), você deve sempre substituir com o tipo de metadados usado pelo registro original.  
  
 Se você estiver <xref:System.Windows.FrameworkPropertyMetadata> criando uma instância, há duas maneiras de preencher esses metadados com valores para as propriedades específicas que comunicam as características da propriedade-framework:  
  
1. Use <xref:System.Windows.FrameworkPropertyMetadata> a assinatura do `flags` construtor que permite um parâmetro. Este parâmetro deve ser preenchido com todos os <xref:System.Windows.FrameworkPropertyMetadataOptions> valores combinados desejados das bandeiras de enumeração.  
  
2. Use uma das assinaturas `flags` sem um parâmetro e, em <xref:System.Windows.FrameworkPropertyMetadata> `true` seguida, defina cada propriedade booleana de relatório para cada mudança característica desejada. Se você fizer isso, você deverá definir essas propriedades antes de quaisquer elementos com esta propriedade de dependência sejam construídos; as propriedades boolianas são leitura / gravação para permitir que esse comportamento de evitar o `flags` parâmetro e ainda preencher os metadados, mas os metadados devem ficar efetivamente selados antes de usar a propriedade. Assim, a tentativa de definir as propriedades, depois de solicitar os metadados, será uma operação inválida.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>
## <a name="framework-property-metadata-merge-behavior"></a>Comportamento de mesclagem de metadados de propriedades de estrutura  
 Quando você substitui metadados de propriedade de estrutura, as diferentes características dos metadados são mescladas ou substituídas.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>é fundido. Se você adicionar <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>um novo, esse retorno de chamada será armazenado nos metadados. Se você não <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> especificar um na substituição, o valor de <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> é promovido como uma referência do ancestral mais próximo que o especificou em metadados.  
  
- O comportamento real <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> do sistema de propriedade é que as implementações para todos os proprietários de metadados na hierarquia são retidas e adicionadas a uma tabela, com ordem de execução pelo sistema de propriedade sendo que os retornos de chamada da classe mais profundamente derivada são invocados primeiro. Retornos de chamada herdados são executados somente uma vez, contando como sendo pertencente a classe que colocou-os nos metadados.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>é substituído. Se você não <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> especificar um na substituição, o valor vem do <xref:System.Windows.PropertyMetadata.DefaultValue%2A> ancestral mais próximo que o especificou em metadados.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementações são substituídas. Se você adicionar <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>um novo, esse retorno de chamada será armazenado nos metadados. Se você não <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> especificar um na substituição, o valor de <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> é promovido como uma referência do ancestral mais próximo que o especificou em metadados.  
  
- O comportamento do sistema <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> de propriedade é que apenas os metadados imediatos são invocados. Não são mantidas referências a outras <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementações na hierarquia.  
  
- As bandeiras de <xref:System.Windows.FrameworkPropertyMetadataOptions> enumeração são combinadas como uma operação or pouco sábia.  Se você <xref:System.Windows.FrameworkPropertyMetadataOptions>especificar, as opções originais não serão substituídas.  Para alterar uma opção, defina a propriedade correspondente em <xref:System.Windows.FrameworkPropertyMetadata>. Por exemplo, se <xref:System.Windows.FrameworkPropertyMetadata> o <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> objeto original definir o <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> sinalizador, você pode alterá-lo definindo-o para `false`.  
  
 Esse comportamento é <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>implementado por , e pode ser substituído em classes de metadados derivadas.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadados de propriedade da dependência](dependency-property-metadata.md)
- [Visão geral das propriedades de dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)

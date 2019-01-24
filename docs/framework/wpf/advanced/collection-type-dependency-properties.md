---
title: Propriedades de dependência do tipo de coleção
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
ms.openlocfilehash: 21f260262d434ffe3685b226193f2d6cd2125549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548424"
---
# <a name="collection-type-dependency-properties"></a>Propriedades de dependência do tipo de coleção
Este tópico fornece diretrizes e padrões sugeridos para como implementar uma propriedade de dependência em que o tipo da propriedade é um tipo de coleção.  
  
 
  
<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Implementando uma Propriedade de Dependência do Tipo de Coleção  
 Para uma propriedade de dependência em geral, a implementação padrão que você segue é que você define uma [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] wrapper de propriedade, em que essa propriedade é feita por um <xref:System.Windows.DependencyProperty> identificador em vez de um campo ou outro constructo. Você segue esse mesmo padrão quando implementa uma propriedade de tipo de coleção. No entanto, uma propriedade do tipo coleção apresenta alguma complexidade ao padrão sempre que o tipo que está contido dentro da coleção é em si uma <xref:System.Windows.DependencyObject> ou <xref:System.Windows.Freezable> classe derivada.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicializando a coleção além do valor padrão  
 Quando você cria uma propriedade de dependência, você não especificar o valor padrão da propriedade como o valor do campo inicial. Em vez disso, você pode especificar o valor padrão por meio de metadados de propriedade de dependência. Se a propriedade for um tipo de referência, o valor padrão especificado nos metadados de propriedade de dependência não será um valor padrão por instância; em vez disso, será um valor padrão que se aplica a todas as instâncias do tipo. Portanto, você deve ter cuidado para não usar a coleção estática singular definida pelos metadados de propriedade de coleção como o valor padrão de trabalho para instâncias recém-criadas do seu tipo. Em vez disso, você deve verificar se definiu deliberadamente o valor da coleção para uma coleção exclusiva (instância) como parte da lógica do construtor de classe. Caso contrário, você terá criado uma classe singleton não intencional.  
  
 Considere o exemplo a seguir. A seção do exemplo a seguir mostra a definição da classe `Aquarium`. A classe define a propriedade de dependência do tipo de coleção `AquariumObjects`, que usa genéricos <xref:System.Collections.Generic.List%601> de tipo com um <xref:System.Windows.FrameworkElement> restrição de tipo. No <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> chamadas para a propriedade de dependência, os metadados estabelecem o valor de padrão para um novo genérico <xref:System.Collections.Generic.List%601>.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 No entanto, se você apenas deixar o código como mostrado, aquele valor padrão de lista será compartilhado para todas as instâncias de `Aquarium`. Se você tiver executado o seguinte código de teste, que destina-se a mostrar como você poderia instanciar duas instâncias separadas de `Aquarium` e adicionado um único `Fish` diferente para cada um deles, você verá um resultado surpreendente:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Em vez de cada coleção ter uma contagem de um, cada conjunto possui uma contagem de dois. Isso ocorre porque cada `Aquarium` adicionou `Fish` à coleção de valores padrão, o que resultou de uma única chamada a construtor nos metadados e, portanto, é compartilhado entre todas as instâncias. Essa situação quase nunca é o que você deseja.  
  
 Para corrigir esse problema, você deve redefinir o valor da propriedade de dependência da coleção para uma instância única, como parte da chamada do construtor de classe. Como a propriedade é uma propriedade de dependência somente leitura, use o <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> método para defini-la, usando o <xref:System.Windows.DependencyPropertyKey> que é acessível somente dentro da classe.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Agora, se você executasse novamente esse mesmo código de teste, você poderia ver resultados mais esperados, no qual cada `Aquarium` daria suporte à sua própria coleção única.  
  
 Haveria uma variação pequena nesse padrão se você optasse por ter sua propriedade da coleção a ser leitura/gravação. Nesse caso, você poderia chamar o acessador set públicos a partir do construtor para fazer a inicialização, o que ainda seria chamar a assinatura sem chave de <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> dentro de seu wrapper de conjunto, usando uma pública <xref:System.Windows.DependencyProperty> identificador.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Relatório de alterações de valor de associação de propriedades de coleção  
 Uma propriedade de coleção que é uma propriedade de dependência não relata automaticamente alterações para suas subpropriedades. Se você estiver criando vínculos em uma coleção, isso poderá impedir que a associação relate alterações, portanto invalidando alguns cenários de vinculação de dados. No entanto, se você usar o tipo de coleção <xref:System.Windows.FreezableCollection%601> como seu tipo de coleção, em seguida, alterações de subpropriedades em elementos contidos na coleção serão relatadas corretamente e a associação funciona conforme o esperado.  
  
 Para habilitar a associação de subpropriedade em uma coleção de objetos de dependência, crie a propriedade de coleção como tipo <xref:System.Windows.FreezableCollection%601>, com uma restrição de tipo para essa coleção para qualquer <xref:System.Windows.DependencyObject> classe derivada.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.FreezableCollection%601>
- [XAML e classes personalizadas para WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [Propriedades de dependência personalizada](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [Metadados de propriedade da dependência](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)

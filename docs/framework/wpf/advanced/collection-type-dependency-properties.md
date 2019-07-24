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
ms.openlocfilehash: dd268c0c132f4ecefe7b2336432442d9569ca38f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401559"
---
# <a name="collection-type-dependency-properties"></a>Propriedades de dependência do tipo de coleção
Este tópico fornece diretrizes e padrões sugeridos para como implementar uma propriedade de dependência em que o tipo da propriedade é um tipo de coleção.  

<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Implementando uma Propriedade de Dependência do Tipo de Coleção  
 Para uma propriedade de dependência em geral, o padrão de implementação que você segue é definir um wrapper de propriedade CLR, em que essa propriedade é apoiada <xref:System.Windows.DependencyProperty> por um identificador em vez de um campo ou outro constructo. Você segue esse mesmo padrão quando implementa uma propriedade de tipo de coleção. No entanto, uma propriedade do tipo coleção apresenta alguma complexidade ao padrão sempre que o tipo contido na coleção é a <xref:System.Windows.DependencyObject> própria classe ou <xref:System.Windows.Freezable> derivada.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicializando a coleção além do valor padrão  
 Quando você cria uma propriedade de dependência, você não especificar o valor padrão da propriedade como o valor do campo inicial. Em vez disso, você pode especificar o valor padrão por meio de metadados de propriedade de dependência. Se a propriedade for um tipo de referência, o valor padrão especificado nos metadados de propriedade de dependência não será um valor padrão por instância; em vez disso, será um valor padrão que se aplica a todas as instâncias do tipo. Portanto, você deve ter cuidado para não usar a coleção estática singular definida pelos metadados de propriedade de coleção como o valor padrão de trabalho para instâncias recém-criadas do seu tipo. Em vez disso, você deve verificar se definiu deliberadamente o valor da coleção para uma coleção exclusiva (instância) como parte da lógica do construtor de classe. Caso contrário, você terá criado uma classe singleton não intencional.  
  
 Considere o exemplo a seguir. A seção do exemplo a seguir mostra a definição da classe `Aquarium`. A classe define a propriedade `AquariumObjects`de dependência de tipo de coleção, que usa o tipo genérico <xref:System.Collections.Generic.List%601> com uma restrição de <xref:System.Windows.FrameworkElement> tipo. Na chamada para a propriedade de dependência, os metadados estabelecem o valor padrão como um novo genérico <xref:System.Collections.Generic.List%601>. <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29>  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 No entanto, se você apenas deixar o código como mostrado, aquele valor padrão de lista será compartilhado para todas as instâncias de `Aquarium`. Se você tiver executado o seguinte código de teste, que destina-se a mostrar como você poderia instanciar duas instâncias separadas de `Aquarium` e adicionado um único `Fish` diferente para cada um deles, você verá um resultado surpreendente:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Em vez de cada coleção ter uma contagem de um, cada conjunto possui uma contagem de dois. Isso ocorre porque cada `Aquarium` adicionou `Fish` à coleção de valores padrão, o que resultou de uma única chamada a construtor nos metadados e, portanto, é compartilhado entre todas as instâncias. Essa situação quase nunca é o que você deseja.  
  
 Para corrigir esse problema, você deve redefinir o valor da propriedade de dependência da coleção para uma instância única, como parte da chamada do construtor de classe. Como a propriedade é uma propriedade de dependência somente leitura, você usa o <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> método para defini-la, usando <xref:System.Windows.DependencyPropertyKey> o que está acessível somente dentro da classe.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Agora, se você executasse novamente esse mesmo código de teste, você poderia ver resultados mais esperados, no qual cada `Aquarium` daria suporte à sua própria coleção única.  
  
 Haveria uma variação pequena nesse padrão se você optasse por ter sua propriedade da coleção a ser leitura/gravação. Nesse caso, você poderia chamar o acessador set público do construtor para fazer a inicialização, que ainda estaria chamando a assinatura não chave de <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> dentro do wrapper definido, usando um identificador público. <xref:System.Windows.DependencyProperty>  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Relatório de alterações de valor de associação de propriedades de coleção  
 Uma propriedade de coleção que é uma propriedade de dependência não relata automaticamente alterações para suas subpropriedades. Se você estiver criando vínculos em uma coleção, isso poderá impedir que a associação relate alterações, portanto invalidando alguns cenários de vinculação de dados. No entanto, se você usar o <xref:System.Windows.FreezableCollection%601> tipo de coleção como o tipo de coleção, subpropriedade alterações nos elementos contidos na coleção serão relatadas corretamente e a associação funcionará conforme o esperado.  
  
 Para habilitar a associação subpropriedade em uma coleção de objetos de dependência, crie a propriedade <xref:System.Windows.FreezableCollection%601>de coleção como tipo, com uma restrição de tipo <xref:System.Windows.DependencyObject> para essa coleção para qualquer classe derivada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FreezableCollection%601>
- [XAML e classes personalizadas para WPF](xaml-and-custom-classes-for-wpf.md)
- [Visão geral da vinculação de dados](../data/data-binding-overview.md)
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Metadados de propriedade da dependência](dependency-property-metadata.md)

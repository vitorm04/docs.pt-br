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
ms.openlocfilehash: e783ce4b95b52b86671181dfe4b316d4b91d8fc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141530"
---
# <a name="collection-type-dependency-properties"></a>Propriedades de dependência do tipo de coleção
Este tópico fornece diretrizes e padrões sugeridos para como implementar uma propriedade de dependência em que o tipo da propriedade é um tipo de coleção.  

<a name="implementing"></a>
## <a name="implementing-a-collection-type-dependency-property"></a>Implementando uma Propriedade de Dependência do Tipo de Coleção  
 Para uma propriedade de dependência em geral, o padrão de implementação que você segue é <xref:System.Windows.DependencyProperty> que você define um invólucro de propriedade CLR, onde essa propriedade é apoiada por um identificador em vez de um campo ou outra construção. Você segue esse mesmo padrão quando implementa uma propriedade de tipo de coleção. No entanto, uma propriedade do tipo coleção introduz alguma complexidade ao padrão <xref:System.Windows.DependencyObject> sempre <xref:System.Windows.Freezable> que o tipo que está contido dentro da coleção é em si uma classe ou derivada.  
  
<a name="initializing"></a>
## <a name="initializing-the-collection-beyond-the-default-value"></a>Inicializando a coleção além do valor padrão  
 Quando você cria uma propriedade de dependência, você não especificar o valor padrão da propriedade como o valor do campo inicial. Em vez disso, você pode especificar o valor padrão por meio de metadados de propriedade de dependência. Se a propriedade for um tipo de referência, o valor padrão especificado nos metadados de propriedade de dependência não será um valor padrão por instância; em vez disso, será um valor padrão que se aplica a todas as instâncias do tipo. Portanto, você deve ter cuidado para não usar a coleção estática singular definida pelos metadados de propriedade de coleção como o valor padrão de trabalho para instâncias recém-criadas do seu tipo. Em vez disso, você deve verificar se definiu deliberadamente o valor da coleção para uma coleção exclusiva (instância) como parte da lógica do construtor de classe. Caso contrário, você terá criado uma classe singleton não intencional.  
  
 Considere o exemplo a seguir. A seção a seguir do exemplo `Aquarium`mostra a definição de uma classe , que contém uma falha com o valor padrão. A classe define a propriedade `AquariumObjects`de dependência do <xref:System.Collections.Generic.List%601> tipo <xref:System.Windows.FrameworkElement> de coleção, que usa o tipo genérico com uma restrição de tipo. Na <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> chamada para a propriedade de dependência, os metadados estabelecem <xref:System.Collections.Generic.List%601>que o valor padrão é um novo genérico .

> [!WARNING]
> O código a seguir não se comporta corretamente.

 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 No entanto, se você apenas deixar o código como mostrado, aquele valor padrão de lista será compartilhado para todas as instâncias de `Aquarium`. Se você tiver executado o seguinte código de teste, que destina-se a mostrar como você poderia instanciar duas instâncias separadas de `Aquarium` e adicionado um único `Fish` diferente para cada um deles, você verá um resultado surpreendente:  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Em vez de cada coleção ter uma contagem de um, cada conjunto possui uma contagem de dois. Isso ocorre porque cada `Aquarium` adicionou `Fish` à coleção de valores padrão, o que resultou de uma única chamada a construtor nos metadados e, portanto, é compartilhado entre todas as instâncias. Essa situação quase nunca é o que você deseja.  
  
 Para corrigir esse problema, você deve redefinir o valor da propriedade de dependência da coleção para uma instância única, como parte da chamada do construtor de classe. Como a propriedade é uma propriedade de dependência <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> somente leitura, você <xref:System.Windows.DependencyPropertyKey> usa o método para defini-la, usando o que só é acessível dentro da classe.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Agora, se você executasse novamente esse mesmo código de teste, você poderia ver resultados mais esperados, no qual cada `Aquarium` daria suporte à sua própria coleção única.  
  
 Haveria uma variação pequena nesse padrão se você optasse por ter sua propriedade da coleção a ser leitura/gravação. Nesse caso, você pode chamar o acessório de conjunto público do construtor para fazer a <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> inicialização, que ainda estaria <xref:System.Windows.DependencyProperty> chamando a assinatura não-chave de dentro do seu invólucro definido, usando um identificador público.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Relatório de alterações de valor de associação de propriedades de coleção  
 Uma propriedade de coleção que é uma propriedade de dependência não relata automaticamente alterações para suas subpropriedades. Se você estiver criando vínculos em uma coleção, isso poderá impedir que a associação relate alterações, portanto invalidando alguns cenários de vinculação de dados. No entanto, se <xref:System.Windows.FreezableCollection%601> você usar o tipo de coleta como seu tipo de coleta, então as alterações de subpropriedade para elementos contidos na coleção são devidamente relatadas e as obras de vinculação, como esperado.  
  
 Para habilitar a vinculação de subpropriedades em uma <xref:System.Windows.FreezableCollection%601>coleção de objetos de <xref:System.Windows.DependencyObject> dependência, crie a propriedade de coleta como tipo, com uma restrição de tipo para essa coleta para qualquer classe derivada.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.FreezableCollection%601>
- [XAML e classes personalizadas para WPF](xaml-and-custom-classes-for-wpf.md)
- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral das propriedades de dependência](dependency-properties-overview.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Metadados de propriedade da dependência](dependency-property-metadata.md)

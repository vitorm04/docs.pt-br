---
title: Carregamento de XAML e propriedades da dependência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
ms.openlocfilehash: 57c25297f995acd1ef307466258b5f4e03cc3098
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459537"
---
# <a name="xaml-loading-and-dependency-properties"></a>Carregamento de XAML e propriedades da dependência
A implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] atual de seu processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é inerentemente com reconhecimento de propriedade de dependência. O processador [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usa métodos de sistema de propriedade de propriedades de dependência ao carregar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] binários e processar atributos que são propriedades de dependência. Isso desvia os wrappers de propriedade de forma efetiva. Ao implementar propriedades de dependência personalizadas, você deve considerar esse comportamento e evitar colocar qualquer outro código em seu wrapper de propriedade diferente dos métodos do sistema de propriedades <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A>.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Este tópico pressupõe que você entende as propriedades de dependência das perspectivas de um consumidor e criador e que leu os tópicos [Visão Geral das Propriedades de Dependência](dependency-properties-overview.md) e [Propriedades de Dependência Personalizada](custom-dependency-properties.md). Também é necessário ter lido [Visão Geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) e [Sintaxe XAML em Detalhes](xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>A implementação do Carregador XAML do WPF e o desempenho  
 Por motivos de implementação, é computacionalmente menos dispendioso identificar uma propriedade como uma propriedade de dependência e acessar o sistema de propriedades <xref:System.Windows.DependencyObject.SetValue%2A> método para defini-lo, em vez de usar o wrapper de propriedade e seu Setter. Isso ocorre porque um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve inferir todo o modelo de objeto do código de suporte baseado apenas no conhecimento das relações entre tipo e membro indicadas pela estrutura da marcação e várias cadeias de caracteres.  
  
 O tipo é pesquisado por meio de uma combinação de atributos xmlns e assembly, mas identificando os membros, determinando quais poderiam dar suporte a ser definido como um atributo e resolvendo a quais tipos os valores de propriedade dão suporte, caso contrário, exigiria reflexão extensiva usando <xref:System.Reflection.PropertyInfo>. Como as propriedades de dependência em um determinado tipo são acessíveis como uma tabela de armazenamento por meio do sistema de propriedades, a implementação de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de seu processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usa essa tabela e infere que qualquer determinada propriedade *ABC* pode ser definida com mais eficiência por chamando <xref:System.Windows.DependencyObject.SetValue%2A> no tipo derivado de <xref:System.Windows.DependencyObject> que a contém, usando o identificador de propriedade de dependência *ABCProperty*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Implicações para Propriedades de Dependência Personalizadas  
 Como a implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] atual do comportamento do processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para a configuração de propriedade desvia os wrappers como um todo, não é necessário colocar nenhuma lógica adicional nas definições estabelecidas do wrapper para a propriedade de dependência personalizada. Se tal lógica for colocada na definição estabelecida, então, a lógica não será executada quando a propriedade estiver definida como [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em vez de no código.  
  
 Da mesma forma, outros aspectos do processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que obtêm valores de Propriedade do processamento de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] também usam <xref:System.Windows.DependencyObject.GetValue%2A> em vez de usar o wrapper. Portanto, você também deve evitar qualquer implementação adicional na definição de `get` além da chamada <xref:System.Windows.DependencyObject.GetValue%2A>.  
  
 O exemplo a seguir é uma definição de propriedade de dependência recomendada com wrappers, em que o identificador de propriedade é armazenado como um campo `public` `static` `readonly` e as definições `get` e `set` não contêm nenhum código além dos métodos de sistema de propriedade necessários que definem o suporte à propriedade de dependência.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Metadados de propriedade da dependência](dependency-property-metadata.md)
- [Propriedades de dependência do tipo de coleção](collection-type-dependency-properties.md)
- [Segurança de propriedade da dependência](dependency-property-security.md)
- [Padrões de construtor seguro para DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)

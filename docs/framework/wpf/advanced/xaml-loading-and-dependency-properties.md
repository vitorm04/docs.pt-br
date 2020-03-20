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
ms.openlocfilehash: de8050e582f5b1a5a288c350c179cfa24fb5471c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186249"
---
# <a name="xaml-loading-and-dependency-properties"></a>Carregamento de XAML e propriedades da dependência
A implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] atual de seu processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é inerentemente com reconhecimento de propriedade de dependência. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador usa métodos de sistema de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] propriedade para propriedades de dependência ao carregar atributos binários e de processamento que são propriedades de dependência. Isso desvia os wrappers de propriedade de forma efetiva. Ao implementar propriedades de dependência personalizadas, você deve prestar contas desse comportamento e deve evitar colocar <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>qualquer outro código em seu invólucro de propriedade que não seja os métodos do sistema de propriedade e .  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você entende as propriedades de dependência das perspectivas de um consumidor e criador e que leu os tópicos [Visão Geral das Propriedades de Dependência](dependency-properties-overview.md) e [Propriedades de Dependência Personalizada](custom-dependency-properties.md). Também é necessário ter lido [Visão Geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) e [Sintaxe XAML em Detalhes](xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>A implementação do Carregador XAML do WPF e o desempenho  
 Por razões de implementação, é computacionalmente menos caro identificar um <xref:System.Windows.DependencyObject.SetValue%2A> imóvel como um imóvel de dependência e acessar o método do sistema de propriedade para defini-lo, em vez de usar o invólucro de propriedade e seu setter. Isso ocorre porque um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve inferir todo o modelo de objeto do código de suporte baseado apenas no conhecimento das relações entre tipo e membro indicadas pela estrutura da marcação e várias cadeias de caracteres.  
  
 O tipo é examinado através de uma combinação de xmlns e atributos de montagem, mas identificando os membros, determinando quais poderiam <xref:System.Reflection.PropertyInfo>suportar ser definidocomo um atributo, e resolvendo quais tipos o suporte de valores de propriedade exigiria uma reflexão extensiva usando . Como as propriedades de dependência de um determinado tipo são [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] acessíveis [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] como uma tabela <xref:System.Windows.DependencyObject> de armazenamento através do sistema de propriedade, <xref:System.Windows.DependencyObject.SetValue%2A> a implementação de seu processador usa esta tabela e infere que qualquer determinada propriedade *ABC* pode ser definida de forma mais eficiente, solicitando o tipo derivado que contém, usando o identificador de propriedade de dependência *ABCProperty*.  
  
<a name="implications"></a>
## <a name="implications-for-custom-dependency-properties"></a>Implicações para Propriedades de Dependência Personalizadas  
 Como a implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] atual do comportamento do processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para a configuração de propriedade desvia os wrappers como um todo, não é necessário colocar nenhuma lógica adicional nas definições estabelecidas do wrapper para a propriedade de dependência personalizada. Se tal lógica for colocada na definição estabelecida, então, a lógica não será executada quando a propriedade estiver definida como [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em vez de no código.  
  
 Da mesma forma, outros [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aspectos do processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que obtém valores de propriedade a partir do processamento também usam <xref:System.Windows.DependencyObject.GetValue%2A> em vez de usar o invólucro. Portanto, você também deve evitar qualquer `get` implementação <xref:System.Windows.DependencyObject.GetValue%2A> adicional na definição além da chamada.  
  
 O exemplo a seguir é uma definição recomendada de propriedade de dependência com `public` `static` `readonly` invólucros, onde o identificador de propriedade é armazenado como um campo, e as `get` definições não `set` contêm nenhum código além dos métodos necessários do sistema de propriedade que definem o backup da propriedade de dependência.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Confira também

- [Visão geral das propriedades de dependência](dependency-properties-overview.md)
- [Visão geral xaml (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Metadados de propriedade da dependência](dependency-property-metadata.md)
- [Propriedades de dependência do tipo de coleção](collection-type-dependency-properties.md)
- [Segurança de propriedade da dependência](dependency-property-security.md)
- [Padrões de construtor seguros para DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)

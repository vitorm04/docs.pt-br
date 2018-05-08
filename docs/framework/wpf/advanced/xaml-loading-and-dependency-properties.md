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
ms.openlocfilehash: 28e121e73ad4bd8ab70aed5f651418eb309b0c03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-loading-and-dependency-properties"></a>Carregamento de XAML e propriedades da dependência
A implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] atual de seu processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é inerentemente com reconhecimento de propriedade de dependência. O processador [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usa métodos de sistema de propriedade de propriedades de dependência ao carregar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] binários e processar atributos que são propriedades de dependência. Isso desvia os wrappers de propriedade de forma efetiva. Quando você implementa propriedades de dependência personalizadas, você deve considerar esse comportamento e evitar colocar qualquer outro código no seu wrapper de propriedade diferente dos métodos de sistema de propriedade <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você entende as propriedades de dependência das perspectivas de um consumidor e criador e que leu os tópicos [Visão Geral das Propriedades de Dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) e [Propriedades de Dependência Personalizada](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md). Também é necessário ter lido [Visão Geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) e [Sintaxe XAML em Detalhes](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>A implementação do Carregador XAML do WPF e o desempenho  
 Por motivos de implementação, é menos dispendiosa identificar uma propriedade como uma propriedade de dependência e acessar o sistema de propriedade <xref:System.Windows.DependencyObject.SetValue%2A> método para defini-la em vez de utilizar o wrapper da propriedade e seu setter. Isso ocorre porque um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] deve inferir todo o modelo de objeto do código de suporte baseado apenas no conhecimento das relações entre tipo e membro indicadas pela estrutura da marcação e várias cadeias de caracteres.  
  
 O tipo é buscado através de uma combinação de xmlns e atributos de assembly, mas identificando os membros, determinando quais poderiam suportar serem definidos como um atributo e resolvendo que tipos que oferecem suporte os valores de propriedade caso contrário, seriam exigem reflexão extensiva usando <xref:System.Reflection.PropertyInfo>. Como propriedades de dependência em um determinado tipo são acessíveis como uma tabela de armazenamento através do sistema de propriedade, o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementação do seu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador usa essa tabela e infere que qualquer dado propriedade *ABC* pode ser definido de forma mais eficiente chamando <xref:System.Windows.DependencyObject.SetValue%2A> em que o contém <xref:System.Windows.DependencyObject> tipo derivado, usando o identificador de propriedade de dependência *ABCProperty*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Implicações para Propriedades de Dependência Personalizadas  
 Como a implementação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] atual do comportamento do processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para a configuração de propriedade desvia os wrappers como um todo, não é necessário colocar nenhuma lógica adicional nas definições estabelecidas do wrapper para a propriedade de dependência personalizada. Se tal lógica for colocada na definição estabelecida, então, a lógica não será executada quando a propriedade estiver definida como [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em vez de no código.  
  
 Da mesma forma, outros aspectos do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador que obtêm valores de propriedade de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processamento também use <xref:System.Windows.DependencyObject.GetValue%2A> em vez de usar o wrapper. Portanto, você deve evitar qualquer implementação adicional no `get` definição além de <xref:System.Windows.DependencyObject.GetValue%2A> chamar.  
  
 O exemplo a seguir é uma definição de propriedade de dependência recomendada com wrappers, em que o identificador de propriedade é armazenado como um campo `public` `static` `readonly` e as definições `get` e `set` não contêm nenhum código além dos métodos de sistema de propriedade necessários que definem o suporte à propriedade de dependência.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Metadados de propriedade da dependência](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Propriedades de dependência do tipo de coleção](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [Segurança de propriedade da dependência](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [Padrões de construtor seguro para DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)

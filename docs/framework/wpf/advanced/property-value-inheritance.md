---
title: Herança do valor de propriedade
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: b63f307d9edffd14315d383d8e06419fa141aee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187187"
---
# <a name="property-value-inheritance"></a>Herança do valor de propriedade
A herança do valor da propriedade é um recurso do sistema de propriedade [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. A herança do valor da propriedade permite que elementos filho em uma árvore de elementos obtenham o valor de uma propriedade específica dos elementos pai, herdando esse valor como ele foi definido em qualquer lugar do elemento pai mais próximo. O elemento pai também pode ter obtido seu valor por meio da herança do valor da propriedade, de modo que o sistema potencialmente é recursivo até a raiz da página. A herança do valor da propriedade não é o comportamento padrão do sistema de propriedade; uma propriedade deve ser estabelecida com uma configuração específica de metadados para fazer com que essa propriedade inicie a herança do valor da propriedade nos elementos filho.  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>
## <a name="property-value-inheritance-is-containment-inheritance"></a>A herança do valor da propriedade é uma herança de confinamento  
 O termo "herança" aqui não tem exatamente o mesmo conceito de herança no contexto de tipos e da programação voltada a objetos de modo geral, em que as classes derivadas herdam definições de membro de suas classes base. O significado de herança também é ativo em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: propriedades definidas em várias classes base são expostas como atributos para classes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] derivadas quando usadas como elementos, e são expostas como membros ao código. A herança do valor da propriedade está relacionada, especificamente, a como valores da propriedade podem ser herdados de um elemento para outro com base nas relações pai e filho dentro de uma árvore de elementos. A árvore de elementos fica visível mais diretamente quando aninha elementos dentro de outros elementos conforme você define aplicativos na marcação de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Árvores de objetos também podem ser criadas programaticamente adicionando objetos a coleções designadas de outros objetos, e a herança do valor da propriedade funciona da mesma maneira na árvore terminada em tempo de execução.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>
## <a name="practical-applications-of-property-value-inheritance"></a>Aplicativos práticos de herança do valor da propriedade  
 As [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] APIs incluem várias propriedades que têm a herança de propriedade ativada. Normalmente, o cenário é que eles envolvem uma propriedade em que é adequado que a propriedade seja definida apenas uma vez por página, mas em que essa propriedade também é membro de uma das classes de elementos base e, portanto, também existiria na maioria dos elementos filho. Por exemplo, <xref:System.Windows.FrameworkElement.FlowDirection%2A> os controles de propriedade que direcionam o conteúdo fluido devem ser apresentados e organizados na página. Geralmente, você deseja que o conceito de fluxo de texto seja manipulado consistentemente em todos os elementos filho. Se a direção do fluxo fosse, por algum motivo, redefinida em algum nível da árvore de elementos por uma ação do usuário ou do ambiente, ela normalmente seria redefinida em todos os casos. Quando <xref:System.Windows.FrameworkElement.FlowDirection%2A> a propriedade é feita para herdar, o valor só precisa ser definido ou redefinido uma vez no nível na árvore de elementos que engloba as necessidades de apresentação de cada página no aplicativo. Até mesmo o valor padrão inicial herdará dessa forma. O modelo de herança do valor da propriedade ainda permite que elementos individuais redefinam o valor para os raros casos em que ter uma combinação de direções de fluxo é intencional.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>
## <a name="making-a-custom-property-inheritable"></a>Tornando uma propriedade personalizada herdável  
 Alterando os metadados de uma propriedade personalizada, você também pode tornar suas próprias propriedades personalizadas herdáveis. Observe, entretanto, que designar uma propriedade como herdável leva a algumas considerações de desempenho. Em casos em que a propriedade não tem um valor local estabelecido, ou um valor obtido através de estilos, modelos ou associação de dados, uma propriedade herdável fornece seus valores de propriedade atribuídos a todos os elementos filho na árvore lógica.  
  
 Para fazer uma propriedade participar da herança de valor, crie uma propriedade anexada personalizada, conforme descrito em [Registrar uma propriedade anexada](how-to-register-an-attached-property.md). Registre a propriedade com<xref:System.Windows.FrameworkPropertyMetadata>metadados e especifique a opção "Herda" nas configurações de opções dentro desse metadados. Verifique também se a propriedade tem um valor padrão estabelecido, porque esse valor será herdado. Embora você tenha registrado a propriedade como anexada, também convém criar um "wrapper" da propriedade para o acesso de obter/definir no tipo do proprietário, exatamente como você faria para uma propriedade de dependência "não anexada". Depois disso, a propriedade hereditária pode ser definida usando o invólucro de propriedade direta no tipo proprietário ou tipos derivados, ou pode ser definida usando a sintaxe de propriedade anexada em qualquer <xref:System.Windows.DependencyObject>.  
  
 As propriedades anexadas são conceitualmente semelhantes às propriedades globais; você pode verificar o <xref:System.Windows.DependencyObject> valor em qualquer e obter um resultado válido. O cenário típico para propriedades anexadas é definir valores de propriedade em elementos infantis, e esse cenário é mais eficaz se a<xref:System.Windows.DependencyObject>propriedade em questão for uma propriedade anexada que está sempre implicitamente presente como uma propriedade anexa da árvore .  
  
> [!NOTE]
> Embora a herança do valor da propriedade possa parecer funcionar para propriedades de dependência não anexadas, o comportamento da herança de uma propriedade não anexada em certos limites de elemento na árvore de tempo de execução é indefinido. Use <xref:System.Windows.DependencyProperty.RegisterAttached%2A> sempre para registrar <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> propriedades onde você especifica rissem nos metadados.  
  
<a name="InheritanceContext"></a>
## <a name="inheriting-property-values-across-tree-boundaries"></a>Herdando valores de propriedade entre limites de árvores  
 A herança de propriedade funciona percorrendo uma árvore de elementos. Esta árvore geralmente é paralela à árvore lógica. No entanto, sempre que você inclui um objeto de nível de núcleo <xref:System.Windows.Media.Brush>WPF na marcação que define uma árvore de elementos, como a , você criou uma árvore lógica descontínua. Uma verdadeira árvore lógica não se <xref:System.Windows.Media.Brush>estende conceitualmente através do , porque a árvore lógica é um conceito de nível de estrutura WPF. Você pode ver isso refletido nos resultados <xref:System.Windows.LogicalTreeHelper>ao usar os métodos de . No entanto, a herança de valor de propriedade pode preencher essa lacuna na árvore lógica e ainda pode passar valores herdados através, <xref:System.Windows.Controls.Frame>desde que a propriedade herdada foi registrada como uma propriedade anexa e nenhum limite de bloqueio de herança deliberada (como um ) é encontrado.  
  
## <a name="see-also"></a>Confira também

- [Metadados de propriedade da dependência](dependency-property-metadata.md)
- [Visão geral das propriedades anexadas](attached-properties-overview.md)
- [Precedência do valor de propriedade da dependência](dependency-property-value-precedence.md)

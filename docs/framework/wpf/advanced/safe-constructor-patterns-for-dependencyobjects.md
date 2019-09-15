---
title: Padrões de construtor seguro para DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: fce17979fbd43df0496f972cac525fd79dcbfe32
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991817"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Padrões de construtor seguro para DependencyObjects
De modo geral, os construtores de classe não devem chamar retornos de chamada como métodos virtuais ou representantes, porque construtores podem ser chamados como inicialização de base dos construtores para uma classe derivada. O fornecimento do virtual pode ser feito em um estado de inicialização incompleta de um determinado objeto. No entanto, o sistema de propriedades chama e expõe os retornos de chamada internamente, como parte do sistema de propriedades de dependência. Como uma operação simples, a definição de um valor de <xref:System.Windows.DependencyObject.SetValue%2A> propriedade de dependência com chamada pode incluir um retorno de chamada em algum lugar na determinação. Por esse motivo, você deve ter cuidado ao definir valores de propriedade de dependência dentro do corpo de um construtor, o que poderá se tornar problemático se o tipo for usado como uma classe base. Há um padrão específico para implementar <xref:System.Windows.DependencyObject> construtores que evitam problemas específicos com Estados de propriedade de dependência e os retornos de chamada inerentes, documentados aqui.  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Métodos virtuais do sistema de propriedades  
 Os seguintes métodos virtuais ou retornos de chamada são potencialmente chamados durante os cálculos da <xref:System.Windows.DependencyObject.SetValue%2A> chamada que define um valor de propriedade de <xref:System.Windows.ValidateValueCallback>dependência <xref:System.Windows.PropertyChangedCallback>: <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>,,. Cada um desses métodos virtuais ou retornos de chamada tem uma finalidade específica para expandir a versatilidade do sistema de propriedades [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e das propriedades de dependência. Para obter mais informações sobre como usar esses virtuais para personalizar a determinação do valor da propriedade, consulte [Retornos de chamada da propriedade de dependência e validação](dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>Imposição da regra de FXCop versus virtuais do sistema de propriedades  
 Se você usar a ferramenta FXCop da Microsoft como parte do processo de build e derivar de determinadas classes de estrutura [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que chamam o construtor base ou implementar suas próprias propriedades de dependência em classes derivadas, talvez você encontre uma violação de regra de FXCop específica. A cadeia de caracteres de nome dessa violação é:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Essa é uma regra que faz parte da regra pública padrão definida para o FXCop. O que essa regra pode estar relatando é um rastreamento do sistema de propriedade de dependência que eventualmente chama o método virtual do sistema de propriedade de dependência. Essa violação de regra pode continuar aparecendo mesmo após você seguir os padrões de construtor recomendados documentados neste tópico, portanto, talvez seja necessário desabilitar ou suprimir essa regra em sua configuração de conjunto de regras do FXCop.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>A maioria dos problemas vem das classes derivadas, não do uso de classes existentes  
 Os problemas relatados por essa regra ocorrem quando uma classe que você implementa com métodos virtuais em sua sequência de construção é, então, derivada. Se você lacrar sua classe ou souber ou impor que sua classe não será derivada, as considerações explicadas aqui e os problemas que motivaram a regra do FXCop não se aplicarão a você. No entanto, se estiver criando classes de forma que elas devam ser usadas como classes base, por exemplo, se estiver criando modelos ou um conjunto de bibliotecas de controle expansível, siga os padrões recomendados aqui para construtores.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Construtores padrão devem inicializar todos os valores solicitados pelos retornos de chamada  
 Todos os membros da instância que são usados por suas substituições de classe ou retornos de chamada (os retornos de chamada da lista na seção virtual do sistema de propriedades) devem ser inicializados no construtor sem parâmetros de classe, mesmo que alguns desses valores sejam preenchidos por valores "reais" por meio de parâmetros dos construtores sem parâmetros.  
  
 O seguinte exemplo de código (e os exemplos depois dele) é um exemplo de "pseudo" C# que viola essa regra e explica o problema:  
  
```csharp  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 Quando o código do `new MyClass(objectvalue)`aplicativo chama, isso chama o construtor sem parâmetros e construtores de classe base. Em seguida, `Property1 = object1`ele define, que chama o `OnPropertyChanged` método virtual no `MyClass` proprietário <xref:System.Windows.DependencyObject>.  A substituição se refere a `_myList`, que ainda não foi inicializado.  
  
 Uma maneira de evitar esses problemas é garantir que os retornos de chamada usem apenas outras propriedades de dependência e que cada propriedade de dependência tenha um valor padrão estabelecido como parte de seus metadados registrados.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Padrões de construtor seguros  
 Para evitar os riscos da inicialização incompleta se sua classe for usada como uma classe base, siga estes padrões:  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a>Construtores sem parâmetros chamando inicialização básica  
 Implemente esses construtores chamando o padrão de base:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Construtores não padrão (de conveniência) que não correspondem a nenhuma assinatura de base  
 Se esses construtores usarem os parâmetros para definir propriedades de dependência na inicialização, primeiro chame seu próprio construtor sem parâmetros de classe para inicialização e, em seguida, use os parâmetros para definir propriedades de dependência. Esses poderiam ser propriedades de dependência definidas por sua classe ou propriedades de dependência herdadas das classes base, mas em ambos os casos, use o seguinte padrão:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Construtores não padrão (de conveniência) que correspondem a assinaturas de base  
 Em vez de chamar o construtor base com a mesma parametrização, chame novamente seu próprio construtor sem parâmetros de classe. Não chame o inicializador de base; em vez disso, você deve chamar `this()`. Em seguida, reproduza o comportamento do construtor original usando os parâmetros passados como valores para definir as propriedades relevantes. Use a documentação do construtor de base original para ver diretrizes para determinar as propriedades que os parâmetros específicos devem definir:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Deve corresponder a todas as assinaturas  
 Para casos em que o tipo base tem várias assinaturas, você deve corresponder deliberadamente a todas as assinaturas possíveis com uma implementação de Construtor própria que usa o padrão recomendado para chamar o construtor sem parâmetros de classe antes de definir mais Properties.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Definindo propriedades de dependência com SetValue  
 Esses mesmos padrões se aplicam se você estiver definindo uma propriedade que não tem um wrapper para conveniência de configuração de propriedade e definir <xref:System.Windows.DependencyObject.SetValue%2A>valores com. Suas chamadas para <xref:System.Windows.DependencyObject.SetValue%2A> esses parâmetros de construtor de passagem também devem chamar o construtor sem parâmetros de classe para inicialização.  
  
## <a name="see-also"></a>Consulte também

- [Propriedades de dependência personalizada](custom-dependency-properties.md)
- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Segurança de propriedade da dependência](dependency-property-security.md)

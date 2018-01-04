---
title: "Padrões de construtor seguro para DependencyObjects"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db1b7f47ef135b1a174eecef7e53b41e6996256d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="9d679-102">Padrões de construtor seguro para DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="9d679-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="9d679-103">De modo geral, os construtores de classe não devem chamar retornos de chamada como métodos virtuais ou representantes, porque construtores podem ser chamados como inicialização de base dos construtores para uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="9d679-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="9d679-104">O fornecimento do virtual pode ser feito em um estado de inicialização incompleta de um determinado objeto.</span><span class="sxs-lookup"><span data-stu-id="9d679-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="9d679-105">No entanto, o sistema de propriedades chama e expõe os retornos de chamada internamente, como parte do sistema de propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="9d679-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="9d679-106">Uma operação como simples de definir um valor de propriedade de dependência com <xref:System.Windows.DependencyObject.SetValue%2A> chamada potencialmente inclui um retorno de chamada em algum lugar na determinação.</span><span class="sxs-lookup"><span data-stu-id="9d679-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="9d679-107">Por esse motivo, você deve ter cuidado ao definir valores de propriedade de dependência dentro do corpo de um construtor, o que poderá se tornar problemático se o tipo for usado como uma classe base.</span><span class="sxs-lookup"><span data-stu-id="9d679-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="9d679-108">Há um padrão específico para implementar <xref:System.Windows.DependencyObject> construtores que evita problemas específicos com estados de propriedade de dependência e os retornos de chamada inerentes, que é documentado aqui.</span><span class="sxs-lookup"><span data-stu-id="9d679-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="9d679-109">Métodos virtuais do sistema de propriedades</span><span class="sxs-lookup"><span data-stu-id="9d679-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="9d679-110">Os seguintes métodos virtuais ou retornos de chamada potencialmente são chamados durante os cálculos do <xref:System.Windows.DependencyObject.SetValue%2A> chamada que define um valor de propriedade de dependência: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d679-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="9d679-111">Cada um desses métodos virtuais ou retornos de chamada tem uma finalidade específica para expandir a versatilidade do sistema de propriedades [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] e das propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="9d679-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="9d679-112">Para obter mais informações sobre como usar esses virtuais para personalizar a determinação do valor da propriedade, consulte [Retornos de chamada da propriedade de dependência e validação](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="9d679-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="9d679-113">Imposição da regra de FXCop versus virtuais do sistema de propriedades</span><span class="sxs-lookup"><span data-stu-id="9d679-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="9d679-114">Se você usar a ferramenta FXCop da Microsoft como parte do processo de build e derivar de determinadas classes de estrutura [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que chamam o construtor base ou implementar suas próprias propriedades de dependência em classes derivadas, talvez você encontre uma violação de regra de FXCop específica.</span><span class="sxs-lookup"><span data-stu-id="9d679-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="9d679-115">A cadeia de caracteres de nome dessa violação é:</span><span class="sxs-lookup"><span data-stu-id="9d679-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="9d679-116">Essa é uma regra que faz parte da regra pública padrão definida para o FXCop.</span><span class="sxs-lookup"><span data-stu-id="9d679-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="9d679-117">O que essa regra pode estar relatando é um rastreamento do sistema de propriedade de dependência que eventualmente chama o método virtual do sistema de propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="9d679-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="9d679-118">Essa violação de regra pode continuar aparecendo mesmo após você seguir os padrões de construtor recomendados documentados neste tópico, portanto, talvez seja necessário desabilitar ou suprimir essa regra em sua configuração de conjunto de regras do FXCop.</span><span class="sxs-lookup"><span data-stu-id="9d679-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="9d679-119">A maioria dos problemas vem das classes derivadas, não do uso de classes existentes</span><span class="sxs-lookup"><span data-stu-id="9d679-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="9d679-120">Os problemas relatados por essa regra ocorrem quando uma classe que você implementa com métodos virtuais em sua sequência de construção é, então, derivada.</span><span class="sxs-lookup"><span data-stu-id="9d679-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="9d679-121">Se você lacrar sua classe ou souber ou impor que sua classe não será derivada, as considerações explicadas aqui e os problemas que motivaram a regra do FXCop não se aplicarão a você.</span><span class="sxs-lookup"><span data-stu-id="9d679-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="9d679-122">No entanto, se estiver criando classes de forma que elas devam ser usadas como classes base, por exemplo, se estiver criando modelos ou um conjunto de bibliotecas de controle expansível, siga os padrões recomendados aqui para construtores.</span><span class="sxs-lookup"><span data-stu-id="9d679-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="9d679-123">Construtores padrão devem inicializar todos os valores solicitados pelos retornos de chamada</span><span class="sxs-lookup"><span data-stu-id="9d679-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="9d679-124">Qualquer membro de instância usado pelas substituições ou retornos de chamada de sua classe (os retornos de chamada da lista na seção Virtuais do sistema de propriedades) deve ser inicializado no construtor padrão de sua classe, mesmo que alguns desses valores sejam preenchidos por valores "reais" por meio de parâmetros dos construtores não padrão.</span><span class="sxs-lookup"><span data-stu-id="9d679-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class default constructor, even if some of those values are filled by "real" values through parameters of the nondefault constructors.</span></span>  
  
 <span data-ttu-id="9d679-125">O seguinte exemplo de código (e os exemplos depois dele) é um exemplo de "pseudo" C# que viola essa regra e explica o problema:</span><span class="sxs-lookup"><span data-stu-id="9d679-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
```  
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
  
 <span data-ttu-id="9d679-126">Quando o código do aplicativo chama `new MyClass(objectvalue)`, isso chama o construtor padrão e os construtores da classe base.</span><span class="sxs-lookup"><span data-stu-id="9d679-126">When application code calls `new MyClass(objectvalue)`, this calls the default constructor and base class constructors.</span></span> <span data-ttu-id="9d679-127">Em seguida, ele define `Property1 = object1`, que chama o método virtual `OnPropertyChanged` na posse `MyClass` <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="9d679-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="9d679-128">A substituição se refere a `_myList`, que ainda não foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="9d679-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="9d679-129">Uma maneira de evitar esses problemas é garantir que os retornos de chamada usem apenas outras propriedades de dependência e que cada propriedade de dependência tenha um valor padrão estabelecido como parte de seus metadados registrados.</span><span class="sxs-lookup"><span data-stu-id="9d679-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="9d679-130">Padrões de construtor seguros</span><span class="sxs-lookup"><span data-stu-id="9d679-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="9d679-131">Para evitar os riscos da inicialização incompleta se sua classe for usada como uma classe base, siga estes padrões:</span><span class="sxs-lookup"><span data-stu-id="9d679-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="default-constructors-calling-base-initialization"></a><span data-ttu-id="9d679-132">Construtores padrão que chamam a inicialização de base</span><span class="sxs-lookup"><span data-stu-id="9d679-132">Default constructors calling base initialization</span></span>  
 <span data-ttu-id="9d679-133">Implemente esses construtores chamando o padrão de base:</span><span class="sxs-lookup"><span data-stu-id="9d679-133">Implement these constructors calling the base default:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="9d679-134">Construtores não padrão (de conveniência) que não correspondem a nenhuma assinatura de base</span><span class="sxs-lookup"><span data-stu-id="9d679-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="9d679-135">Se esses construtores usarem os parâmetros para definir propriedades de dependência na inicialização, primeiro chame seu próprio construtor padrão da classe para inicialização e, em seguida, use os parâmetros para definir propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="9d679-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class default constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="9d679-136">Esses poderiam ser propriedades de dependência definidas por sua classe ou propriedades de dependência herdadas das classes base, mas em ambos os casos, use o seguinte padrão:</span><span class="sxs-lookup"><span data-stu-id="9d679-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="9d679-137">Construtores não padrão (de conveniência) que correspondem a assinaturas de base</span><span class="sxs-lookup"><span data-stu-id="9d679-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="9d679-138">Em vez de chamar o construtor de base com a mesma parametrização, chame novamente o construtor padrão da sua própria classe.</span><span class="sxs-lookup"><span data-stu-id="9d679-138">Instead of calling the base constructor with the same parameterization, again call your own class' default constructor.</span></span> <span data-ttu-id="9d679-139">Não chame o inicializador de base; em vez disso, você deve chamar `this()`.</span><span class="sxs-lookup"><span data-stu-id="9d679-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="9d679-140">Em seguida, reproduza o comportamento do construtor original usando os parâmetros passados como valores para definir as propriedades relevantes.</span><span class="sxs-lookup"><span data-stu-id="9d679-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="9d679-141">Use a documentação do construtor de base original para ver diretrizes para determinar as propriedades que os parâmetros específicos devem definir:</span><span class="sxs-lookup"><span data-stu-id="9d679-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="9d679-142">Deve corresponder a todas as assinaturas</span><span class="sxs-lookup"><span data-stu-id="9d679-142">Must match all signatures</span></span>  
 <span data-ttu-id="9d679-143">Para casos em que o tipo base tem várias assinaturas, você deve corresponder deliberadamente todas as assinaturas possíveis com uma implementação do construtor que seja sua e que use o padrão recomendado de chamar o construtor padrão da classe antes de configurar mais propriedades.</span><span class="sxs-lookup"><span data-stu-id="9d679-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class default constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="9d679-144">Definindo propriedades de dependência com SetValue</span><span class="sxs-lookup"><span data-stu-id="9d679-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="9d679-145">Esses mesmos padrões se aplicam se você estiver definindo uma propriedade que não tenha um wrapper para a conveniência de configuração de propriedade e definir valores com <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="9d679-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="9d679-146">As chamadas para <xref:System.Windows.DependencyObject.SetValue%2A> que passar parâmetros do construtor também deve chamar o construtor padrão da classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="9d679-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' default constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d679-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d679-147">See Also</span></span>  
 [<span data-ttu-id="9d679-148">Propriedades de dependência personalizada</span><span class="sxs-lookup"><span data-stu-id="9d679-148">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="9d679-149">Visão geral das propriedades da dependência</span><span class="sxs-lookup"><span data-stu-id="9d679-149">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="9d679-150">Segurança de propriedade da dependência</span><span class="sxs-lookup"><span data-stu-id="9d679-150">Dependency Property Security</span></span>](../../../../docs/framework/wpf/advanced/dependency-property-security.md)

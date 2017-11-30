---
title: Escrevendo atributos personalizados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0205edba221b833625becbe6a1f2fdda2f9409a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="8f109-102">Escrevendo atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="8f109-102">Writing Custom Attributes</span></span>
<span data-ttu-id="8f109-103">Para criar seus próprios atributos personalizados, você não precisa dominar muitos novos conceitos.</span><span class="sxs-lookup"><span data-stu-id="8f109-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="8f109-104">Se você estiver familiarizado com programação orientada a objeto e sabe como criar classes, você já tem a maioria do conhecimento necessário.</span><span class="sxs-lookup"><span data-stu-id="8f109-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="8f109-105">Atributos personalizados são classes essencialmente tradicionais que derivam direta ou indiretamente <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f109-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8f109-106">Exatamente como classes tradicionais, os atributos personalizados contêm métodos que armazenam e recuperam dados.</span><span class="sxs-lookup"><span data-stu-id="8f109-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="8f109-107">As etapas principais para criar corretamente classes de atributos personalizados são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="8f109-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
-   [<span data-ttu-id="8f109-108">Aplicando o AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="8f109-108">Applying the AttributeUsageAttribute</span></span>](#cpconapplyingattributeusageattribute)  
  
-   [<span data-ttu-id="8f109-109">Declarando a classe de atributo</span><span class="sxs-lookup"><span data-stu-id="8f109-109">Declaring the attribute class</span></span>](#cpcondeclaringattributeclass)  
  
-   [<span data-ttu-id="8f109-110">Declarando construtores</span><span class="sxs-lookup"><span data-stu-id="8f109-110">Declaring constructors</span></span>](#cpcondeclaringconstructors)  
  
-   [<span data-ttu-id="8f109-111">Declarando propriedades</span><span class="sxs-lookup"><span data-stu-id="8f109-111">Declaring properties</span></span>](#cpcondeclaringproperties)  
  
 <span data-ttu-id="8f109-112">Esta seção descreve cada uma dessas etapas e termina com um [exemplo de atributo personalizado](#cpconcustomattributeexample).</span><span class="sxs-lookup"><span data-stu-id="8f109-112">This section describes each of these steps and concludes with a [custom attribute example](#cpconcustomattributeexample).</span></span>  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="8f109-113">Aplicando o AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="8f109-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="8f109-114">Uma declaração de atributo personalizado começa com o **AttributeUsageAttribute**, que define algumas das principais características da sua classe de atributo.</span><span class="sxs-lookup"><span data-stu-id="8f109-114">A custom attribute declaration begins with the **AttributeUsageAttribute**, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="8f109-115">Por exemplo, você pode especificar se o atributo pode ser herdada por outras classes ou especificar a quais elementos o atributo pode ser aplicado a.</span><span class="sxs-lookup"><span data-stu-id="8f109-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="8f109-116">O fragmento de código a seguir demonstra como usar o **AttributeUsageAttribute**.</span><span class="sxs-lookup"><span data-stu-id="8f109-116">The following code fragment demonstrates how to use the **AttributeUsageAttribute**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="8f109-117">O <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> tem três membros que são importantes para a criação de atributos personalizados: [AttributeTargets](#cpconwritingcustomattributesanchor1), [herdadas](#cpconwritingcustomattributesanchor2), e [AllowMultiple](#cpconwritingcustomattributesanchor3).</span><span class="sxs-lookup"><span data-stu-id="8f109-117">The <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> has three members that are important for the creation of custom attributes: [AttributeTargets](#cpconwritingcustomattributesanchor1), [Inherited](#cpconwritingcustomattributesanchor2), and [AllowMultiple](#cpconwritingcustomattributesanchor3).</span></span>  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a><span data-ttu-id="8f109-118">Membro da AttributeTargets</span><span class="sxs-lookup"><span data-stu-id="8f109-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="8f109-119">No exemplo anterior, **AttributeTargets. All** é especificada, indicando que esse atributo pode ser aplicado a todos os elementos do programa.</span><span class="sxs-lookup"><span data-stu-id="8f109-119">In the previous example, **AttributeTargets.All** is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="8f109-120">Como alternativa, você pode especificar **AttributeTargets**, indicando que o atributo pode ser aplicado somente a uma classe, ou **AttributeTargets**, indicando que o atributo pode ser aplicado somente a um método.</span><span class="sxs-lookup"><span data-stu-id="8f109-120">Alternatively, you can specify **AttributeTargets.Class**, indicating that your attribute can be applied only to a class, or **AttributeTargets.Method**, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="8f109-121">Todos os elementos do programa podem ser marcados para descrição por um atributo personalizado dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="8f109-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="8f109-122">Você também pode passar várias instâncias do <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="8f109-122">You can also pass multiple instances of <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="8f109-123">O fragmento de código a seguir especifica que um atributo personalizado pode ser aplicado a qualquer classe ou método.</span><span class="sxs-lookup"><span data-stu-id="8f109-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a><span data-ttu-id="8f109-124">Propriedade herdada</span><span class="sxs-lookup"><span data-stu-id="8f109-124">Inherited Property</span></span>  
 <span data-ttu-id="8f109-125">O <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> propriedade indica se o atributo pode ser herdado por classes derivadas de classes para o qual o atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="8f109-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="8f109-126">Essa propriedade aceita um **true** (o padrão) ou **false** sinalizador.</span><span class="sxs-lookup"><span data-stu-id="8f109-126">This property takes either a **true** (the default) or **false** flag.</span></span> <span data-ttu-id="8f109-127">Por exemplo, no exemplo a seguir, `MyAttribute` tem um padrão <xref:System.AttributeUsageAttribute.Inherited%2A> valor **true**, enquanto `YourAttribute` tem um <xref:System.AttributeUsageAttribute.Inherited%2A> valor **false**.</span><span class="sxs-lookup"><span data-stu-id="8f109-127">For example, in the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of **true**, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of **false**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="8f109-128">Os dois atributos são aplicados a um método na classe base `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="8f109-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="8f109-129">Por fim, a classe `YourClass` é herdada da classe base `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="8f109-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="8f109-130">O método `MyMethod` mostra `MyAttribute`, mas não `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8f109-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a><span data-ttu-id="8f109-131">Propriedade AllowMultiple</span><span class="sxs-lookup"><span data-stu-id="8f109-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="8f109-132">O <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> propriedade indica se várias instâncias do seu atributo podem existir em um elemento.</span><span class="sxs-lookup"><span data-stu-id="8f109-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="8f109-133">Se definido como **true**, são permitidas várias instâncias; se definido como **false** (o padrão), somente uma instância é permitida.</span><span class="sxs-lookup"><span data-stu-id="8f109-133">If set to **true**, multiple instances are allowed; if set to **false** (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="8f109-134">No exemplo a seguir, `MyAttribute` tem um padrão <xref:System.AttributeUsageAttribute.AllowMultiple%2A> valor **false**, enquanto `YourAttribute` tem um valor de **true**.</span><span class="sxs-lookup"><span data-stu-id="8f109-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of **false**, while `YourAttribute` has a value of **true**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="8f109-135">Quando várias instâncias desses atributos são aplicadas, `MyAttribute` produz um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="8f109-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="8f109-136">O exemplo de código a seguir mostra o uso válido de `YourAttribute` e o uso inválido de `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8f109-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="8f109-137">Se o <xref:System.AttributeUsageAttribute.AllowMultiple%2A> propriedade e o <xref:System.AttributeUsageAttribute.Inherited%2A> propriedade são definidos como **true**, uma classe herdada de outra classe pode herdar de um atributo e ter outra instância do mesmo atributo aplicado na mesma classe filho.</span><span class="sxs-lookup"><span data-stu-id="8f109-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to **true**, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="8f109-138">Se <xref:System.AttributeUsageAttribute.AllowMultiple%2A> é definido como **false**, os valores de quaisquer atributos na classe pai serão substituídos pelas novas instâncias do mesmo atributo na classe filha.</span><span class="sxs-lookup"><span data-stu-id="8f109-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to **false**, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="8f109-139">Declarando a classe de atributo</span><span class="sxs-lookup"><span data-stu-id="8f109-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="8f109-140">Depois de aplicar o <xref:System.AttributeUsageAttribute>, você pode começar a definir as especificidades do seu atributo.</span><span class="sxs-lookup"><span data-stu-id="8f109-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="8f109-141">A declaração de uma classe de atributo é semelhante à declaração de uma classe tradicional, como demonstrado pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8f109-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="8f109-142">Esta definição de atributo demonstra os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="8f109-142">This attribute definition demonstrates the following points:</span></span>  
  
-   <span data-ttu-id="8f109-143">Classes de atributo devem ser declarados como classes públicas.</span><span class="sxs-lookup"><span data-stu-id="8f109-143">Attribute classes must be declared as public classes.</span></span>  
  
-   <span data-ttu-id="8f109-144">Por convenção, o nome da classe de atributo termina com a palavra **atributo**.</span><span class="sxs-lookup"><span data-stu-id="8f109-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="8f109-145">Embora não seja necessário, esta convenção é recomendada para facilitar a leitura.</span><span class="sxs-lookup"><span data-stu-id="8f109-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="8f109-146">Quando o atributo é aplicado, a inclusão da palavra atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="8f109-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
-   <span data-ttu-id="8f109-147">Todas as classes de atributo devem herdar direta ou indiretamente de **Attribute**.</span><span class="sxs-lookup"><span data-stu-id="8f109-147">All attribute classes must inherit directly or indirectly from **System.Attribute**.</span></span>  
  
-   <span data-ttu-id="8f109-148">No Microsoft Visual Basic, todas as classes de atributo personalizado devem ter o **AttributeUsageAttribute** atributo.</span><span class="sxs-lookup"><span data-stu-id="8f109-148">In Microsoft Visual Basic, all custom attribute classes must have the **AttributeUsageAttribute** attribute.</span></span>  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a><span data-ttu-id="8f109-149">Declarando construtores</span><span class="sxs-lookup"><span data-stu-id="8f109-149">Declaring Constructors</span></span>  
 <span data-ttu-id="8f109-150">Atributos são inicializados com construtores da mesma forma como as classes tradicionais.</span><span class="sxs-lookup"><span data-stu-id="8f109-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="8f109-151">O fragmento de código a seguir ilustra um típico construtor de atributos.</span><span class="sxs-lookup"><span data-stu-id="8f109-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="8f109-152">Esse construtor público aceita um parâmetro e define seu valor igual a uma variável de membro.</span><span class="sxs-lookup"><span data-stu-id="8f109-152">This public constructor takes a parameter and sets its value equal to a member variable.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="8f109-153">Você pode sobrecarregar o construtor para acomodar diferentes combinações de valores.</span><span class="sxs-lookup"><span data-stu-id="8f109-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="8f109-154">Se você também definir um [propriedade](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) para sua classe de atributo personalizado, você pode usar uma combinação de parâmetros nomeados e posicionais ao inicializar o atributo.</span><span class="sxs-lookup"><span data-stu-id="8f109-154">If you also define a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="8f109-155">Normalmente, você define todos os parâmetros necessários como parâmetros posicionais e todos opcionais, como chamado.</span><span class="sxs-lookup"><span data-stu-id="8f109-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="8f109-156">Nesse caso, o atributo não pode ser inicializado sem o parâmetro necessário.</span><span class="sxs-lookup"><span data-stu-id="8f109-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="8f109-157">Todos os outros parâmetros são opcionais.</span><span class="sxs-lookup"><span data-stu-id="8f109-157">All other parameters are optional.</span></span> <span data-ttu-id="8f109-158">Observe que no Visual Basic, construtores para uma classe de atributo não devem usar um argumento ParamArray.</span><span class="sxs-lookup"><span data-stu-id="8f109-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="8f109-159">O exemplo de código a seguir mostra como um atributo que usa o construtor anterior pode ser aplicado usando parâmetros necessários e opcionais.</span><span class="sxs-lookup"><span data-stu-id="8f109-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="8f109-160">Ele pressupõe que o atributo tem um valor booleano necessário e uma cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="8f109-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a><span data-ttu-id="8f109-161">Declarando propriedades</span><span class="sxs-lookup"><span data-stu-id="8f109-161">Declaring Properties</span></span>  
 <span data-ttu-id="8f109-162">Se você quiser definir um parâmetro nomeado ou fornecer uma maneira fácil para retornar os valores armazenados pelo seu atributo, declare um [propriedade](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="8f109-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="8f109-163">Propriedades de atributo devem ser declaradas como entidades públicas com uma descrição do tipo de dados que será retornado.</span><span class="sxs-lookup"><span data-stu-id="8f109-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="8f109-164">Definir a variável que irá conter o valor de sua propriedade e associá-lo com o **obter** e **definir** métodos.</span><span class="sxs-lookup"><span data-stu-id="8f109-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="8f109-165">O exemplo de código a seguir demonstra como implementar uma propriedade simples em seu atributo.</span><span class="sxs-lookup"><span data-stu-id="8f109-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a><span data-ttu-id="8f109-166">Exemplo de atributo personalizado</span><span class="sxs-lookup"><span data-stu-id="8f109-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="8f109-167">Esta seção incorpora as informações anteriores e mostra como criar um atributo simples que documenta informações sobre o autor de uma seção de código.</span><span class="sxs-lookup"><span data-stu-id="8f109-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="8f109-168">O atributo neste exemplo armazena o nome e o nível do programador, e se o código foi revisado.</span><span class="sxs-lookup"><span data-stu-id="8f109-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="8f109-169">Ele usa três variáveis privadas para armazenar os valores reais para salvar.</span><span class="sxs-lookup"><span data-stu-id="8f109-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="8f109-170">Cada variável é representado por uma propriedade pública que obtém e define os valores.</span><span class="sxs-lookup"><span data-stu-id="8f109-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="8f109-171">Finalmente, o construtor é definido com dois parâmetros necessários.</span><span class="sxs-lookup"><span data-stu-id="8f109-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="8f109-172">Você pode aplicar esse atributo usando o nome completo, `DeveloperAttribute`, ou usando o nome abreviado, `Developer`, em uma das seguintes maneiras.</span><span class="sxs-lookup"><span data-stu-id="8f109-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="8f109-173">O primeiro exemplo mostra o atributo aplicado com apenas o necessário a parâmetros nomeados, enquanto o segundo exemplo mostra o atributo aplicado com os parâmetros necessários e opcionais.</span><span class="sxs-lookup"><span data-stu-id="8f109-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f109-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f109-174">See Also</span></span>  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="8f109-175">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f109-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)

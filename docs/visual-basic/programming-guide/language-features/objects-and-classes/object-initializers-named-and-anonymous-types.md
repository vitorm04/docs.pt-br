---
title: 'Inicializadores de objeto: tipos nomeados e anônimos'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 724407fed5bf90ed6e3e470cbabc9e42856cb99a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087473"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a><span data-ttu-id="78e40-102">Inicializadores de objeto: tipos nomeados e anônimos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78e40-102">Object Initializers: Named and Anonymous Types (Visual Basic)</span></span>

<span data-ttu-id="78e40-103">Os inicializadores de objeto permitem especificar propriedades para um objeto complexo usando uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="78e40-103">Object initializers enable you to specify properties for a complex object by using a single expression.</span></span> <span data-ttu-id="78e40-104">Eles podem ser usados para criar instâncias de tipos nomeados e de tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="78e40-104">They can be used to create instances of named types and of anonymous types.</span></span>  
  
## <a name="declarations"></a><span data-ttu-id="78e40-105">Declarações</span><span class="sxs-lookup"><span data-stu-id="78e40-105">Declarations</span></span>  

 <span data-ttu-id="78e40-106">Declarações de instâncias de tipos nomeados e anônimos podem parecer quase idênticas, mas seus efeitos não são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="78e40-106">Declarations of instances of named and anonymous types can look almost identical, but their effects are not the same.</span></span> <span data-ttu-id="78e40-107">Cada categoria tem habilidades e restrições próprias.</span><span class="sxs-lookup"><span data-stu-id="78e40-107">Each category has abilities and restrictions of its own.</span></span> <span data-ttu-id="78e40-108">O exemplo a seguir mostra uma maneira conveniente de declarar e inicializar uma instância de uma classe nomeada, `Customer` , usando uma lista de inicializadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="78e40-108">The following example shows a convenient way to declare and initialize an instance of a named class, `Customer`, by using an object initializer list.</span></span> <span data-ttu-id="78e40-109">Observe que o nome da classe é especificado após a palavra-chave `New` .</span><span class="sxs-lookup"><span data-stu-id="78e40-109">Notice that the name of the class is specified after the keyword `New`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 <span data-ttu-id="78e40-110">Um tipo anônimo não tem nome utilizável.</span><span class="sxs-lookup"><span data-stu-id="78e40-110">An anonymous type has no usable name.</span></span> <span data-ttu-id="78e40-111">Portanto, uma instanciação de um tipo anônimo não pode incluir um nome de classe.</span><span class="sxs-lookup"><span data-stu-id="78e40-111">Therefore an instantiation of an anonymous type cannot include a class name.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 <span data-ttu-id="78e40-112">Os requisitos e os resultados das duas declarações não são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="78e40-112">The requirements and results of the two declarations are not the same.</span></span> <span data-ttu-id="78e40-113">Para `namedCust` , uma `Customer` classe que tem uma `Name` Propriedade já deve existir e a declaração cria uma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="78e40-113">For `namedCust`, a `Customer` class that has a `Name` property must already exist, and the declaration creates an instance of that class.</span></span> <span data-ttu-id="78e40-114">Para `anonymousCust` o, o compilador define uma nova classe que tem uma propriedade, uma cadeia `Name` de caracteres chamada e cria uma nova instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="78e40-114">For `anonymousCust`, the compiler defines a new class that has one property, a string called `Name`, and creates a new instance of that class.</span></span>  
  
## <a name="named-types"></a><span data-ttu-id="78e40-115">Tipos nomeados</span><span class="sxs-lookup"><span data-stu-id="78e40-115">Named Types</span></span>  

 <span data-ttu-id="78e40-116">Os inicializadores de objeto fornecem uma maneira simples de chamar o construtor de um tipo e, em seguida, definir os valores de algumas ou todas as propriedades em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="78e40-116">Object initializers provide a simple way to call the constructor of a type and then set the values of some or all properties in a single statement.</span></span> <span data-ttu-id="78e40-117">O compilador invoca o construtor apropriado para a instrução: o construtor sem parâmetros se nenhum argumento for apresentado ou um construtor com parâmetros se um ou mais argumentos forem enviados.</span><span class="sxs-lookup"><span data-stu-id="78e40-117">The compiler invokes the appropriate constructor for the statement: the parameterless constructor if no arguments are presented, or a parameterized constructor if one or more arguments are sent.</span></span> <span data-ttu-id="78e40-118">Depois disso, as propriedades especificadas são inicializadas na ordem em que são apresentadas na lista de inicializadores.</span><span class="sxs-lookup"><span data-stu-id="78e40-118">After that, the specified properties are initialized in the order in which they are presented in the initializer list.</span></span>  
  
 <span data-ttu-id="78e40-119">Cada inicialização na lista de inicializadores consiste na atribuição de um valor inicial a um membro da classe.</span><span class="sxs-lookup"><span data-stu-id="78e40-119">Each initialization in the initializer list consists of the assignment of an initial value to a member of the class.</span></span> <span data-ttu-id="78e40-120">Os nomes e tipos de dados dos membros são determinados quando a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="78e40-120">The names and data types of the members are determined when the class is defined.</span></span> <span data-ttu-id="78e40-121">Nos exemplos a seguir, a `Customer` classe deve existir e deve ter membros chamados `Name` e `City` que pode aceitar valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="78e40-121">In the following examples, the `Customer` class must exist, and must have members named `Name` and `City` that can accept string values.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 <span data-ttu-id="78e40-122">Como alternativa, você pode obter o mesmo resultado usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="78e40-122">Alternatively, you can obtain the same result by using the following code:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 <span data-ttu-id="78e40-123">Cada uma dessas declarações é equivalente ao exemplo a seguir, que cria um `Customer` objeto usando o construtor sem parâmetros e, em seguida, especifica os valores iniciais para as `Name` `City` Propriedades e usando uma `With` instrução.</span><span class="sxs-lookup"><span data-stu-id="78e40-123">Each of these declarations is equivalent to the following example, which creates a `Customer` object by using the parameterless constructor, and then specifies initial values for the `Name` and `City` properties by using a `With` statement.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 <span data-ttu-id="78e40-124">Se a `Customer` classe contiver um construtor com parâmetros que permita que você envie um valor para `Name` , por exemplo, você também pode declarar e inicializar um `Customer` objeto das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="78e40-124">If the `Customer` class contains a parameterized constructor that enables you to send in a value for `Name`, for example, you can also declare and initialize a `Customer` object in the following ways:</span></span>  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 <span data-ttu-id="78e40-125">Você não precisa inicializar todas as propriedades, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="78e40-125">You do not have to initialize all properties, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 <span data-ttu-id="78e40-126">No entanto, a lista de inicialização não pode ficar vazia.</span><span class="sxs-lookup"><span data-stu-id="78e40-126">However, the initialization list cannot be empty.</span></span> <span data-ttu-id="78e40-127">As propriedades não inicializadas retêm seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="78e40-127">Uninitialized properties retain their default values.</span></span>  
  
### <a name="type-inference-with-named-types"></a><span data-ttu-id="78e40-128">Inferência de tipos com tipos nomeados</span><span class="sxs-lookup"><span data-stu-id="78e40-128">Type Inference with Named Types</span></span>  

 <span data-ttu-id="78e40-129">Você pode encurtar o código para a declaração de `cust1` combinando inicializadores de objeto e inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="78e40-129">You can shorten the code for the declaration of `cust1` by combining object initializers and local type inference.</span></span> <span data-ttu-id="78e40-130">Isso permite omitir a `As` cláusula na declaração da variável.</span><span class="sxs-lookup"><span data-stu-id="78e40-130">This enables you to omit the `As` clause in the variable declaration.</span></span> <span data-ttu-id="78e40-131">O tipo de dados da variável é inferido a partir do tipo do objeto criado pela atribuição.</span><span class="sxs-lookup"><span data-stu-id="78e40-131">The data type of the variable is inferred from the type of the object that is created by the assignment.</span></span> <span data-ttu-id="78e40-132">No exemplo a seguir, o tipo de `cust6` é `Customer` .</span><span class="sxs-lookup"><span data-stu-id="78e40-132">In the following example, the type of `cust6` is `Customer`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a><span data-ttu-id="78e40-133">Comentários sobre tipos nomeados</span><span class="sxs-lookup"><span data-stu-id="78e40-133">Remarks About Named Types</span></span>  
  
- <span data-ttu-id="78e40-134">Um membro de classe não pode ser inicializado mais de uma vez na lista de inicializadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="78e40-134">A class member cannot be initialized more than one time in the object initializer list.</span></span> <span data-ttu-id="78e40-135">A declaração de `cust7` causa um erro.</span><span class="sxs-lookup"><span data-stu-id="78e40-135">The declaration of `cust7` causes an error.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- <span data-ttu-id="78e40-136">Um membro pode ser usado para inicializar a si mesmo ou outro campo.</span><span class="sxs-lookup"><span data-stu-id="78e40-136">A member can be used to initialize itself or another field.</span></span> <span data-ttu-id="78e40-137">Se um membro for acessado antes de ser inicializado, como na declaração a seguir para `cust8` , o valor padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="78e40-137">If a member is accessed before it has been initialized, as in the following declaration for `cust8`, the default value will be used.</span></span> <span data-ttu-id="78e40-138">Lembre-se de que quando uma declaração que usa um inicializador de objeto é processada, a primeira coisa que acontece é que o construtor apropriado é invocado.</span><span class="sxs-lookup"><span data-stu-id="78e40-138">Remember that when a declaration that uses an object initializer is processed, the first thing that happens is that the appropriate constructor is invoked.</span></span> <span data-ttu-id="78e40-139">Depois disso, os campos individuais na lista de inicializadores são inicializados.</span><span class="sxs-lookup"><span data-stu-id="78e40-139">After that, the individual fields in the initializer list are initialized.</span></span> <span data-ttu-id="78e40-140">Nos exemplos a seguir, o valor padrão para `Name` é atribuído para `cust8` e um valor inicializado é atribuído em `cust9` .</span><span class="sxs-lookup"><span data-stu-id="78e40-140">In the following examples, the default value for `Name` is assigned for `cust8`, and an initialized value is assigned in `cust9`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     <span data-ttu-id="78e40-141">O exemplo a seguir usa o construtor com parâmetros de `cust3` e `cust4` para declarar e inicializar `cust10` e `cust11` .</span><span class="sxs-lookup"><span data-stu-id="78e40-141">The following example uses the parameterized constructor from `cust3` and `cust4` to declare and initialize `cust10` and `cust11`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- <span data-ttu-id="78e40-142">Os inicializadores de objeto podem ser aninhados.</span><span class="sxs-lookup"><span data-stu-id="78e40-142">Object initializers can be nested.</span></span> <span data-ttu-id="78e40-143">No exemplo a seguir, `AddressClass` é uma classe que tem duas propriedades `City` e `State` , e a `Customer` classe tem uma `Address` propriedade que é uma instância do `AddressClass` .</span><span class="sxs-lookup"><span data-stu-id="78e40-143">In the following example, `AddressClass` is a class that has two properties, `City` and `State`, and the `Customer` class has an `Address` property that is an instance of `AddressClass`.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- <span data-ttu-id="78e40-144">A lista de inicialização não pode ficar vazia.</span><span class="sxs-lookup"><span data-stu-id="78e40-144">The initialization list cannot be empty.</span></span>  
  
- <span data-ttu-id="78e40-145">A instância que está sendo inicializada não pode ser do tipo Object.</span><span class="sxs-lookup"><span data-stu-id="78e40-145">The instance being initialized cannot be of type Object.</span></span>  
  
- <span data-ttu-id="78e40-146">Membros de classe que estão sendo inicializados não podem ser membros compartilhados, membros somente leitura, constantes ou chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="78e40-146">Class members being initialized cannot be shared members, read-only members, constants, or method calls.</span></span>  
  
- <span data-ttu-id="78e40-147">Membros de classe que estão sendo inicializados não podem ser indexados ou qualificados.</span><span class="sxs-lookup"><span data-stu-id="78e40-147">Class members being initialized cannot be indexed or qualified.</span></span> <span data-ttu-id="78e40-148">Os exemplos a seguir geram erros do compilador:</span><span class="sxs-lookup"><span data-stu-id="78e40-148">The following examples raise compiler errors:</span></span>  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a><span data-ttu-id="78e40-149">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="78e40-149">Anonymous Types</span></span>  

 <span data-ttu-id="78e40-150">Os tipos anônimos usam inicializadores de objeto para criar instâncias de novos tipos que você não define explicitamente e nomear.</span><span class="sxs-lookup"><span data-stu-id="78e40-150">Anonymous types use object initializers to create instances of new types that you do not explicitly define and name.</span></span> <span data-ttu-id="78e40-151">Em vez disso, o compilador gera um tipo de acordo com as propriedades que você designa na lista de inicializadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="78e40-151">Instead, the compiler generates a type according to the properties you designate in the object initializer list.</span></span> <span data-ttu-id="78e40-152">Como o nome do tipo não é especificado, ele é conhecido como um *tipo anônimo*.</span><span class="sxs-lookup"><span data-stu-id="78e40-152">Because the name of the type is not specified, it is referred to as an *anonymous type*.</span></span> <span data-ttu-id="78e40-153">Por exemplo, compare a declaração a seguir para a anterior para `cust6` .</span><span class="sxs-lookup"><span data-stu-id="78e40-153">For example, compare the following declaration to the earlier one for `cust6`.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 <span data-ttu-id="78e40-154">A única diferença sintaticamente é que nenhum nome é especificado depois `New` para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="78e40-154">The only difference syntactically is that no name is specified after `New` for the data type.</span></span> <span data-ttu-id="78e40-155">No entanto, o que acontece é bastante diferente.</span><span class="sxs-lookup"><span data-stu-id="78e40-155">However, what happens is quite different.</span></span> <span data-ttu-id="78e40-156">O compilador define um novo tipo anônimo que tem duas propriedades `Name` e `City` cria uma instância dela com os valores especificados.</span><span class="sxs-lookup"><span data-stu-id="78e40-156">The compiler defines a new anonymous type that has two properties, `Name` and `City`, and creates an instance of it with the specified values.</span></span> <span data-ttu-id="78e40-157">A inferência de tipos determina os tipos de `Name` e, `City` no exemplo, para serem cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="78e40-157">Type inference determines the types of `Name` and `City` in the example to be strings.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="78e40-158">O nome do tipo anônimo é gerado pelo compilador e pode variar de compilação para compilação.</span><span class="sxs-lookup"><span data-stu-id="78e40-158">The name of the anonymous type is generated by the compiler, and may vary from compilation to compilation.</span></span> <span data-ttu-id="78e40-159">Seu código não deve usar ou depender do nome de um tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="78e40-159">Your code should not use or rely on the name of an anonymous type.</span></span>  
  
 <span data-ttu-id="78e40-160">Como o nome do tipo não está disponível, você não pode usar uma `As` cláusula para declarar `cust13` .</span><span class="sxs-lookup"><span data-stu-id="78e40-160">Because the name of the type is not available, you cannot use an `As` clause to declare `cust13`.</span></span> <span data-ttu-id="78e40-161">Seu tipo deve ser inferido.</span><span class="sxs-lookup"><span data-stu-id="78e40-161">Its type must be inferred.</span></span> <span data-ttu-id="78e40-162">Sem usar a ligação tardia, isso limita o uso de tipos anônimos a variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="78e40-162">Without using late binding, this limits the use of anonymous types to local variables.</span></span>  
  
 <span data-ttu-id="78e40-163">Tipos anônimos fornecem suporte crítico para consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="78e40-163">Anonymous types provide critical support for LINQ queries.</span></span> <span data-ttu-id="78e40-164">Para obter mais informações sobre o uso de tipos anônimos em consultas, consulte [tipos anônimos](anonymous-types.md) e [introdução ao LINQ no Visual Basic](../linq/introduction-to-linq.md).</span><span class="sxs-lookup"><span data-stu-id="78e40-164">For more information about the use of anonymous types in queries, see [Anonymous Types](anonymous-types.md) and [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
### <a name="remarks-about-anonymous-types"></a><span data-ttu-id="78e40-165">Comentários sobre tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="78e40-165">Remarks About Anonymous Types</span></span>  
  
- <span data-ttu-id="78e40-166">Normalmente, todas ou a maioria das propriedades em uma declaração de tipo anônimo serão Propriedades de chave, que são indicadas digitando-se a palavra-chave `Key` na frente do nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="78e40-166">Typically, all or most of the properties in an anonymous type declaration will be key properties, which are indicated by typing the keyword `Key` in front of the property name.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     <span data-ttu-id="78e40-167">Para obter mais informações sobre as propriedades de chave, consulte [chave](../../../language-reference/modifiers/key.md).</span><span class="sxs-lookup"><span data-stu-id="78e40-167">For more information about key properties, see [Key](../../../language-reference/modifiers/key.md).</span></span>  
  
- <span data-ttu-id="78e40-168">Como tipos nomeados, listas de inicializadores para definições de tipo anônimo devem declarar pelo menos uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="78e40-168">Like named types, initializer lists for anonymous type definitions must declare at least one property.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- <span data-ttu-id="78e40-169">Quando uma instância de um tipo anônimo é declarada, o compilador gera uma definição de tipo anônimo correspondente.</span><span class="sxs-lookup"><span data-stu-id="78e40-169">When an instance of an anonymous type is declared, the compiler generates a matching anonymous type definition.</span></span> <span data-ttu-id="78e40-170">Os nomes e tipos de dados das propriedades são obtidos da declaração de instância e são incluídos pelo compilador na definição.</span><span class="sxs-lookup"><span data-stu-id="78e40-170">The names and data types of the properties are taken from the instance declaration, and are included by the compiler in the definition.</span></span> <span data-ttu-id="78e40-171">As propriedades não são nomeadas e definidas com antecedência, como seriam para um tipo nomeado.</span><span class="sxs-lookup"><span data-stu-id="78e40-171">The properties are not named and defined in advance, as they would be for a named type.</span></span> <span data-ttu-id="78e40-172">Seus tipos são inferidos.</span><span class="sxs-lookup"><span data-stu-id="78e40-172">Their types are inferred.</span></span> <span data-ttu-id="78e40-173">Você não pode especificar os tipos de dados das propriedades usando uma `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="78e40-173">You cannot specify the data types of the properties by using an `As` clause.</span></span>  
  
- <span data-ttu-id="78e40-174">Os tipos anônimos também podem estabelecer os nomes e valores de suas propriedades de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="78e40-174">Anonymous types can also establish the names and values of their properties in several other ways.</span></span> <span data-ttu-id="78e40-175">Por exemplo, uma propriedade de tipo anônimo pode pegar o nome e o valor de uma variável, ou o nome e o valor de uma propriedade de outro objeto.</span><span class="sxs-lookup"><span data-stu-id="78e40-175">For example, an anonymous type property can take both the name and the value of a variable, or the name and value of a property of another object.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     <span data-ttu-id="78e40-176">Para obter mais informações sobre as opções para definir propriedades em tipos anônimos, consulte [como: inferir nomes e tipos de propriedade em declarações de tipo anônimo](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="78e40-176">For more information about the options for defining properties in anonymous types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e40-177">Confira também</span><span class="sxs-lookup"><span data-stu-id="78e40-177">See also</span></span>

- [<span data-ttu-id="78e40-178">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="78e40-178">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="78e40-179">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="78e40-179">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="78e40-180">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78e40-180">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="78e40-181">Como inferir nomes e tipos de propriedade na declaração de tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="78e40-181">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="78e40-182">Chave</span><span class="sxs-lookup"><span data-stu-id="78e40-182">Key</span></span>](../../../language-reference/modifiers/key.md)
- [<span data-ttu-id="78e40-183">Como declarar um objeto usando um inicializador de objeto</span><span class="sxs-lookup"><span data-stu-id="78e40-183">How to: Declare an Object by Using an Object Initializer</span></span>](how-to-declare-an-object-by-using-an-object-initializer.md)

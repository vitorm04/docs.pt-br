---
title: 'Como: Definir uma classe que pode fornecer uma funcionalidade idêntica em tipos de dados diferentes (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 9121041f936c091cda0e2af41b4f5be8d826d582
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906627"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="84710-102">Como: Definir uma classe que pode fornecer uma funcionalidade idêntica em tipos de dados diferentes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84710-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="84710-103">Você pode definir uma classe da qual você pode criar objetos que fornecem uma funcionalidade idêntica em tipos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="84710-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="84710-104">Para fazer isso, você especifica um ou mais *parâmetros de tipo* na definição.</span><span class="sxs-lookup"><span data-stu-id="84710-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="84710-105">A classe, em seguida, pode servir como um modelo para objetos que usam vários tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="84710-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="84710-106">Uma classe definida dessa maneira é chamada um *classe genérica*.</span><span class="sxs-lookup"><span data-stu-id="84710-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="84710-107">A vantagem de definir uma classe genérica é que você define apenas uma vez, e seu código pode usá-lo para criar vários objetos que usam uma ampla variedade de tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="84710-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="84710-108">Isso resulta em desempenho melhor do que a definição de classe com o `Object` tipo.</span><span class="sxs-lookup"><span data-stu-id="84710-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="84710-109">Além das classes, você também pode definir e usar delegados, interfaces, procedimentos e estruturas genéricas.</span><span class="sxs-lookup"><span data-stu-id="84710-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="84710-110">Para definir uma classe com um parâmetro de tipo</span><span class="sxs-lookup"><span data-stu-id="84710-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="84710-111">Defina a classe da forma normal.</span><span class="sxs-lookup"><span data-stu-id="84710-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="84710-112">Adicione `(Of` *typeparameter* `)` imediatamente após o nome de classe para especificar um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="84710-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="84710-113">Se você tiver mais de um parâmetro de tipo, faça uma lista separada por vírgulas dentro dos parênteses.</span><span class="sxs-lookup"><span data-stu-id="84710-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="84710-114">Não se repetem o `Of` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="84710-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="84710-115">Se seu código executa operações em um parâmetro de tipo diferente de atribuição simples, siga esse parâmetro de tipo com uma `As` cláusula para adicionar um ou mais *restrições de*.</span><span class="sxs-lookup"><span data-stu-id="84710-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="84710-116">Uma restrição garante que o tipo fornecido para esse parâmetro de tipo satisfaz um requisito, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="84710-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="84710-117">Oferece suporte a uma operação, como `>`, que executa o código</span><span class="sxs-lookup"><span data-stu-id="84710-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="84710-118">Dá suporte a um membro, como um método, que acessa seu código</span><span class="sxs-lookup"><span data-stu-id="84710-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="84710-119">Expõe um construtor sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="84710-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="84710-120">Se você não especificar quaisquer restrições, operações e membros que seu código pode usar somente são aquelas com suporte a [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="84710-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="84710-121">Para obter mais informações, consulte [lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="84710-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="84710-122">Identifique cada membro da classe que deve ser declarado com um tipo fornecido e declará-la `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="84710-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="84710-123">Isso se aplica ao armazenamento interno, parâmetros de procedimento e valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="84710-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="84710-124">Certifique-se de que seu código usa somente operações e métodos que são suportados por qualquer tipo de dados que ele pode fornecer a `itemType`.</span><span class="sxs-lookup"><span data-stu-id="84710-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="84710-125">O exemplo a seguir define uma classe que gerencia uma lista muito simples.</span><span class="sxs-lookup"><span data-stu-id="84710-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="84710-126">Ele contém a lista da matriz interna `items`e o usando o código pode declarar o tipo de dados dos elementos de lista.</span><span class="sxs-lookup"><span data-stu-id="84710-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="84710-127">Um construtor parametrizado permite o uso de código para definir o limite superior de `items`, e o construtor padrão define isso como 9 (para um total de 10 itens).</span><span class="sxs-lookup"><span data-stu-id="84710-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="84710-128">Você pode declarar uma classe de `simpleList` para manter uma lista de `Integer` valores, outra classe para conter uma lista de `String` valores e outra para conter `Date` valores.</span><span class="sxs-lookup"><span data-stu-id="84710-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="84710-129">Com exceção do tipo de dados dos membros da lista, objetos criados a partir de todas essas classes têm comportamento idêntico.</span><span class="sxs-lookup"><span data-stu-id="84710-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="84710-130">O argumento de tipo que o código usado fornece ao `itemType` pode ser um tipo intrínseco, como `Boolean` ou `Double`, uma estrutura, uma enumeração ou qualquer tipo de classe, incluindo um que define seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84710-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="84710-131">Você pode testar a classe `simpleList` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="84710-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="84710-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84710-132">See also</span></span>

- [<span data-ttu-id="84710-133">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="84710-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="84710-134">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84710-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="84710-135">Componentes de independência de linguagem e componentes independentes da linguagem</span><span class="sxs-lookup"><span data-stu-id="84710-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="84710-136">Of</span><span class="sxs-lookup"><span data-stu-id="84710-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="84710-137">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="84710-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="84710-138">Como: usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="84710-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="84710-139">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="84710-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

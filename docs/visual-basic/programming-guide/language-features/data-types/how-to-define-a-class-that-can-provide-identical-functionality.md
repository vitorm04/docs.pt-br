---
title: "Como: definir uma classe que pode fornecer funcionalidade idêntica em tipos de dados diferentes (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data type arguments, using
- type parameters, defining
- data type arguments, defining
- arguments [Visual Basic], data types
- Of keyword, using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters, using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters, type
- type arguments
- types [Visual Basic], generic
- parameters, generic
- type parameters
- data type arguments
- parameters, data type
- generics [Visual Basic], defining generic types
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: faebfcb0b4ea115075c3cbf1666bb8e428a83a23
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="5ca40-102">Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ca40-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="5ca40-103">Você pode definir uma classe da qual você pode criar objetos que fornecem funcionalidade idêntica em tipos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="5ca40-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="5ca40-104">Para fazer isso, você especifica um ou mais *parâmetros de tipo* na definição.</span><span class="sxs-lookup"><span data-stu-id="5ca40-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="5ca40-105">A classe, em seguida, pode servir como um modelo para objetos que usam vários tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="5ca40-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="5ca40-106">Uma classe definida dessa maneira é chamada uma *classe genérica*.</span><span class="sxs-lookup"><span data-stu-id="5ca40-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="5ca40-107">A vantagem de definir uma classe genérica é que você define apenas uma vez, e seu código pode usá-lo para criar vários objetos que usam uma grande variedade de tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="5ca40-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="5ca40-108">Isso resulta em um desempenho melhor que a definição de classe com o `Object` tipo.</span><span class="sxs-lookup"><span data-stu-id="5ca40-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="5ca40-109">Além de classes, você também pode definir e usar delegados, interfaces, procedimentos e estruturas genéricas.</span><span class="sxs-lookup"><span data-stu-id="5ca40-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="5ca40-110">Para definir uma classe com um parâmetro de tipo</span><span class="sxs-lookup"><span data-stu-id="5ca40-110">To define a class with a type parameter</span></span>  
  
1.  <span data-ttu-id="5ca40-111">Defina a classe da forma normal.</span><span class="sxs-lookup"><span data-stu-id="5ca40-111">Define the class in the normal way.</span></span>  
  
2.  <span data-ttu-id="5ca40-112">Adicionar `(Of` *typeparameter* `)` imediatamente após o nome da classe para especificar um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="5ca40-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3.  <span data-ttu-id="5ca40-113">Se você tiver mais de um parâmetro de tipo, faça uma lista separada por vírgulas dentro dos parênteses.</span><span class="sxs-lookup"><span data-stu-id="5ca40-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="5ca40-114">Não se repetem o `Of` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5ca40-114">Do not repeat the `Of` keyword.</span></span>  
  
4.  <span data-ttu-id="5ca40-115">Se seu código executa operações em um parâmetro de tipo diferente de atribuição simples, siga esse parâmetro do tipo com uma `As` cláusula para adicionar um ou mais *restrições*.</span><span class="sxs-lookup"><span data-stu-id="5ca40-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="5ca40-116">Uma restrição garante que o tipo fornecido para esse parâmetro do tipo satisfaça um requisito, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5ca40-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    -   <span data-ttu-id="5ca40-117">Oferece suporte a uma operação, como `>`, que executa o código</span><span class="sxs-lookup"><span data-stu-id="5ca40-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    -   <span data-ttu-id="5ca40-118">Oferece suporte a um membro, como um método, que seu código acessa</span><span class="sxs-lookup"><span data-stu-id="5ca40-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    -   <span data-ttu-id="5ca40-119">Expõe um construtor sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ca40-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="5ca40-120">Se você não especificar quaisquer restrições, operações e membros que seu código pode usar somente são aquelas com suporte a [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="5ca40-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="5ca40-121">Para obter mais informações, consulte [tipo lista](../../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="5ca40-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5.  <span data-ttu-id="5ca40-122">Identifique cada membro da classe que será declarado com um tipo fornecido e declare- `As` `typeparameter`.</span><span class="sxs-lookup"><span data-stu-id="5ca40-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="5ca40-123">Isso se aplica a armazenamento interno, parâmetros de procedimento e valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="5ca40-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6.  <span data-ttu-id="5ca40-124">Certifique-se de que seu código use somente operações e métodos que são suportados por qualquer tipo de dados pode ele fornecer a `itemType`.</span><span class="sxs-lookup"><span data-stu-id="5ca40-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="5ca40-125">O exemplo a seguir define uma classe que gerencia uma lista muito simples.</span><span class="sxs-lookup"><span data-stu-id="5ca40-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="5ca40-126">Ele contém a lista da matriz interna `items`e o uso de código pode declarar o tipo de dados dos elementos de lista.</span><span class="sxs-lookup"><span data-stu-id="5ca40-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="5ca40-127">Um construtor parametrizado permite o uso de código para definir o limite superior de `items`, e o construtor padrão define esta como 9 (para um total de 10 itens).</span><span class="sxs-lookup"><span data-stu-id="5ca40-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the default constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     <span data-ttu-id="5ca40-128">[!code-vb[VbVbalrDataTypes&#7;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ca40-128">[!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]</span></span>  
  
     <span data-ttu-id="5ca40-129">Você pode declarar uma classe de `simpleList` para manter uma lista de `Integer` valores, outra classe para conter uma lista de `String` valores e outra para conter `Date` valores.</span><span class="sxs-lookup"><span data-stu-id="5ca40-129">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="5ca40-130">Exceto pelo tipo de dados dos membros da lista, objetos criados a partir de todas essas classes tenham comportamento idêntico.</span><span class="sxs-lookup"><span data-stu-id="5ca40-130">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="5ca40-131">O argumento de tipo que o código usado fornece para `itemType` pode ser um tipo intrínseco como `Boolean` ou `Double`, uma estrutura, uma enumeração ou qualquer tipo de classe, inclusive uma que seu aplicativo define.</span><span class="sxs-lookup"><span data-stu-id="5ca40-131">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="5ca40-132">Você pode testar a classe `simpleList` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5ca40-132">You can test the class `simpleList` with the following code.</span></span>  
  
     <span data-ttu-id="5ca40-133">[!code-vb[VbVbalrDataTypes n º&8;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ca40-133">[!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca40-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ca40-134">See Also</span></span>  
 <span data-ttu-id="5ca40-135">[Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ca40-135">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="5ca40-136"> [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="5ca40-136"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="5ca40-137"> [Independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) </span><span class="sxs-lookup"><span data-stu-id="5ca40-137"> [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) </span></span>  
<span data-ttu-id="5ca40-138"> [De](../../../../visual-basic/language-reference/statements/of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="5ca40-138"> [Of](../../../../visual-basic/language-reference/statements/of-clause.md) </span></span>  
<span data-ttu-id="5ca40-139"> [Lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md) </span><span class="sxs-lookup"><span data-stu-id="5ca40-139"> [Type List](../../../../visual-basic/language-reference/statements/type-list.md) </span></span>  
<span data-ttu-id="5ca40-140"> [Como: usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="5ca40-140"> [How to: Use a Generic Class](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="5ca40-141"> [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="5ca40-141"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)</span></span>

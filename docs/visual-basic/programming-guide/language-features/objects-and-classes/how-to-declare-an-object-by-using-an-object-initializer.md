---
title: 'Como: Declarar um objeto usando um inicializador de objeto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 314706207800b2e86aa0032a52d8c50fbb726887
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825126"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="7b0b5-102">Como: Declarar um objeto usando um inicializador de objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b0b5-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="7b0b5-103">Inicializadores de objeto permitem que você declarar e instanciar uma instância de uma classe em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="7b0b5-104">Além disso, você pode inicializar um ou mais membros da instância ao mesmo tempo, sem chamar um construtor com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="7b0b5-105">Quando você usa um inicializador de objeto para criar uma instância de um tipo nomeado, o construtor padrão para a classe é chamado, seguido pela inicialização dos membros designados na ordem em que você especificar.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-105">When you use an object initializer to create an instance of a named type, the default constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="7b0b5-106">O procedimento a seguir mostra como criar uma instância de um `Student` classe de três maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="7b0b5-107">A classe tem nome, sobrenome e propriedades de ano de classe, entre outros.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="7b0b5-108">Cada uma das três declarações cria uma nova instância da `Student`, com a propriedade `First` definida como "Michael," propriedade `Last` definida como "Tucker", e todos os outros membros definidos para seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="7b0b5-109">O resultado de cada declaração no procedimento é equivalente ao exemplo a seguir, que não usa um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="7b0b5-110">Para a implementação do `Student` classe, consulte [como: Criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="7b0b5-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="7b0b5-111">Você pode copiar o código daquele tópico para configurar a classe e criar uma lista de `Student` objetos para trabalhar com.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="7b0b5-112">Para criar um objeto de uma classe nomeada usando um inicializador de objeto</span><span class="sxs-lookup"><span data-stu-id="7b0b5-112">To create an object of a named class by using an object initializer</span></span>  
  
1.  <span data-ttu-id="7b0b5-113">Inicie a declaração como se planejar usar um construtor.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2.  <span data-ttu-id="7b0b5-114">Digite a palavra-chave `With`, seguido por uma lista de inicialização entre chaves.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  <span data-ttu-id="7b0b5-115">Na lista de inicialização, inclua cada propriedade que você deseja inicializar e atribuir um valor inicial a ela.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="7b0b5-116">O nome da propriedade é precedido por um período.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="7b0b5-117">Você pode inicializar um ou mais membros da classe.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-117">You can initialize one or more members of the class.</span></span>  
  
4.  <span data-ttu-id="7b0b5-118">Como alternativa, você pode declarar uma nova instância da classe e, em seguida, atribuir um valor a ela.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="7b0b5-119">Em primeiro lugar, declarar uma instância de `Student`:</span><span class="sxs-lookup"><span data-stu-id="7b0b5-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5.  <span data-ttu-id="7b0b5-120">Começar a criação de uma instância de `Student` da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6.  <span data-ttu-id="7b0b5-121">Tipo `With` e, em seguida, um inicializador de objeto para inicializar um ou mais membros da nova instância.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7.  <span data-ttu-id="7b0b5-122">Você pode simplificar a definição na etapa anterior, omitindo `As Student`.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="7b0b5-123">Se você fizer isso, o compilador determina que `student3` é uma instância de `Student` usando inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="7b0b5-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="7b0b5-124">Para obter mais informações, consulte [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="7b0b5-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b0b5-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b0b5-125">See also</span></span>

- [<span data-ttu-id="7b0b5-126">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="7b0b5-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="7b0b5-127">Como: Criar uma lista de itens</span><span class="sxs-lookup"><span data-stu-id="7b0b5-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="7b0b5-128">Inicializadores de objeto: Tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="7b0b5-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="7b0b5-129">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="7b0b5-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

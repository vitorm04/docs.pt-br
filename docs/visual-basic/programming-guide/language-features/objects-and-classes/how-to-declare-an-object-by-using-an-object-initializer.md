---
title: 'Como: declarar um objeto usando um inicializador de objeto (Visual Basic) | Documentos do Microsoft'
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
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1187fd95334f7b0e6763a227edac2e8174750ef4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="b37b3-102">Como declarar um objeto usando um inicializador de objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b37b3-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="b37b3-103">Inicializadores de objeto permitem que você declarar e instanciar uma instância de uma classe em uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="b37b3-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="b37b3-104">Além disso, você pode inicializar um ou mais membros da instância ao mesmo tempo, sem chamar um construtor com parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b37b3-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="b37b3-105">Quando você usa um inicializador de objeto para criar uma instância de um tipo nomeado, o construtor padrão para a classe é chamado, seguido pela inicialização dos membros designados na ordem que você especifica.</span><span class="sxs-lookup"><span data-stu-id="b37b3-105">When you use an object initializer to create an instance of a named type, the default constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="b37b3-106">O procedimento a seguir mostra como criar uma instância de um `Student` classe de três maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="b37b3-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="b37b3-107">A classe tem primeiro nome, sobrenome e propriedades de ano da classe, entre outros.</span><span class="sxs-lookup"><span data-stu-id="b37b3-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="b37b3-108">Cada uma das três declarações cria uma nova instância de `Student`, com a propriedade `First` definida como "Michael", propriedade `Last` definida como "Tucker", e todos os outros membros definidos com seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="b37b3-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="b37b3-109">O resultado de cada declaração no procedimento é equivalente ao exemplo a seguir, que não usa um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="b37b3-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 <span data-ttu-id="b37b3-110">[!code-vb[20 VbVbalrObjectInit](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b37b3-110">[!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]</span></span>  
  
 <span data-ttu-id="b37b3-111">Para uma implementação do `Student` classe, consulte [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="b37b3-111">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="b37b3-112">Você pode copiar o código daquele tópico para configurar a classe e criar uma lista de `Student` objetos para trabalhar.</span><span class="sxs-lookup"><span data-stu-id="b37b3-112">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="b37b3-113">Para criar um objeto de uma classe nomeada usando um inicializador de objeto</span><span class="sxs-lookup"><span data-stu-id="b37b3-113">To create an object of a named class by using an object initializer</span></span>  
  
1.  <span data-ttu-id="b37b3-114">Comece a declaração como se planejar usar um construtor.</span><span class="sxs-lookup"><span data-stu-id="b37b3-114">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2.  <span data-ttu-id="b37b3-115">Digite a palavra-chave `With`, seguido por uma lista de inicialização entre chaves.</span><span class="sxs-lookup"><span data-stu-id="b37b3-115">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  <span data-ttu-id="b37b3-116">Na lista de inicialização, inclua cada propriedade que você deseja inicializar e atribua um valor inicial a ela.</span><span class="sxs-lookup"><span data-stu-id="b37b3-116">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="b37b3-117">O nome da propriedade é precedido por um período.</span><span class="sxs-lookup"><span data-stu-id="b37b3-117">The name of the property is preceded by a period.</span></span>  
  
     <span data-ttu-id="b37b3-118">[!code-vb[VbVbalrObjectInit&#21;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b37b3-118">[!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]</span></span>  
  
     <span data-ttu-id="b37b3-119">Você pode inicializar um ou mais membros da classe.</span><span class="sxs-lookup"><span data-stu-id="b37b3-119">You can initialize one or more members of the class.</span></span>  
  
4.  <span data-ttu-id="b37b3-120">Como alternativa, você pode declarar uma nova instância da classe e, em seguida, atribuir um valor a ela.</span><span class="sxs-lookup"><span data-stu-id="b37b3-120">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="b37b3-121">Primeiro, declare uma instância de `Student`:</span><span class="sxs-lookup"><span data-stu-id="b37b3-121">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5.  <span data-ttu-id="b37b3-122">Inicie a criação de uma instância de `Student` da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="b37b3-122">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6.  <span data-ttu-id="b37b3-123">Tipo de `With` e, em seguida, um inicializador de objeto para inicializar um ou mais membros da nova instância.</span><span class="sxs-lookup"><span data-stu-id="b37b3-123">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     <span data-ttu-id="b37b3-124">[!code-vb[VbVbalrObjectInit&#22;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b37b3-124">[!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]</span></span>  
  
7.  <span data-ttu-id="b37b3-125">Você pode simplificar a definição na etapa anterior omitindo `As Student`.</span><span class="sxs-lookup"><span data-stu-id="b37b3-125">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="b37b3-126">Se você fizer isso, o compilador determina que `student3` é uma instância de `Student` usando inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="b37b3-126">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     <span data-ttu-id="b37b3-127">[!code-vb[VbVbalrObjectInit&#23;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b37b3-127">[!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]</span></span>  
  
     <span data-ttu-id="b37b3-128">Para obter mais informações, consulte [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="b37b3-128">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b37b3-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b37b3-129">See Also</span></span>  
 <span data-ttu-id="b37b3-130">[Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="b37b3-130">[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="b37b3-131"> [Como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md) </span><span class="sxs-lookup"><span data-stu-id="b37b3-131"> [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md) </span></span>  
<span data-ttu-id="b37b3-132"> [Inicializadores de objeto: Tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="b37b3-132"> [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="b37b3-133"> [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="b37b3-133"> [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span></span>

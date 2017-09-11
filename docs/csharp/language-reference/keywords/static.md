---
title: "static (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8e46dc2f00d1c185379dba1017ca445b9ae5ae72
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="static-c-reference"></a><span data-ttu-id="364b2-102">static (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="364b2-102">static (C# Reference)</span></span>
<span data-ttu-id="364b2-103">Use o modificador `static` para declarar um membro estático que pertença ao próprio tipo, em vez de um objeto específico.</span><span class="sxs-lookup"><span data-stu-id="364b2-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="364b2-104">O modificador `static` pode ser usado com classes, campos, métodos, propriedades, operadores, eventos e construtores, mas não pode ser usado com indexadores, finalizadores ou tipos diferentes de classes.</span><span class="sxs-lookup"><span data-stu-id="364b2-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="364b2-105">Para obter mais informações, consulte [Classes estáticas e membros de classes estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="364b2-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="364b2-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="364b2-106">Example</span></span>  
 <span data-ttu-id="364b2-107">A seguinte classe é declarada como `static` e contém apenas métodos `static`:</span><span class="sxs-lookup"><span data-stu-id="364b2-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 <span data-ttu-id="364b2-108">[!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="364b2-108">[!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]</span></span>  
  
 <span data-ttu-id="364b2-109">Uma constante ou declaração de tipo é, implicitamente, um membro estático.</span><span class="sxs-lookup"><span data-stu-id="364b2-109">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="364b2-110">Um membro estático não pode ser referenciado por meio de uma instância.</span><span class="sxs-lookup"><span data-stu-id="364b2-110">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="364b2-111">Em vez disso, ele é referenciado pelo nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="364b2-111">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="364b2-112">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="364b2-112">For example, consider the following class:</span></span>  
  
 <span data-ttu-id="364b2-113">[!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="364b2-113">[!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]</span></span>  
  
 <span data-ttu-id="364b2-114">Para fazer referência ao membro estático `x`, use o nome totalmente qualificado `MyBaseC.MyStruct.x`, a menos que o membro esteja acessível no mesmo escopo:</span><span class="sxs-lookup"><span data-stu-id="364b2-114">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="364b2-115">Embora uma instância de uma classe contenha uma cópia separada de todos os campos de instância da classe, há apenas uma cópia de cada campo estático.</span><span class="sxs-lookup"><span data-stu-id="364b2-115">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="364b2-116">Não é possível usar [this](../../../csharp/language-reference/keywords/this.md) para referenciar métodos estáticos ou acessadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="364b2-116">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="364b2-117">Se a palavra-chave `static` for aplicada a uma classe, todos os membros da classe deverão ser estáticos.</span><span class="sxs-lookup"><span data-stu-id="364b2-117">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="364b2-118">As classes e as classes estáticas podem ter construtores estáticos.</span><span class="sxs-lookup"><span data-stu-id="364b2-118">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="364b2-119">Os construtores estáticos são chamados em algum ponto entre o momento em que o programa é iniciado e a classe é instanciada.</span><span class="sxs-lookup"><span data-stu-id="364b2-119">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="364b2-120">A palavra-chave `static` tem utilizações mais limitadas do que no C++.</span><span class="sxs-lookup"><span data-stu-id="364b2-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="364b2-121">Para comparar com a palavra-chave do C++, consulte [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static) (Classes de armazenamento (C++)).</span><span class="sxs-lookup"><span data-stu-id="364b2-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="364b2-122">Para demonstrar os membros estáticos, considere uma classe que representa um funcionário da empresa.</span><span class="sxs-lookup"><span data-stu-id="364b2-122">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="364b2-123">Suponha que a classe contém um método para contar funcionários e um campo para armazenar o número de funcionários.</span><span class="sxs-lookup"><span data-stu-id="364b2-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="364b2-124">O método e o campo não pertencem a qualquer instância funcionário.</span><span class="sxs-lookup"><span data-stu-id="364b2-124">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="364b2-125">Em vez disso, eles pertencem à classe empresa.</span><span class="sxs-lookup"><span data-stu-id="364b2-125">Instead they belong to the company class.</span></span> <span data-ttu-id="364b2-126">Portanto, eles devem ser declarados como membros estáticos da classe.</span><span class="sxs-lookup"><span data-stu-id="364b2-126">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="364b2-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="364b2-127">Example</span></span>  
 <span data-ttu-id="364b2-128">Este exemplo lê o nome e a ID de um novo funcionário, incrementa o contador de funcionário em um e exibe as informações do novo funcionário e do novo número de funcionários.</span><span class="sxs-lookup"><span data-stu-id="364b2-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="364b2-129">Para simplificar, este programa lê, do teclado, o número atual de funcionários.</span><span class="sxs-lookup"><span data-stu-id="364b2-129">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="364b2-130">Em um aplicativo real, essas informações devem ser lidas de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="364b2-130">In a real application, this information should be read from a file.</span></span>  
  
 <span data-ttu-id="364b2-131">[!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="364b2-131">[!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="364b2-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="364b2-132">Example</span></span>  
 <span data-ttu-id="364b2-133">Este exemplo mostra que, embora seja possível inicializar um campo estático usando outro campo estático que ainda não foi declarado, os resultados serão indefinidos até que você atribua explicitamente um valor ao campo estático.</span><span class="sxs-lookup"><span data-stu-id="364b2-133">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 <span data-ttu-id="364b2-134">[!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="364b2-134">[!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="364b2-135">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="364b2-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="364b2-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="364b2-136">See Also</span></span>  
 <span data-ttu-id="364b2-137">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="364b2-137">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="364b2-138">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="364b2-138">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="364b2-139">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="364b2-139">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="364b2-140">[Modificadores](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="364b2-140">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="364b2-141">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="364b2-141">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)


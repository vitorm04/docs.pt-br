---
title: abstract (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: d0a51afe61e75b750ed8bf336ca4636cb58dfbba
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44212536"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="6c6e4-102">abstract (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6c6e4-102">abstract (C# Reference)</span></span>
<span data-ttu-id="6c6e4-103">O modificador `abstract` indica que o item que está sendo modificado tem uma implementação ausente ou incompleta.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="6c6e4-104">O modificador abstrato pode ser usado com classes, métodos, propriedades, indexadores e eventos.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="6c6e4-105">Use o modificador `abstract` em uma declaração de classe para indicar que uma classe destina-se apenas a ser uma classe base de outras classes.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.</span></span> <span data-ttu-id="6c6e4-106">Membros marcados como abstratos ou incluídos em uma classe abstrata, devem ser implementados por classes que derivam da classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-106">Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c6e4-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c6e4-107">Example</span></span>  
 <span data-ttu-id="6c6e4-108">Neste exemplo, a classe `Square` deve fornecer uma implementação de `Area` porque deriva de `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="6c6e4-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="6c6e4-109">As classes abstratas têm os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="6c6e4-109">Abstract classes have the following features:</span></span>  
  
-   <span data-ttu-id="6c6e4-110">Uma classe abstrata não pode ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-110">An abstract class cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="6c6e4-111">Uma classe abstrata pode conter acessadores e métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
-   <span data-ttu-id="6c6e4-112">Não é possível modificar uma classe abstrata com o modificador [sealed](../../../csharp/language-reference/keywords/sealed.md) porque os dois modificadores têm significados opostos.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifers have opposite meanings.</span></span> <span data-ttu-id="6c6e4-113">O modificador `sealed` impede que uma classe seja herdada e o modificador `abstract` requer uma classe a ser herdada.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
-   <span data-ttu-id="6c6e4-114">Uma classe não abstrata derivada de uma classe abstrata deve incluir implementações reais de todos os acessadores e métodos abstratos herdados.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="6c6e4-115">Use o modificador `abstract` em uma declaração de método ou propriedade para indicar que o método ou propriedade não contem a implementação.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="6c6e4-116">Os métodos abstratos têm os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="6c6e4-116">Abstract methods have the following features:</span></span>  
  
-   <span data-ttu-id="6c6e4-117">Um método abstrato é implicitamente um método virtual.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-117">An abstract method is implicitly a virtual method.</span></span>  
  
-   <span data-ttu-id="6c6e4-118">Declarações de método abstrato são permitidas apenas em classes abstratas.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
-   <span data-ttu-id="6c6e4-119">Como uma declaração de método abstrato não fornece nenhuma implementação real, não há nenhum corpo de método, a declaração do método simplesmente termina com um ponto e vírgula e não há chaves ({ }) após a assinatura.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="6c6e4-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6c6e4-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="6c6e4-121">A implementação é fornecida por uma [substituição](../../../csharp/language-reference/keywords/override.md) de método, que é um membro de uma classe não abstrata.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-121">The implementation is provided by a method [override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
-   <span data-ttu-id="6c6e4-122">É um erro usar os modificadores [static](../../../csharp/language-reference/keywords/static.md) ou [virtual](../../../csharp/language-reference/keywords/virtual.md) em uma declaração de método abstrato.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="6c6e4-123">Propriedades abstratas se comportam como métodos abstratos, exceto pelas diferenças na sintaxe de declaração e chamada.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="6c6e4-124">É um erro usar o modificador `abstract` em uma propriedade estática.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="6c6e4-125">Uma propriedade herdada abstrata pode ser substituída em uma classe derivada incluindo uma declaração de propriedade que usa o modificador [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="6c6e4-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="6c6e4-126">Para obter mais informações sobre classes abstratas, consulte [Classes e membros de classes abstratos e lacrados](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="6c6e4-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="6c6e4-127">Uma classe abstrata deve fornecer uma implementação para todos os membros de interface.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="6c6e4-128">Uma classe abstrata que implementa uma interface pode mapear os métodos de interface em métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="6c6e4-129">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6c6e4-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="6c6e4-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c6e4-130">Example</span></span>  
 <span data-ttu-id="6c6e4-131">Nesse exemplo, a classe `DerivedClass` é derivada de uma classe abstrata `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="6c6e4-132">A classe abstrata contém um método abstrato, `AbstractMethod` e duas propriedades abstratas, `X` e `Y`.</span><span class="sxs-lookup"><span data-stu-id="6c6e4-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="6c6e4-133">No exemplo anterior, se você tentar instanciar a classe abstrata usando uma instrução como esta:</span><span class="sxs-lookup"><span data-stu-id="6c6e4-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="6c6e4-134">Você receberá uma mensagem de erro informando que o compilador não pode criar uma instância da classe abstrata "BaseClass".</span><span class="sxs-lookup"><span data-stu-id="6c6e4-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6c6e4-135">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6c6e4-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6c6e4-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c6e4-136">See Also</span></span>  

- [<span data-ttu-id="6c6e4-137">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="6c6e4-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6c6e4-138">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6c6e4-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6c6e4-139">Modificadores</span><span class="sxs-lookup"><span data-stu-id="6c6e4-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="6c6e4-140">virtual</span><span class="sxs-lookup"><span data-stu-id="6c6e4-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
- [<span data-ttu-id="6c6e4-141">override</span><span class="sxs-lookup"><span data-stu-id="6c6e4-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
- [<span data-ttu-id="6c6e4-142">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="6c6e4-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

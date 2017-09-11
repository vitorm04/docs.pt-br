---
title: "Como saber a diferença entre passar um struct e passar uma referência de classe para um método (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
caps.latest.revision: 25
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
ms.openlocfilehash: 1a4508c8765ac678fd371180cb0c3ece3e1d9a44
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a><span data-ttu-id="8a3cd-102">Como saber a diferença entre passar um struct e passar uma referência de classe para um método (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8a3cd-102">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method (C# Programming Guide)</span></span>
<span data-ttu-id="8a3cd-103">O exemplo a seguir demonstra como passar um [struct](../../../csharp/language-reference/keywords/struct.md) para um método difere de passar uma instância de [classe](../../../csharp/language-reference/keywords/class.md) para um método.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-103">The following example demonstrates how passing a [struct](../../../csharp/language-reference/keywords/struct.md) to a method differs from passing a [class](../../../csharp/language-reference/keywords/class.md) instance to a method.</span></span> <span data-ttu-id="8a3cd-104">No exemplo, ambos os argumentos (struct e instância de classe) são passados por valor e ambos os métodos alteram o valor de um campo do argumento.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-104">In the example, both of the arguments (struct and class instance) are passed by value, and both methods change the value of one field of the argument.</span></span> <span data-ttu-id="8a3cd-105">No entanto, os resultados dos dois métodos não são os mesmos, pois o que é passado ao passar um struct é diferente do que é passado ao passar uma instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-105">However, the results of the two methods are not the same because what is passed when you pass a struct differs from what is passed when you pass an instance of a class.</span></span>  
  
 <span data-ttu-id="8a3cd-106">Como um struct é um [tipo de valor](../../../csharp/language-reference/keywords/value-types.md), ao [passar um struct por valor](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) a um método, esse método receberá e operará em uma cópia do argumento do struct.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-106">Because a struct is a [value type](../../../csharp/language-reference/keywords/value-types.md), when you [pass a struct by value](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md) to a method, the method receives and operates on a copy of the struct argument.</span></span> <span data-ttu-id="8a3cd-107">O método não tem acesso ao struct original no método de chamada e, portanto, não é possível alterá-lo de forma alguma.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-107">The method has no access to the original struct in the calling method and therefore can't change it in any way.</span></span> <span data-ttu-id="8a3cd-108">O método pode alterar somente a cópia.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-108">The method can change only the copy.</span></span>  
  
 <span data-ttu-id="8a3cd-109">Uma instância de classe é um [tipo de referência](../../../csharp/language-reference/keywords/reference-types.md) e não é um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-109">A class instance is a [reference type](../../../csharp/language-reference/keywords/reference-types.md), not a value type.</span></span> <span data-ttu-id="8a3cd-110">Quando [um tipo de referência é passado por valor](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) a um método, esse método receberá uma cópia da referência para a instância da classe.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-110">When [a reference type is passed by value](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) to a method, the method receives a copy of the reference to the class instance.</span></span> <span data-ttu-id="8a3cd-111">Assim, o método receberá uma cópia do endereço da instância e não uma cópia da própria instância.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-111">That is, the method receives a copy of the address of the instance, not a copy of the instance itself.</span></span> <span data-ttu-id="8a3cd-112">A instância de classe no método de chamada tem um endereço, o parâmetro do método chamado tem uma cópia do endereço e os dois endereços se referem ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-112">The class instance in the calling method has an address, the parameter in the called method has a copy of the address, and both addresses refer to the same object.</span></span> <span data-ttu-id="8a3cd-113">Como o parâmetro contém apenas uma cópia do endereço, o método chamado não pode alterar o endereço da instância de classe no método de chamada.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-113">Because the parameter contains only a copy of the address, the called method cannot change the address of the class instance in the calling method.</span></span> <span data-ttu-id="8a3cd-114">No entanto, o método chamado pode usar o endereço para acessar os membros de classe que o endereço original e a cópia referenciam.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-114">However, the called method can use the address to access the class members that both the original address and the copy reference.</span></span> <span data-ttu-id="8a3cd-115">Se o método chamado alterar um membro de classe, a instância da classe original no método de chamada também será alterada.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-115">If the called method changes a class member, the original class instance in the calling method also changes.</span></span>  
  
 <span data-ttu-id="8a3cd-116">O resultado do exemplo a seguir ilustra a diferença.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-116">The output of the following example illustrates the difference.</span></span> <span data-ttu-id="8a3cd-117">O valor do campo `willIChange` da instância da classe foi alterado pela chamada ao método `ClassTaker`, pois o método usa o endereço no parâmetro para localizar o campo especificado da instância da classe.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-117">The value of the `willIChange` field of the class instance is changed by the call to method `ClassTaker` because the method uses the address in the parameter to find the specified field of the class instance.</span></span> <span data-ttu-id="8a3cd-118">O campo `willIChange` do struct no método de chamada não foi alterado pela chamada ao método `StructTaker`, pois o valor do argumento é uma cópia do próprio struct e não uma cópia de seu endereço.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-118">The `willIChange` field of the struct in the calling method is not changed by the call to method `StructTaker` because the value of the argument is a copy of the struct itself, not a copy of its address.</span></span> <span data-ttu-id="8a3cd-119">`StructTaker` altera a cópia e a cópia será perdida quando a chamada para `StructTaker` for concluída.</span><span class="sxs-lookup"><span data-stu-id="8a3cd-119">`StructTaker` changes the copy, and the copy is lost when the call to `StructTaker` is completed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a3cd-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a3cd-120">Example</span></span>  
 <span data-ttu-id="8a3cd-121">[!code-cs[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8a3cd-121">[!code-cs[csProgGuideObjects#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3cd-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a3cd-122">See Also</span></span>  
 <span data-ttu-id="8a3cd-123">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8a3cd-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8a3cd-124">[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) </span><span class="sxs-lookup"><span data-stu-id="8a3cd-124">[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) </span></span>  
 <span data-ttu-id="8a3cd-125">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span><span class="sxs-lookup"><span data-stu-id="8a3cd-125">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span></span>  
 [<span data-ttu-id="8a3cd-126">Passando parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a3cd-126">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)


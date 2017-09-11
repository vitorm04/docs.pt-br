---
title: "Tipos de ponteiro (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: 19
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
ms.openlocfilehash: 1a4ebc69762f18dc630100b544c18df0f43734ac
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="c5e29-102">Tipos de ponteiro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c5e29-102">Pointer types (C# Programming Guide)</span></span>
<span data-ttu-id="c5e29-103">Em um contexto inseguro, um tipo pode ser de ponteiro, valor ou referência.</span><span class="sxs-lookup"><span data-stu-id="c5e29-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="c5e29-104">Uma declaração de tipo de ponteiro usa uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="c5e29-104">A pointer type declaration takes one of the following forms:</span></span>  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 <span data-ttu-id="c5e29-105">Alguns dos seguintes tipos podem ser um tipo de ponteiro:</span><span class="sxs-lookup"><span data-stu-id="c5e29-105">Any of the following types may be a pointer type:</span></span>  
  
-   <span data-ttu-id="c5e29-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md) ou [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="c5e29-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md), or [bool](../../../csharp/language-reference/keywords/bool.md).</span></span>  
  
-   <span data-ttu-id="c5e29-107">Qualquer tipo [enum](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="c5e29-107">Any [enum](../../../csharp/language-reference/keywords/enum.md) type.</span></span>  
  
-   <span data-ttu-id="c5e29-108">Qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c5e29-108">Any pointer type.</span></span>  
  
-   <span data-ttu-id="c5e29-109">Qualquer struct definido pelo usuário que contenha somente campos de tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c5e29-109">Any user-defined struct type that contains fields of unmanaged types only.</span></span>  
  
 <span data-ttu-id="c5e29-110">Os tipos de ponteiro não são herdados de [objeto](../../../csharp/language-reference/keywords/object.md) e não há nenhuma conversão entre tipos de ponteiro e `object`.</span><span class="sxs-lookup"><span data-stu-id="c5e29-110">Pointer types do not inherit from [object](../../../csharp/language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="c5e29-111">Além disso, as conversões boxing e unboxing não oferecem suporte a ponteiros.</span><span class="sxs-lookup"><span data-stu-id="c5e29-111">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="c5e29-112">No entanto, você pode converter entre diferentes tipos de ponteiro e tipos de ponteiro e tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="c5e29-112">However, you can convert between different pointer types and between pointer types and integral types.</span></span>  
  
 <span data-ttu-id="c5e29-113">Quando você designa vários ponteiros na mesma declaração, o asterisco (*) é escrito junto apenas com o tipo subjacente; ele não é usado como um prefixo para cada nome de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c5e29-113">When you declare multiple pointers in the same declaration, the asterisk (*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="c5e29-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c5e29-114">For example:</span></span>  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 <span data-ttu-id="c5e29-115">Um ponteiro não pode apontar para uma referência ou um [struct](../../../csharp/language-reference/keywords/struct.md) que contenha referências, pois uma referência de objeto pode ser coletada como lixo mesmo se um ponteiro estiver apontando para ela.</span><span class="sxs-lookup"><span data-stu-id="c5e29-115">A pointer cannot point to a reference or to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="c5e29-116">O coletor de lixo não acompanha se um objeto está sendo apontado por qualquer tipo de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c5e29-116">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>  
  
 <span data-ttu-id="c5e29-117">O valor da variável de ponteiro do tipo `myType*` é o endereço de uma variável do tipo `myType`.</span><span class="sxs-lookup"><span data-stu-id="c5e29-117">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="c5e29-118">Estes são exemplos de declarações de tipos de ponteiro:</span><span class="sxs-lookup"><span data-stu-id="c5e29-118">The following are examples of pointer type declarations:</span></span>  
  
|<span data-ttu-id="c5e29-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5e29-119">Example</span></span>|<span data-ttu-id="c5e29-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5e29-120">Description</span></span>|  
|-------------|-----------------|  
|`int* p`|<span data-ttu-id="c5e29-121">`p` é um ponteiro para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="c5e29-121">`p` is a pointer to an integer.</span></span>|  
|`int** p`|<span data-ttu-id="c5e29-122">`p` é um ponteiro para um ponteiro para um inteiro.</span><span class="sxs-lookup"><span data-stu-id="c5e29-122">`p` is a pointer to a pointer to an integer.</span></span>|  
|`int*[] p`|<span data-ttu-id="c5e29-123">`p` é uma matriz unidimensional de ponteiros para inteiros.</span><span class="sxs-lookup"><span data-stu-id="c5e29-123">`p` is a single-dimensional array of pointers to integers.</span></span>|  
|`char* p`|<span data-ttu-id="c5e29-124">`p` é um ponteiro para um caractere.</span><span class="sxs-lookup"><span data-stu-id="c5e29-124">`p` is a pointer to a char.</span></span>|  
|`void* p`|<span data-ttu-id="c5e29-125">`p` é um ponteiro para um tipo desconhecido.</span><span class="sxs-lookup"><span data-stu-id="c5e29-125">`p` is a pointer to an unknown type.</span></span>|  
  
 <span data-ttu-id="c5e29-126">O operador de indireção de ponteiro * pode ser usado para acessar o conteúdo no local apontado pela variável de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c5e29-126">The pointer indirection operator * can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="c5e29-127">Por exemplo, considere a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="c5e29-127">For example, consider the following declaration:</span></span>  
  
```  
int* myVariable;  
```  
  
 <span data-ttu-id="c5e29-128">A expressão `*myVariable` denota a variável `int` encontrada no endereço contido em `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="c5e29-128">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>  
  
 <span data-ttu-id="c5e29-129">Há vários exemplos de ponteiros nos tópicos [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md) e [Conversões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="c5e29-129">There are several examples of pointers in the topics [fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span>  <span data-ttu-id="c5e29-130">O exemplo a seguir mostra a necessidade da palavra-chave `unsafe` e a instrução `fixed` e como incrementar um ponteiro interior.</span><span class="sxs-lookup"><span data-stu-id="c5e29-130">The following example shows the need for the `unsafe` keyword and the `fixed` statement, and how to increment an interior pointer.</span></span>  <span data-ttu-id="c5e29-131">Você pode colar esse código na função principal de um aplicativo de console para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="c5e29-131">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="c5e29-132">(Lembre-se de habilitar o código não seguro no **Designer de Projeto**, escolha **Projeto**, **Propriedades** na barra de menus e selecione **Permitir código não seguro** na guia **Compilar**.)</span><span class="sxs-lookup"><span data-stu-id="c5e29-132">(Remember to enable unsafe code in the **Project Designer**; choose **Project**, **Properties** on the menu bar, and then select **Allow unsafe code** in the **Build** tab.)</span></span>  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 <span data-ttu-id="c5e29-133">Você não pode aplicar o operador de indireção para um ponteiro do tipo `void*`.</span><span class="sxs-lookup"><span data-stu-id="c5e29-133">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="c5e29-134">No entanto, você pode usar uma conversão para converter um ponteiro nulo em qualquer outro tipo de ponteiro e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="c5e29-134">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>  
  
 <span data-ttu-id="c5e29-135">Um ponteiro pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="c5e29-135">A pointer can be `null`.</span></span> <span data-ttu-id="c5e29-136">Aplicar o operador de indireção a um ponteiro nulo causa um comportamento definido por implementação.</span><span class="sxs-lookup"><span data-stu-id="c5e29-136">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>  
  
 <span data-ttu-id="c5e29-137">Lembre-se de que transmitir ponteiros entre métodos pode causar comportamento indefinido.</span><span class="sxs-lookup"><span data-stu-id="c5e29-137">Be aware that passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="c5e29-138">Exemplos estão retornando um ponteiro para uma variável local através de um parâmetro Out ou Ref ou como o resultado da função.</span><span class="sxs-lookup"><span data-stu-id="c5e29-138">Examples are returning a pointer to a local variable through an Out or Ref parameter or as the function result.</span></span> <span data-ttu-id="c5e29-139">Se o ponteiro foi definido em um bloco fixo, a variável à qual ele aponta não pode mais ser corrigida.</span><span class="sxs-lookup"><span data-stu-id="c5e29-139">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>  
  
 <span data-ttu-id="c5e29-140">A tabela a seguir lista os operadores e as instruções que podem operar em ponteiros em um contexto inseguro:</span><span class="sxs-lookup"><span data-stu-id="c5e29-140">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>  
  
|<span data-ttu-id="c5e29-141">Operador/Instrução</span><span class="sxs-lookup"><span data-stu-id="c5e29-141">Operator/Statement</span></span>|<span data-ttu-id="c5e29-142">Use</span><span class="sxs-lookup"><span data-stu-id="c5e29-142">Use</span></span>|  
|-------------------------|---------|  
|*|<span data-ttu-id="c5e29-143">Executa indireção de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c5e29-143">Performs pointer indirection.</span></span>|  
|->|<span data-ttu-id="c5e29-144">Acessa um membro de um struct através de um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c5e29-144">Accesses a member of a struct through a pointer.</span></span>|  
|<span data-ttu-id="c5e29-145">[]</span><span class="sxs-lookup"><span data-stu-id="c5e29-145">[]</span></span>|<span data-ttu-id="c5e29-146">Indexa um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c5e29-146">Indexes a pointer.</span></span>|  
|`&`|<span data-ttu-id="c5e29-147">Obtém o endereço de uma variável.</span><span class="sxs-lookup"><span data-stu-id="c5e29-147">Obtains the address of a variable.</span></span>|  
|<span data-ttu-id="c5e29-148">++ e --</span><span class="sxs-lookup"><span data-stu-id="c5e29-148">++ and --</span></span>|<span data-ttu-id="c5e29-149">Incrementa e decrementa ponteiros.</span><span class="sxs-lookup"><span data-stu-id="c5e29-149">Increments and decrements pointers.</span></span>|  
|<span data-ttu-id="c5e29-150">+ e -</span><span class="sxs-lookup"><span data-stu-id="c5e29-150">+ and -</span></span>|<span data-ttu-id="c5e29-151">Executa aritmética de ponteiros.</span><span class="sxs-lookup"><span data-stu-id="c5e29-151">Performs pointer arithmetic.</span></span>|  
|<span data-ttu-id="c5e29-152">==, !=, \<, >, \<= e >=</span><span class="sxs-lookup"><span data-stu-id="c5e29-152">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="c5e29-153">Compara ponteiros.</span><span class="sxs-lookup"><span data-stu-id="c5e29-153">Compares pointers.</span></span>|  
|`stackalloc`|<span data-ttu-id="c5e29-154">Aloca memória na pilha.</span><span class="sxs-lookup"><span data-stu-id="c5e29-154">Allocates memory on the stack.</span></span>|  
|<span data-ttu-id="c5e29-155">Instrução `fixed`</span><span class="sxs-lookup"><span data-stu-id="c5e29-155">`fixed` statement</span></span>|<span data-ttu-id="c5e29-156">Corrige temporariamente uma variável para que seu endereço possa ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="c5e29-156">Temporarily fixes a variable so that its address may be found.</span></span>|  
  
## <a name="c-language-specification"></a><span data-ttu-id="c5e29-157">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c5e29-157">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5e29-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5e29-158">See Also</span></span>  
 <span data-ttu-id="c5e29-159">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c5e29-159">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c5e29-160">[Código Não Seguro e Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="c5e29-160">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="c5e29-161">[Conversões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="c5e29-161">[Pointer Conversions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md) </span></span>  
 <span data-ttu-id="c5e29-162">[Expressões de Ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="c5e29-162">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="c5e29-163">[Tipos](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="c5e29-163">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="c5e29-164">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="c5e29-164">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="c5e29-165">[Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c5e29-165">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 <span data-ttu-id="c5e29-166">[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) </span><span class="sxs-lookup"><span data-stu-id="c5e29-166">[stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) </span></span>  
 [<span data-ttu-id="c5e29-167">Conversão boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="c5e29-167">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)


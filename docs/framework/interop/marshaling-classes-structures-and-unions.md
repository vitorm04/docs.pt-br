---
title: "Marshaling de classes, estruturas e uniões"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 92146a13438067c25a36d589f7ec7fb148ed825d
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="00c3a-102">Marshaling de classes, estruturas e uniões</span><span class="sxs-lookup"><span data-stu-id="00c3a-102">Marshaling Classes, Structures, and Unions</span></span>
<span data-ttu-id="00c3a-103">Estruturas e classes são semelhantes no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00c3a-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="00c3a-104">Ambas podem ter campos, propriedades e eventos.</span><span class="sxs-lookup"><span data-stu-id="00c3a-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="00c3a-105">Elas também podem ter métodos estáticos e não estáticos.</span><span class="sxs-lookup"><span data-stu-id="00c3a-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="00c3a-106">Uma diferença importante é que estruturas são tipos de valor e classes são tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="00c3a-106">One notable difference is that structures are value types and classes are reference types.</span></span>  
  
 <span data-ttu-id="00c3a-107">A tabela a seguir lista as opções de marshaling de classes, estruturas e uniões, descreve o uso delas e fornece um link para a amostra de invocação de plataforma correspondente.</span><span class="sxs-lookup"><span data-stu-id="00c3a-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>  
  
|<span data-ttu-id="00c3a-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="00c3a-108">Type</span></span>|<span data-ttu-id="00c3a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="00c3a-109">Description</span></span>|<span data-ttu-id="00c3a-110">Amostra</span><span class="sxs-lookup"><span data-stu-id="00c3a-110">Sample</span></span>|  
|----------|-----------------|------------|  
|<span data-ttu-id="00c3a-111">Classe por valor.</span><span class="sxs-lookup"><span data-stu-id="00c3a-111">Class by value.</span></span>|<span data-ttu-id="00c3a-112">Passa uma classe com membros de inteiro como um parâmetro In/Out, como no caso gerenciado.</span><span class="sxs-lookup"><span data-stu-id="00c3a-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|<span data-ttu-id="00c3a-113">Exemplo SysTime</span><span class="sxs-lookup"><span data-stu-id="00c3a-113">SysTime sample</span></span>|  
|<span data-ttu-id="00c3a-114">Estrutura por valor.</span><span class="sxs-lookup"><span data-stu-id="00c3a-114">Structure by value.</span></span>|<span data-ttu-id="00c3a-115">Passa estruturas como parâmetros In.</span><span class="sxs-lookup"><span data-stu-id="00c3a-115">Passes structures as In parameters.</span></span>|<span data-ttu-id="00c3a-116">Amostra de estruturas</span><span class="sxs-lookup"><span data-stu-id="00c3a-116">Structures sample</span></span>|  
|<span data-ttu-id="00c3a-117">Estrutura por referência.</span><span class="sxs-lookup"><span data-stu-id="00c3a-117">Structure by reference.</span></span>|<span data-ttu-id="00c3a-118">Passa estruturas como parâmetros In/Out.</span><span class="sxs-lookup"><span data-stu-id="00c3a-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="00c3a-119">Exemplo de OSInfo</span><span class="sxs-lookup"><span data-stu-id="00c3a-119">OSInfo sample</span></span>|  
|<span data-ttu-id="00c3a-120">Estrutura com estruturas aninhadas (mescladas).</span><span class="sxs-lookup"><span data-stu-id="00c3a-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="00c3a-121">Passa uma classe que representa uma estrutura com estruturas aninhadas na função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="00c3a-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="00c3a-122">A estrutura é mesclada em uma estrutura grande no protótipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="00c3a-122">The structure is flattened to one big structure in the managed prototype.</span></span>|<span data-ttu-id="00c3a-123">Exemplo FindFile</span><span class="sxs-lookup"><span data-stu-id="00c3a-123">FindFile sample</span></span>|  
|<span data-ttu-id="00c3a-124">Estrutura com um ponteiro para outra estrutura.</span><span class="sxs-lookup"><span data-stu-id="00c3a-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="00c3a-125">Passa uma estrutura que contém um ponteiro para uma segunda estrutura como um membro.</span><span class="sxs-lookup"><span data-stu-id="00c3a-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|<span data-ttu-id="00c3a-126">Exemplo de estruturas</span><span class="sxs-lookup"><span data-stu-id="00c3a-126">Structures Sample</span></span>|  
|<span data-ttu-id="00c3a-127">Matriz de estruturas com inteiros por valor.</span><span class="sxs-lookup"><span data-stu-id="00c3a-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="00c3a-128">Passa uma matriz de estruturas que contêm somente inteiros como um parâmetro In/Out.</span><span class="sxs-lookup"><span data-stu-id="00c3a-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="00c3a-129">Os membros da matriz podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="00c3a-129">Members of the array can be changed.</span></span>|<span data-ttu-id="00c3a-130">Exemplo de matrizes</span><span class="sxs-lookup"><span data-stu-id="00c3a-130">Arrays Sample</span></span>|  
|<span data-ttu-id="00c3a-131">Matriz de estruturas com inteiros e cadeias de caracteres por referência.</span><span class="sxs-lookup"><span data-stu-id="00c3a-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="00c3a-132">Passa uma matriz de estruturas que contêm inteiros e cadeias de caracteres como um parâmetro Out.</span><span class="sxs-lookup"><span data-stu-id="00c3a-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="00c3a-133">A função chamada aloca memória para a matriz.</span><span class="sxs-lookup"><span data-stu-id="00c3a-133">The called function allocates memory for the array.</span></span>|<span data-ttu-id="00c3a-134">Exemplo de OutArrayOfStructs</span><span class="sxs-lookup"><span data-stu-id="00c3a-134">OutArrayOfStructs Sample</span></span>|  
|<span data-ttu-id="00c3a-135">Uniões com tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="00c3a-135">Unions with value types.</span></span>|<span data-ttu-id="00c3a-136">Passa uniões com tipos de valor (integer e double).</span><span class="sxs-lookup"><span data-stu-id="00c3a-136">Passes unions with value types (integer and double).</span></span>|<span data-ttu-id="00c3a-137">Exemplo de uniões</span><span class="sxs-lookup"><span data-stu-id="00c3a-137">Unions sample</span></span>|  
|<span data-ttu-id="00c3a-138">Uniões com tipos mistos.</span><span class="sxs-lookup"><span data-stu-id="00c3a-138">Unions with mixed types.</span></span>|<span data-ttu-id="00c3a-139">Passa uniões com tipos mistos (integer e string).</span><span class="sxs-lookup"><span data-stu-id="00c3a-139">Passes unions with mixed types (integer and string).</span></span>|<span data-ttu-id="00c3a-140">Exemplo de uniões</span><span class="sxs-lookup"><span data-stu-id="00c3a-140">Unions sample</span></span>|  
|<span data-ttu-id="00c3a-141">Valores nulos na estrutura.</span><span class="sxs-lookup"><span data-stu-id="00c3a-141">Null values in structure.</span></span>|<span data-ttu-id="00c3a-142">Passa uma referência nula (**Nothing** no Visual Basic) em vez de uma referência a um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="00c3a-142">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="00c3a-143">Exemplo HandleRef</span><span class="sxs-lookup"><span data-stu-id="00c3a-143">HandleRef sample</span></span>|  
  
## <a name="structures-sample"></a><span data-ttu-id="00c3a-144">Amostra de estruturas</span><span class="sxs-lookup"><span data-stu-id="00c3a-144">Structures sample</span></span>  
 <span data-ttu-id="00c3a-145">Este exemplo demonstra como passar uma estrutura que aponta para uma segunda estrutura, passar uma estrutura com uma estrutura inserida e passar uma estrutura com uma matriz inserida.</span><span class="sxs-lookup"><span data-stu-id="00c3a-145">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
 <span data-ttu-id="00c3a-146">A amostra de Structs usa as seguintes funções não gerenciadas, mostradas com a sua declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="00c3a-146">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="00c3a-147">**TestStructInStruct** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="00c3a-147">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   <span data-ttu-id="00c3a-148">**TestStructInStruct3** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="00c3a-148">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   <span data-ttu-id="00c3a-149">**TestArrayInStruct** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="00c3a-149">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 <span data-ttu-id="00c3a-150">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) é uma biblioteca personalizada não gerenciada que contém implementações para as funções listadas anteriormente e quatro estruturas: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="00c3a-150">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="00c3a-151">Essas estruturas contêm os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="00c3a-151">These structures contain the following elements:</span></span>  
  
```  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON, *LP_MYPERSON;  
  
typedef struct _MYPERSON2  
{  
   MYPERSON* person;  
   int age;   
} MYPERSON2, *LP_MYPERSON2;  
  
typedef struct _MYPERSON3  
{  
   MYPERSON person;  
   int age;   
} MYPERSON3;  
  
typedef struct _MYARRAYSTRUCT  
{  
   bool flag;  
   int vals[ 3 ];   
} MYARRAYSTRUCT;  
```  
  
 <span data-ttu-id="00c3a-152">As estruturas gerenciadas `MyPerson`, `MyPerson2`, `MyPerson3` e `MyArrayStruct` têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="00c3a-152">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>  
  
-   <span data-ttu-id="00c3a-153">`MyPerson` contém apenas membros de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="00c3a-153">`MyPerson` contains only string members.</span></span> <span data-ttu-id="00c3a-154">O campo [CharSet](../../../docs/framework/interop/specifying-a-character-set.md) define as cadeias de caracteres em formato ANSI quando passadas para a função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="00c3a-154">The [CharSet](../../../docs/framework/interop/specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>  
  
-   <span data-ttu-id="00c3a-155">`MyPerson2` contém uma **IntPtr** para a estrutura `MyPerson`.</span><span class="sxs-lookup"><span data-stu-id="00c3a-155">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="00c3a-156">O tipo **IntPtr** substitui o ponteiro original para a estrutura não gerenciada porque aplicativos do .NET Framework não usam ponteiros, a menos que o código esteja marcado como **não seguro**.</span><span class="sxs-lookup"><span data-stu-id="00c3a-156">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>  
  
-   <span data-ttu-id="00c3a-157">`MyPerson3` contém `MyPerson` como uma estrutura inserida.</span><span class="sxs-lookup"><span data-stu-id="00c3a-157">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="00c3a-158">Uma estrutura inserida em outra estrutura pode ser mesclada colocando-se os elementos da estrutura inserida diretamente para a estrutura principal ou pode ser deixada como uma estrutura inserida, o que é feito neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="00c3a-158">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>  
  
-   <span data-ttu-id="00c3a-159">`MyArrayStruct` contém uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="00c3a-159">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="00c3a-160">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> define o valor de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para **ByValArray**, que é usado para indicar o número de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="00c3a-160">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>  
  
 <span data-ttu-id="00c3a-161">Para todas as estruturas nesta amostra, o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> é aplicado para garantir que os membros sejam organizados na memória em sequência, na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="00c3a-161">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="00c3a-162">A classe `LibWrap` contém protótipos gerenciados para os métodos `TestStructInStruct`, `TestStructInStruct3` e `TestArrayInStruct` chamados pela classe `App`.</span><span class="sxs-lookup"><span data-stu-id="00c3a-162">The `LibWrap` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="00c3a-163">Cada protótipo declara um único parâmetro, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="00c3a-163">Each prototype declares a single parameter, as follows:</span></span>  
  
-   <span data-ttu-id="00c3a-164">`TestStructInStruct` declara uma referência ao tipo `MyPerson2` como seu parâmetro.</span><span class="sxs-lookup"><span data-stu-id="00c3a-164">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>  
  
-   <span data-ttu-id="00c3a-165">`TestStructInStruct3` declara o tipo `MyPerson3` como seu parâmetro e passa o parâmetro por valor.</span><span class="sxs-lookup"><span data-stu-id="00c3a-165">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>  
  
-   <span data-ttu-id="00c3a-166">`TestArrayInStruct` declara uma referência ao tipo `MyArrayStruct` como seu parâmetro.</span><span class="sxs-lookup"><span data-stu-id="00c3a-166">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>  
  
 <span data-ttu-id="00c3a-167">Estruturas como argumentos para métodos são passadas por valor, a menos que o parâmetro contenha a palavra-chave **ref** (**ByRef** no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="00c3a-167">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="00c3a-168">Por exemplo, o método `TestStructInStruct` passa uma referência (o valor de um endereço) para um objeto do tipo `MyPerson2` para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="00c3a-168">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="00c3a-169">Para manipular a estrutura para a qual `MyPerson2` aponta, a amostra cria um buffer de tamanho especificado e retorna o endereço dele combinando os métodos <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=fullName> e <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="00c3a-169">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=fullName> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> methods.</span></span> <span data-ttu-id="00c3a-170">Em seguida, a amostra copia o conteúdo da estrutura gerenciada para o buffer não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="00c3a-170">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="00c3a-171">Por fim, a amostra usa o método <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=fullName> para realizar marshaling de dados do buffer não gerenciado para um objeto gerenciado e o método <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=fullName> para liberar o bloco de memória não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="00c3a-171">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=fullName> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=fullName> method to free the unmanaged block of memory.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="00c3a-172">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="00c3a-172">Declaring Prototypes</span></span>  
 <span data-ttu-id="00c3a-173">[!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)] [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)] [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-173">[!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)] [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)] [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]</span></span>  
  
### <a name="calling-functions"></a><span data-ttu-id="00c3a-174">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="00c3a-174">Calling Functions</span></span>  
 <span data-ttu-id="00c3a-175">[!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)] [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)] [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-175">[!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)] [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)] [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]</span></span>  
  
## <a name="findfile-sample"></a><span data-ttu-id="00c3a-176">Exemplo FindFile</span><span class="sxs-lookup"><span data-stu-id="00c3a-176">FindFile sample</span></span>  
 <span data-ttu-id="00c3a-177">Esta amostra demonstra como passar uma estrutura que contém uma segunda estrutura inserida para uma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="00c3a-177">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="00c3a-178">Ele também demonstra como usar o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> para declarar uma matriz de tamanho fixo dentro da estrutura.</span><span class="sxs-lookup"><span data-stu-id="00c3a-178">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="00c3a-179">Nesta amostra, os elementos de estrutura inserida são adicionados à estrutura pai.</span><span class="sxs-lookup"><span data-stu-id="00c3a-179">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="00c3a-180">Para obter um exemplo de uma estrutura inserida que não é mesclada, consulte [Amostra de estruturas](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e).</span><span class="sxs-lookup"><span data-stu-id="00c3a-180">For a sample of an embedded structure that is not flattened, see [Structures Sample](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e).</span></span>  
  
 <span data-ttu-id="00c3a-181">A amostra de FindFile usa a seguinte função não gerenciada, mostrada com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="00c3a-181">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="00c3a-182">**FindFirstFile** exportado de Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="00c3a-182">**FindFirstFile** exported from Kernel32.dll.</span></span>  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 <span data-ttu-id="00c3a-183">A estrutura original passada para a função contém os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="00c3a-183">The original structure passed to the function contains the following elements:</span></span>  
  
```  
typedef struct _WIN32_FIND_DATA   
{  
  DWORD    dwFileAttributes;   
  FILETIME ftCreationTime;   
  FILETIME ftLastAccessTime;   
  FILETIME ftLastWriteTime;   
  DWORD    nFileSizeHigh;   
  DWORD    nFileSizeLow;   
  DWORD    dwReserved0;   
  DWORD    dwReserved1;   
  TCHAR    cFileName[ MAX_PATH ];   
  TCHAR    cAlternateFileName[ 14 ];   
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;  
```  
  
 <span data-ttu-id="00c3a-184">Neste exemplo, a classe `FindData` contém um membro de dados correspondente para cada elemento da estrutura original e da estrutura inserida.</span><span class="sxs-lookup"><span data-stu-id="00c3a-184">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="00c3a-185">Em vez de dois buffers de caracteres originais, a classe substitui cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="00c3a-185">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="00c3a-186">**MarshalAsAttribute** define a enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para **ByValTStr**, que é usado para identificar as matrizes de caracteres embutidas e de comprimento fixo que aparecem dentro de estruturas não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="00c3a-186">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>  
  
 <span data-ttu-id="00c3a-187">A classe `LibWrap` contém um protótipo gerenciado do método `FindFirstFile`, que passa a classe `FindData` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="00c3a-187">The `LibWrap` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="00c3a-188">O parâmetro deve ser declarado com os atributos <xref:System.Runtime.InteropServices.InAttribute> e <xref:System.Runtime.InteropServices.OutAttribute> porque as classes, que são tipos de referência, são passadas como parâmetros In por padrão.</span><span class="sxs-lookup"><span data-stu-id="00c3a-188">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="00c3a-189">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="00c3a-189">Declaring Prototypes</span></span>  
 <span data-ttu-id="00c3a-190">[!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)] [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)] [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-190">[!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)] [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)] [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]</span></span>  
  
### <a name="calling-functions"></a><span data-ttu-id="00c3a-191">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="00c3a-191">Calling Functions</span></span>  
 <span data-ttu-id="00c3a-192">[!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)] [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)] [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-192">[!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)] [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)] [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]</span></span>  
  
## <a name="unions-sample"></a><span data-ttu-id="00c3a-193">Exemplo de uniões</span><span class="sxs-lookup"><span data-stu-id="00c3a-193">Unions sample</span></span>  
 <span data-ttu-id="00c3a-194">Este exemplo demonstra como passar estruturas que contêm apenas tipos de valor e estruturas que contém um tipo de valor e uma cadeia de caracteres como parâmetros para uma função não gerenciada esperando uma união.</span><span class="sxs-lookup"><span data-stu-id="00c3a-194">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="00c3a-195">Uma união representa um local de memória que pode ser compartilhado por duas ou mais variáveis.</span><span class="sxs-lookup"><span data-stu-id="00c3a-195">A union represents a memory location that can be shared by two or more variables.</span></span>  
  
 <span data-ttu-id="00c3a-196">A amostra de Unions usa a seguinte função não gerenciada, mostrada com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="00c3a-196">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="00c3a-197">**TestUnion** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="00c3a-197">**TestUnion** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 <span data-ttu-id="00c3a-198">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) é uma biblioteca personalizada não gerenciada que contém uma implementação para a função listada anteriormente e duas uniões, **MYUNION** e **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="00c3a-198">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="00c3a-199">As uniões contêm os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="00c3a-199">The unions contain the following elements:</span></span>  
  
```  
union MYUNION  
{  
    int number;  
    double d;  
}  
  
union MYUNION2  
{  
    int i;  
    char str[128];  
};  
```  
  
 <span data-ttu-id="00c3a-200">No código gerenciado, as uniões são definidas como estruturas.</span><span class="sxs-lookup"><span data-stu-id="00c3a-200">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="00c3a-201">A estrutura `MyUnion` contém dois tipos de valor como membros: um integer e um double.</span><span class="sxs-lookup"><span data-stu-id="00c3a-201">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="00c3a-202">O atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> está definido para controlar a posição precisa de cada membro de dados.</span><span class="sxs-lookup"><span data-stu-id="00c3a-202">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="00c3a-203">O atributo <xref:System.Runtime.InteropServices.FieldOffsetAttribute> indica a posição física dos campos dentro da representação não gerenciada de uma união.</span><span class="sxs-lookup"><span data-stu-id="00c3a-203">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="00c3a-204">Observe que ambos os membros têm os mesmos valores de deslocamento, de modo que os membros podem definir a mesma parte da memória.</span><span class="sxs-lookup"><span data-stu-id="00c3a-204">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>  
  
 <span data-ttu-id="00c3a-205">`MyUnion2_1` e `MyUnion2_2` contêm um tipo de valor (integer) e uma cadeia de caracteres, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="00c3a-205">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="00c3a-206">No código gerenciado, não é permitido que os tipos de valor e os tipos de referência se sobreponham.</span><span class="sxs-lookup"><span data-stu-id="00c3a-206">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="00c3a-207">Esta amostra usa a sobrecarga de método para permitir que o chamador use ambos os tipos ao chamar a mesma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="00c3a-207">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="00c3a-208">O layout de `MyUnion2_1` é explícito e tem um valor de deslocamento preciso.</span><span class="sxs-lookup"><span data-stu-id="00c3a-208">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="00c3a-209">Por outro lado, `MyUnion2_2` tem um layout sequencial, pois layouts explícitos não são permitidos com tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="00c3a-209">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="00c3a-210">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> define a enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para **ByValTStr**, que é usado para identificar as matrizes de caracteres embutidas e de comprimento fixo que aparecem dentro da representação não gerenciada da união.</span><span class="sxs-lookup"><span data-stu-id="00c3a-210">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>  
  
 <span data-ttu-id="00c3a-211">A classe `LibWrap` contém os protótipos para os métodos `TestUnion` e `TestUnion2`.</span><span class="sxs-lookup"><span data-stu-id="00c3a-211">The `LibWrap` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="00c3a-212">`TestUnion2` está sobrecarregado para declarar `MyUnion2_1` ou `MyUnion2_2` como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="00c3a-212">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="00c3a-213">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="00c3a-213">Declaring Prototypes</span></span>  
 <span data-ttu-id="00c3a-214">[!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)] [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)] [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-214">[!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)] [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)] [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]</span></span>  
  
### <a name="calling-functions"></a><span data-ttu-id="00c3a-215">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="00c3a-215">Calling Functions</span></span>  
 <span data-ttu-id="00c3a-216">[!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)] [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)] [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-216">[!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)] [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)] [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]</span></span>  
  
## <a name="systime-sample"></a><span data-ttu-id="00c3a-217">Exemplo SysTime</span><span class="sxs-lookup"><span data-stu-id="00c3a-217">SysTime sample</span></span>  
 <span data-ttu-id="00c3a-218">Este exemplo demonstra como passar um ponteiro para uma classe para uma função não gerenciada que espera um ponteiro para uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="00c3a-218">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>  
  
 <span data-ttu-id="00c3a-219">A amostra de SysTime usa a seguinte função não gerenciada, mostrada com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="00c3a-219">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="00c3a-220">**GetSystemTime** exportado de Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="00c3a-220">**GetSystemTime** exported from Kernel32.dll.</span></span>  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 <span data-ttu-id="00c3a-221">A estrutura original passada para a função contém os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="00c3a-221">The original structure passed to the function contains the following elements:</span></span>  
  
```  
typedef struct _SYSTEMTIME {   
    WORD wYear;   
    WORD wMonth;   
    WORD wDayOfWeek;   
    WORD wDay;   
    WORD wHour;   
    WORD wMinute;   
    WORD wSecond;   
    WORD wMilliseconds;   
} SYSTEMTIME, *PSYSTEMTIME;  
```  
  
 <span data-ttu-id="00c3a-222">Neste exemplo, a classe `SystemTime` contém os elementos da estrutura original representados como membros de classe.</span><span class="sxs-lookup"><span data-stu-id="00c3a-222">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="00c3a-223">O atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> é definido para garantir que os membros sejam organizados na memória em sequência, na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="00c3a-223">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="00c3a-224">A classe `LibWrap` contém um protótipo gerenciado do método `GetSystemTime`, que passa a classe `SystemTime` como um parâmetro In/Out por padrão.</span><span class="sxs-lookup"><span data-stu-id="00c3a-224">The `LibWrap` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="00c3a-225">O parâmetro deve ser declarado com os atributos <xref:System.Runtime.InteropServices.InAttribute> e <xref:System.Runtime.InteropServices.OutAttribute> porque as classes, que são tipos de referência, são passadas como parâmetros In por padrão.</span><span class="sxs-lookup"><span data-stu-id="00c3a-225">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="00c3a-226">Para o chamador receber os resultados, esses [atributos direcionais](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) devem ser aplicados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="00c3a-226">For the caller to receive the results, these [directional attributes](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2) must be applied explicitly.</span></span> <span data-ttu-id="00c3a-227">A classe `App` cria uma nova instância da classe `SystemTime` e acessa seus campos de dados.</span><span class="sxs-lookup"><span data-stu-id="00c3a-227">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>  
  
### <a name="code-samples"></a><span data-ttu-id="00c3a-228">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="00c3a-228">Code Samples</span></span>  
 <span data-ttu-id="00c3a-229">[!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)] [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)] [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-229">[!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)] [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)] [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]</span></span>  
  
## <a name="outarrayofstructs-sample"></a><span data-ttu-id="00c3a-230">Exemplo OutArrayOfStructs</span><span class="sxs-lookup"><span data-stu-id="00c3a-230">OutArrayOfStructs sample</span></span>  
 <span data-ttu-id="00c3a-231">Este exemplo mostra como passar uma matriz de estruturas que contém inteiros e cadeias de caracteres como parâmetros Out para uma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="00c3a-231">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>  
  
 <span data-ttu-id="00c3a-232">Este exemplo demonstra como chamar uma função nativa usando a classe <xref:System.Runtime.InteropServices.Marshal> e usando código não seguro.</span><span class="sxs-lookup"><span data-stu-id="00c3a-232">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>  
  
 <span data-ttu-id="00c3a-233">Esta amostra usa funções wrapper e invocações de plataforma definidas em [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614), também fornecido nos arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="00c3a-233">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614), also provided in the source files.</span></span> <span data-ttu-id="00c3a-234">Ela usa a função `TestOutArrayOfStructs` e a estrutura `MYSTRSTRUCT2`.</span><span class="sxs-lookup"><span data-stu-id="00c3a-234">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="00c3a-235">A estrutura contém os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="00c3a-235">The structure contains the following elements:</span></span>  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 <span data-ttu-id="00c3a-236">A classe `MyStruct` contém um objeto de cadeia de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="00c3a-236">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="00c3a-237">O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> especifica o formato ANSI.</span><span class="sxs-lookup"><span data-stu-id="00c3a-237">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="00c3a-238">`MyUnsafeStruct` é uma estrutura que contém um tipo <xref:System.IntPtr> em vez de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="00c3a-238">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>  
  
 <span data-ttu-id="00c3a-239">A classe `LibWrap` contém o método de protótipo `TestOutArrayOfStructs` sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="00c3a-239">The `LibWrap` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="00c3a-240">Se um método declara um ponteiro como um parâmetro, a classe deve ser marcada com a palavra-chave `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="00c3a-240">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="00c3a-241">Já que [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] não é capaz de usar o código não seguro, o método sobrecarregado, o modificador não seguro e a estrutura `MyUnsafeStruct` são desnecessários.</span><span class="sxs-lookup"><span data-stu-id="00c3a-241">Because [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>  
  
 <span data-ttu-id="00c3a-242">A classe `App` implementa o método `UsingMarshaling`, que executa todas as tarefas necessárias para passar a matriz.</span><span class="sxs-lookup"><span data-stu-id="00c3a-242">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="00c3a-243">A matriz é marcada com a palavra-chave `out` (`ByRef` no Visual Basic) para indicar que os dados passam do receptor para o chamador.</span><span class="sxs-lookup"><span data-stu-id="00c3a-243">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="00c3a-244">A implementação usa os seguintes métodos de classe <xref:System.Runtime.InteropServices.Marshal>:</span><span class="sxs-lookup"><span data-stu-id="00c3a-244">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>  
  
-   <span data-ttu-id="00c3a-245"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> para realizar marshaling de dados do buffer não gerenciado para um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="00c3a-245"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>  
  
-   <span data-ttu-id="00c3a-246"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> para liberar a memória reservada para cadeias de caracteres na estrutura.</span><span class="sxs-lookup"><span data-stu-id="00c3a-246"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>  
  
-   <span data-ttu-id="00c3a-247"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> para liberar a memória reservada para a matriz.</span><span class="sxs-lookup"><span data-stu-id="00c3a-247"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>  
  
 <span data-ttu-id="00c3a-248">Como mencionado anteriormente, o C# permite código não seguro e o [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] não.</span><span class="sxs-lookup"><span data-stu-id="00c3a-248">As previously mentioned, C# allows unsafe code and [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] does not.</span></span> <span data-ttu-id="00c3a-249">Na amostra do C#, `UsingUnsafePointer` é uma implementação de método alternativo que usa ponteiros em vez da classe <xref:System.Runtime.InteropServices.Marshal> para passar de volta a matriz que contém a estrutura `MyUnsafeStruct`.</span><span class="sxs-lookup"><span data-stu-id="00c3a-249">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="00c3a-250">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="00c3a-250">Declaring Prototypes</span></span>  
 <span data-ttu-id="00c3a-251">[!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)] [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)] [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-251">[!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)] [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)] [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]</span></span>  
  
### <a name="calling-functions"></a><span data-ttu-id="00c3a-252">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="00c3a-252">Calling Functions</span></span>  
 <span data-ttu-id="00c3a-253">[!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)] [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)] [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-253">[!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)] [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)] [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c3a-254">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00c3a-254">See Also</span></span>  
 <span data-ttu-id="00c3a-255">[Marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md) </span><span class="sxs-lookup"><span data-stu-id="00c3a-255">[Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md) </span></span>  
 <span data-ttu-id="00c3a-256">[Tipos de Dados de Invocação de Plataforma](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f) </span><span class="sxs-lookup"><span data-stu-id="00c3a-256">[Platform Invoke Data Types](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f) </span></span>  
 <span data-ttu-id="00c3a-257">[Marshaling em cadeias de caracteres](../../../docs/framework/interop/marshaling-strings.md) </span><span class="sxs-lookup"><span data-stu-id="00c3a-257">[Marshaling Strings](../../../docs/framework/interop/marshaling-strings.md) </span></span>  
 [<span data-ttu-id="00c3a-258">Marshaling de matrizes de tipos</span><span class="sxs-lookup"><span data-stu-id="00c3a-258">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)


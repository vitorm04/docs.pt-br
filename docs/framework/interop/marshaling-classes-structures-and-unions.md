---
title: Marshaling de classes, estruturas e uniões
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
ms.openlocfilehash: 708ed6a232950cb69796f105f6f198749ed53a24
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200009"
---
# <a name="marshaling-classes-structures-and-unions"></a><span data-ttu-id="10abd-102">Marshaling de classes, estruturas e uniões</span><span class="sxs-lookup"><span data-stu-id="10abd-102">Marshaling Classes, Structures, and Unions</span></span>

<span data-ttu-id="10abd-103">Estruturas e classes são semelhantes no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10abd-103">Classes and structures are similar in the .NET Framework.</span></span> <span data-ttu-id="10abd-104">Ambas podem ter campos, propriedades e eventos.</span><span class="sxs-lookup"><span data-stu-id="10abd-104">Both can have fields, properties, and events.</span></span> <span data-ttu-id="10abd-105">Elas também podem ter métodos estáticos e não estáticos.</span><span class="sxs-lookup"><span data-stu-id="10abd-105">They can also have static and nonstatic methods.</span></span> <span data-ttu-id="10abd-106">Uma diferença importante é que estruturas são tipos de valor e classes são tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="10abd-106">One notable difference is that structures are value types and classes are reference types.</span></span>

<span data-ttu-id="10abd-107">A tabela a seguir lista as opções de marshaling de classes, estruturas e uniões, descreve o uso delas e fornece um link para a amostra de invocação de plataforma correspondente.</span><span class="sxs-lookup"><span data-stu-id="10abd-107">The following table lists marshaling options for classes, structures, and unions; describes their usage; and provides a link to the corresponding platform invoke sample.</span></span>

|<span data-ttu-id="10abd-108">Type</span><span class="sxs-lookup"><span data-stu-id="10abd-108">Type</span></span>|<span data-ttu-id="10abd-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="10abd-109">Description</span></span>|<span data-ttu-id="10abd-110">Amostra</span><span class="sxs-lookup"><span data-stu-id="10abd-110">Sample</span></span>|
|----------|-----------------|------------|
|<span data-ttu-id="10abd-111">Classe por valor.</span><span class="sxs-lookup"><span data-stu-id="10abd-111">Class by value.</span></span>|<span data-ttu-id="10abd-112">Passa uma classe com membros de inteiro como um parâmetro In/Out, como no caso gerenciado.</span><span class="sxs-lookup"><span data-stu-id="10abd-112">Passes a class with integer members as an In/Out parameter, like the managed case.</span></span>|[<span data-ttu-id="10abd-113">Exemplo SysTime</span><span class="sxs-lookup"><span data-stu-id="10abd-113">SysTime sample</span></span>](#systime-sample)|
|<span data-ttu-id="10abd-114">Estrutura por valor.</span><span class="sxs-lookup"><span data-stu-id="10abd-114">Structure by value.</span></span>|<span data-ttu-id="10abd-115">Passa estruturas como parâmetros In.</span><span class="sxs-lookup"><span data-stu-id="10abd-115">Passes structures as In parameters.</span></span>|[<span data-ttu-id="10abd-116">Exemplo de estruturas</span><span class="sxs-lookup"><span data-stu-id="10abd-116">Structures sample</span></span>](#structures-sample)|
|<span data-ttu-id="10abd-117">Estrutura por referência.</span><span class="sxs-lookup"><span data-stu-id="10abd-117">Structure by reference.</span></span>|<span data-ttu-id="10abd-118">Passa estruturas como parâmetros In/Out.</span><span class="sxs-lookup"><span data-stu-id="10abd-118">Passes structures as In/Out parameters.</span></span>|<span data-ttu-id="10abd-119">[Exemplo de OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10abd-119">[OSInfo sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))</span></span>|
|<span data-ttu-id="10abd-120">Estrutura com estruturas aninhadas (mescladas).</span><span class="sxs-lookup"><span data-stu-id="10abd-120">Structure with nested structures (flattened).</span></span>|<span data-ttu-id="10abd-121">Passa uma classe que representa uma estrutura com estruturas aninhadas na função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="10abd-121">Passes a class that represents a structure with nested structures in the unmanaged function.</span></span> <span data-ttu-id="10abd-122">A estrutura é mesclada em uma estrutura grande no protótipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="10abd-122">The structure is flattened to one big structure in the managed prototype.</span></span>|[<span data-ttu-id="10abd-123">Exemplo FindFile</span><span class="sxs-lookup"><span data-stu-id="10abd-123">FindFile sample</span></span>](#findfile-sample)|
|<span data-ttu-id="10abd-124">Estrutura com um ponteiro para outra estrutura.</span><span class="sxs-lookup"><span data-stu-id="10abd-124">Structure with a pointer to another structure.</span></span>|<span data-ttu-id="10abd-125">Passa uma estrutura que contém um ponteiro para uma segunda estrutura como um membro.</span><span class="sxs-lookup"><span data-stu-id="10abd-125">Passes a structure that contains a pointer to a second structure as a member.</span></span>|[<span data-ttu-id="10abd-126">Exemplo de estruturas</span><span class="sxs-lookup"><span data-stu-id="10abd-126">Structures Sample</span></span>](#structures-sample)|
|<span data-ttu-id="10abd-127">Matriz de estruturas com inteiros por valor.</span><span class="sxs-lookup"><span data-stu-id="10abd-127">Array of structures with integers by value.</span></span>|<span data-ttu-id="10abd-128">Passa uma matriz de estruturas que contêm somente inteiros como um parâmetro In/Out.</span><span class="sxs-lookup"><span data-stu-id="10abd-128">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="10abd-129">Os membros da matriz podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="10abd-129">Members of the array can be changed.</span></span>|[<span data-ttu-id="10abd-130">Exemplo de matrizes</span><span class="sxs-lookup"><span data-stu-id="10abd-130">Arrays Sample</span></span>](marshaling-different-types-of-arrays.md)|
|<span data-ttu-id="10abd-131">Matriz de estruturas com inteiros e cadeias de caracteres por referência.</span><span class="sxs-lookup"><span data-stu-id="10abd-131">Array of structures with integers and strings by reference.</span></span>|<span data-ttu-id="10abd-132">Passa uma matriz de estruturas que contêm inteiros e cadeias de caracteres como um parâmetro Out.</span><span class="sxs-lookup"><span data-stu-id="10abd-132">Passes an array of structures that contain integers and strings as an Out parameter.</span></span> <span data-ttu-id="10abd-133">A função chamada aloca memória para a matriz.</span><span class="sxs-lookup"><span data-stu-id="10abd-133">The called function allocates memory for the array.</span></span>|[<span data-ttu-id="10abd-134">Exemplo de OutArrayOfStructs</span><span class="sxs-lookup"><span data-stu-id="10abd-134">OutArrayOfStructs Sample</span></span>](#outarrayofstructs-sample)|
|<span data-ttu-id="10abd-135">Uniões com tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="10abd-135">Unions with value types.</span></span>|<span data-ttu-id="10abd-136">Passa uniões com tipos de valor (integer e double).</span><span class="sxs-lookup"><span data-stu-id="10abd-136">Passes unions with value types (integer and double).</span></span>|[<span data-ttu-id="10abd-137">Exemplo de uniões</span><span class="sxs-lookup"><span data-stu-id="10abd-137">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="10abd-138">Uniões com tipos mistos.</span><span class="sxs-lookup"><span data-stu-id="10abd-138">Unions with mixed types.</span></span>|<span data-ttu-id="10abd-139">Passa uniões com tipos mistos (integer e string).</span><span class="sxs-lookup"><span data-stu-id="10abd-139">Passes unions with mixed types (integer and string).</span></span>|[<span data-ttu-id="10abd-140">Exemplo de uniões</span><span class="sxs-lookup"><span data-stu-id="10abd-140">Unions sample</span></span>](#unions-sample)|
|<span data-ttu-id="10abd-141">Struct com layout específico da plataforma.</span><span class="sxs-lookup"><span data-stu-id="10abd-141">Struct with platform-specific layout.</span></span>|<span data-ttu-id="10abd-142">Passa um tipo com definições de embalagens nativas.</span><span class="sxs-lookup"><span data-stu-id="10abd-142">Passes a type with native-packing definitions.</span></span>|[<span data-ttu-id="10abd-143">Exemplo de plataforma</span><span class="sxs-lookup"><span data-stu-id="10abd-143">Platform sample</span></span>](#platform-sample)|
|<span data-ttu-id="10abd-144">Valores nulos na estrutura.</span><span class="sxs-lookup"><span data-stu-id="10abd-144">Null values in structure.</span></span>|<span data-ttu-id="10abd-145">Passa uma referência nula (**Nothing** no Visual Basic) em vez de uma referência a um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="10abd-145">Passes a null reference (**Nothing** in Visual Basic) instead of a reference to a value type.</span></span>|<span data-ttu-id="10abd-146">[Exemplo HandleRef](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="10abd-146">[HandleRef sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/hc662t8k(v=vs.85))</span></span>|

## <a name="structures-sample"></a><span data-ttu-id="10abd-147">Amostra de estruturas</span><span class="sxs-lookup"><span data-stu-id="10abd-147">Structures sample</span></span>

<span data-ttu-id="10abd-148">Este exemplo demonstra como passar uma estrutura que aponta para uma segunda estrutura, passar uma estrutura com uma estrutura inserida e passar uma estrutura com uma matriz inserida.</span><span class="sxs-lookup"><span data-stu-id="10abd-148">This sample demonstrates how to pass a structure that points to a second structure, pass a structure with an embedded structure, and pass a structure with an embedded array.</span></span>  
  
<span data-ttu-id="10abd-149">A amostra de Structs usa as seguintes funções não gerenciadas, mostradas com a sua declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="10abd-149">The Structs sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="10abd-150">**TestStructInStruct** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="10abd-150">**TestStructInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    int TestStructInStruct(MYPERSON2* pPerson2);
    ```

- <span data-ttu-id="10abd-151">**TestStructInStruct3** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="10abd-151">**TestStructInStruct3** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestStructInStruct3(MYPERSON3 person3);
    ```

- <span data-ttu-id="10abd-152">**TestArrayInStruct** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="10abd-152">**TestArrayInStruct** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestArrayInStruct(MYARRAYSTRUCT* pStruct);
    ```

<span data-ttu-id="10abd-153">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) é uma biblioteca personalizada não gerenciada que contém implementações para as funções listadas anteriormente e quatro estruturas: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span><span class="sxs-lookup"><span data-stu-id="10abd-153">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and four structures: **MYPERSON**, **MYPERSON2**, **MYPERSON3**, and **MYARRAYSTRUCT**.</span></span> <span data-ttu-id="10abd-154">Essas estruturas contêm os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="10abd-154">These structures contain the following elements:</span></span>

```cpp
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

<span data-ttu-id="10abd-155">As estruturas gerenciadas `MyPerson`, `MyPerson2`, `MyPerson3` e `MyArrayStruct` têm as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="10abd-155">The managed `MyPerson`, `MyPerson2`, `MyPerson3`, and `MyArrayStruct` structures have the following characteristic:</span></span>

- <span data-ttu-id="10abd-156">`MyPerson` contém apenas membros de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="10abd-156">`MyPerson` contains only string members.</span></span> <span data-ttu-id="10abd-157">O campo [CharSet](specifying-a-character-set.md) define as cadeias de caracteres em formato ANSI quando passadas para a função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="10abd-157">The [CharSet](specifying-a-character-set.md) field sets the strings to ANSI format when passed to the unmanaged function.</span></span>

- <span data-ttu-id="10abd-158">`MyPerson2` contém uma **IntPtr** para a estrutura `MyPerson`.</span><span class="sxs-lookup"><span data-stu-id="10abd-158">`MyPerson2` contains an **IntPtr** to the `MyPerson` structure.</span></span> <span data-ttu-id="10abd-159">O tipo **IntPtr** substitui o ponteiro original para a estrutura não gerenciada porque aplicativos do .NET Framework não usam ponteiros, a menos que o código esteja marcado como **não seguro**.</span><span class="sxs-lookup"><span data-stu-id="10abd-159">The **IntPtr** type replaces the original pointer to the unmanaged structure because .NET Framework applications do not use pointers unless the code is marked **unsafe**.</span></span>

- <span data-ttu-id="10abd-160">`MyPerson3` contém `MyPerson` como uma estrutura inserida.</span><span class="sxs-lookup"><span data-stu-id="10abd-160">`MyPerson3` contains `MyPerson` as an embedded structure.</span></span> <span data-ttu-id="10abd-161">Uma estrutura inserida em outra estrutura pode ser mesclada colocando-se os elementos da estrutura inserida diretamente para a estrutura principal ou pode ser deixada como uma estrutura inserida, o que é feito neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="10abd-161">A structure embedded within another structure can be flattened by placing the elements of the embedded structure directly into the main structure, or it can be left as an embedded structure, as is done in this sample.</span></span>

- <span data-ttu-id="10abd-162">`MyArrayStruct` contém uma matriz de inteiros.</span><span class="sxs-lookup"><span data-stu-id="10abd-162">`MyArrayStruct` contains an array of integers.</span></span> <span data-ttu-id="10abd-163">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> define o valor de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para **ByValArray**, que é usado para indicar o número de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="10abd-163">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration value to **ByValArray**, which is used to indicate the number of elements in the array.</span></span>

<span data-ttu-id="10abd-164">Para todas as estruturas nesta amostra, o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> é aplicado para garantir que os membros sejam organizados na memória em sequência, na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="10abd-164">For all structures in this sample, the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is applied to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="10abd-165">A classe `NativeMethods` contém protótipos gerenciados para os métodos `TestStructInStruct`, `TestStructInStruct3` e `TestArrayInStruct` chamados pela classe `App`.</span><span class="sxs-lookup"><span data-stu-id="10abd-165">The `NativeMethods` class contains managed prototypes for the `TestStructInStruct`, `TestStructInStruct3`, and `TestArrayInStruct` methods called by the `App` class.</span></span> <span data-ttu-id="10abd-166">Cada protótipo declara um único parâmetro, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="10abd-166">Each prototype declares a single parameter, as follows:</span></span>

- <span data-ttu-id="10abd-167">`TestStructInStruct` declara uma referência ao tipo `MyPerson2` como seu parâmetro.</span><span class="sxs-lookup"><span data-stu-id="10abd-167">`TestStructInStruct` declares a reference to type `MyPerson2` as its parameter.</span></span>

- <span data-ttu-id="10abd-168">`TestStructInStruct3` declara o tipo `MyPerson3` como seu parâmetro e passa o parâmetro por valor.</span><span class="sxs-lookup"><span data-stu-id="10abd-168">`TestStructInStruct3` declares type `MyPerson3` as its parameter and passes the parameter by value.</span></span>

- <span data-ttu-id="10abd-169">`TestArrayInStruct` declara uma referência ao tipo `MyArrayStruct` como seu parâmetro.</span><span class="sxs-lookup"><span data-stu-id="10abd-169">`TestArrayInStruct` declares a reference to type `MyArrayStruct` as its parameter.</span></span>

<span data-ttu-id="10abd-170">Estruturas como argumentos para métodos são passadas por valor, a menos que o parâmetro contenha a palavra-chave **ref** (**ByRef** no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="10abd-170">Structures as arguments to methods are passed by value unless the parameter contains the **ref** (**ByRef** in Visual Basic) keyword.</span></span> <span data-ttu-id="10abd-171">Por exemplo, o método `TestStructInStruct` passa uma referência (o valor de um endereço) para um objeto do tipo `MyPerson2` para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="10abd-171">For example, the `TestStructInStruct` method passes a reference (the value of an address) to an object of type `MyPerson2` to unmanaged code.</span></span> <span data-ttu-id="10abd-172">Para manipular a estrutura para a qual `MyPerson2` aponta, a amostra cria um buffer de tamanho especificado e retorna o endereço dele combinando os métodos <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> e <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10abd-172">To manipulate the structure that `MyPerson2` points to, the sample creates a buffer of a specified size and returns its address by combining the <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="10abd-173">Em seguida, a amostra copia o conteúdo da estrutura gerenciada para o buffer não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="10abd-173">Next, the sample copies the content of the managed structure to the unmanaged buffer.</span></span> <span data-ttu-id="10abd-174">Por fim, a amostra usa o método <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> para realizar marshaling de dados do buffer não gerenciado para um objeto gerenciado e o método <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> para liberar o bloco de memória não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="10abd-174">Finally, the sample uses the <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> method to marshal data from the unmanaged buffer to a managed object and the <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> method to free the unmanaged block of memory.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="10abd-175">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="10abd-175">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#23](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
[!code-csharp[Conceptual.Interop.Marshaling#23](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
[!code-vb[Conceptual.Interop.Marshaling#23](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]

### <a name="calling-functions"></a><span data-ttu-id="10abd-176">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="10abd-176">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#24](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
[!code-csharp[Conceptual.Interop.Marshaling#24](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
[!code-vb[Conceptual.Interop.Marshaling#24](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]

## <a name="findfile-sample"></a><span data-ttu-id="10abd-177">Exemplo FindFile</span><span class="sxs-lookup"><span data-stu-id="10abd-177">FindFile sample</span></span>

<span data-ttu-id="10abd-178">Esta amostra demonstra como passar uma estrutura que contém uma segunda estrutura inserida para uma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="10abd-178">This sample demonstrates how to pass a structure that contains a second, embedded structure to an unmanaged function.</span></span> <span data-ttu-id="10abd-179">Ele também demonstra como usar o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> para declarar uma matriz de tamanho fixo dentro da estrutura.</span><span class="sxs-lookup"><span data-stu-id="10abd-179">It also demonstrates how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to declare a fixed-length array within the structure.</span></span> <span data-ttu-id="10abd-180">Nesta amostra, os elementos de estrutura inserida são adicionados à estrutura pai.</span><span class="sxs-lookup"><span data-stu-id="10abd-180">In this sample, the embedded structure elements are added to the parent structure.</span></span> <span data-ttu-id="10abd-181">Para obter um exemplo de uma estrutura inserida que não é mesclada, consulte [Amostra de estruturas](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="10abd-181">For a sample of an embedded structure that is not flattened, see [Structures Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100)).</span></span>

<span data-ttu-id="10abd-182">A amostra de FindFile usa a seguinte função não gerenciada, mostrada com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="10abd-182">The FindFile sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="10abd-183">**FindFirstFile** exportado de Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="10abd-183">**FindFirstFile** exported from Kernel32.dll.</span></span>

    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);
    ```

<span data-ttu-id="10abd-184">A estrutura original passada para a função contém os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="10abd-184">The original structure passed to the function contains the following elements:</span></span>

```cpp
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

<span data-ttu-id="10abd-185">Neste exemplo, a classe `FindData` contém um membro de dados correspondente para cada elemento da estrutura original e da estrutura inserida.</span><span class="sxs-lookup"><span data-stu-id="10abd-185">In this sample, the `FindData` class contains a corresponding data member for each element of the original structure and the embedded structure.</span></span> <span data-ttu-id="10abd-186">Em vez de dois buffers de caracteres originais, a classe substitui cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="10abd-186">In place of two original character buffers, the class substitutes strings.</span></span> <span data-ttu-id="10abd-187">**MarshalAsAttribute** define a enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para **ByValTStr**, que é usado para identificar as matrizes de caracteres embutidas e de comprimento fixo que aparecem dentro de estruturas não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="10abd-187">**MarshalAsAttribute** sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged structures.</span></span>

<span data-ttu-id="10abd-188">A classe `NativeMethods` contém um protótipo gerenciado do método `FindFirstFile`, que passa a classe `FindData` como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="10abd-188">The `NativeMethods` class contains a managed prototype of the `FindFirstFile` method, which passes the `FindData` class as a parameter.</span></span> <span data-ttu-id="10abd-189">O parâmetro deve ser declarado com os atributos <xref:System.Runtime.InteropServices.InAttribute> e <xref:System.Runtime.InteropServices.OutAttribute> porque as classes, que são tipos de referência, são passadas como parâmetros In por padrão.</span><span class="sxs-lookup"><span data-stu-id="10abd-189">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="10abd-190">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="10abd-190">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#17](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
[!code-csharp[Conceptual.Interop.Marshaling#17](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
[!code-vb[Conceptual.Interop.Marshaling#17](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]

### <a name="calling-functions"></a><span data-ttu-id="10abd-191">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="10abd-191">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#18](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
[!code-csharp[Conceptual.Interop.Marshaling#18](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]

## <a name="unions-sample"></a><span data-ttu-id="10abd-192">Exemplo de uniões</span><span class="sxs-lookup"><span data-stu-id="10abd-192">Unions sample</span></span>

<span data-ttu-id="10abd-193">Este exemplo demonstra como passar estruturas que contêm apenas tipos de valor e estruturas que contém um tipo de valor e uma cadeia de caracteres como parâmetros para uma função não gerenciada esperando uma união.</span><span class="sxs-lookup"><span data-stu-id="10abd-193">This sample demonstrates how to pass structures containing only value types, and structures containing a value type and a string as parameters to an unmanaged function expecting a union.</span></span> <span data-ttu-id="10abd-194">Uma união representa um local de memória que pode ser compartilhado por duas ou mais variáveis.</span><span class="sxs-lookup"><span data-stu-id="10abd-194">A union represents a memory location that can be shared by two or more variables.</span></span>

<span data-ttu-id="10abd-195">A amostra de Unions usa a seguinte função não gerenciada, mostrada com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="10abd-195">The Unions sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="10abd-196">**TestUnion** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="10abd-196">**TestUnion** exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestUnion(MYUNION u, int type);
    ```

<span data-ttu-id="10abd-197">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) é uma biblioteca personalizada não gerenciada que contém uma implementação para a função listada anteriormente e duas uniões, **MYUNION** e **MYUNION2**.</span><span class="sxs-lookup"><span data-stu-id="10abd-197">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed function and two unions, **MYUNION** and **MYUNION2**.</span></span> <span data-ttu-id="10abd-198">As uniões contêm os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="10abd-198">The unions contain the following elements:</span></span>

```cpp
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

<span data-ttu-id="10abd-199">No código gerenciado, as uniões são definidas como estruturas.</span><span class="sxs-lookup"><span data-stu-id="10abd-199">In managed code, unions are defined as structures.</span></span> <span data-ttu-id="10abd-200">A estrutura `MyUnion` contém dois tipos de valor como membros: um integer e um double.</span><span class="sxs-lookup"><span data-stu-id="10abd-200">The `MyUnion` structure contains two value types as its members: an integer and a double.</span></span> <span data-ttu-id="10abd-201">O atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> está definido para controlar a posição precisa de cada membro de dados.</span><span class="sxs-lookup"><span data-stu-id="10abd-201">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to control the precise position of each data member.</span></span> <span data-ttu-id="10abd-202">O atributo <xref:System.Runtime.InteropServices.FieldOffsetAttribute> indica a posição física dos campos dentro da representação não gerenciada de uma união.</span><span class="sxs-lookup"><span data-stu-id="10abd-202">The <xref:System.Runtime.InteropServices.FieldOffsetAttribute> attribute provides the physical position of fields within the unmanaged representation of a union.</span></span> <span data-ttu-id="10abd-203">Observe que ambos os membros têm os mesmos valores de deslocamento, de modo que os membros podem definir a mesma parte da memória.</span><span class="sxs-lookup"><span data-stu-id="10abd-203">Notice that both members have the same offset values, so the members can define the same piece of memory.</span></span>

<span data-ttu-id="10abd-204">`MyUnion2_1` e `MyUnion2_2` contêm um tipo de valor (integer) e uma cadeia de caracteres, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="10abd-204">`MyUnion2_1` and `MyUnion2_2` contain a value type (integer) and a string, respectively.</span></span> <span data-ttu-id="10abd-205">No código gerenciado, não é permitido que os tipos de valor e os tipos de referência se sobreponham.</span><span class="sxs-lookup"><span data-stu-id="10abd-205">In managed code, value types and reference types are not permitted to overlap.</span></span> <span data-ttu-id="10abd-206">Esta amostra usa a sobrecarga de método para permitir que o chamador use ambos os tipos ao chamar a mesma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="10abd-206">This sample uses method overloading to enable the caller to use both types when calling the same unmanaged function.</span></span> <span data-ttu-id="10abd-207">O layout de `MyUnion2_1` é explícito e tem um valor de deslocamento preciso.</span><span class="sxs-lookup"><span data-stu-id="10abd-207">The layout of `MyUnion2_1` is explicit and has a precise offset value.</span></span> <span data-ttu-id="10abd-208">Por outro lado, `MyUnion2_2` tem um layout sequencial, pois layouts explícitos não são permitidos com tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="10abd-208">In contrast, `MyUnion2_2` has a sequential layout, because explicit layouts are not permitted with reference types.</span></span> <span data-ttu-id="10abd-209">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> define a enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para **ByValTStr**, que é usado para identificar as matrizes de caracteres embutidas e de comprimento fixo que aparecem dentro da representação não gerenciada da união.</span><span class="sxs-lookup"><span data-stu-id="10abd-209">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute sets the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration to **ByValTStr**, which is used to identify the inline, fixed-length character arrays that appear within the unmanaged representation of the union.</span></span>

<span data-ttu-id="10abd-210">A classe `NativeMethods` contém os protótipos para os métodos `TestUnion` e `TestUnion2`.</span><span class="sxs-lookup"><span data-stu-id="10abd-210">The `NativeMethods` class contains the prototypes for the `TestUnion` and `TestUnion2` methods.</span></span> <span data-ttu-id="10abd-211">`TestUnion2` está sobrecarregado para declarar `MyUnion2_1` ou `MyUnion2_2` como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="10abd-211">`TestUnion2` is overloaded to declare `MyUnion2_1` or `MyUnion2_2` as parameters.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="10abd-212">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="10abd-212">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#28](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
[!code-csharp[Conceptual.Interop.Marshaling#28](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
[!code-vb[Conceptual.Interop.Marshaling#28](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]

### <a name="calling-functions"></a><span data-ttu-id="10abd-213">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="10abd-213">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#29](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
[!code-csharp[Conceptual.Interop.Marshaling#29](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
[!code-vb[Conceptual.Interop.Marshaling#29](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]

## <a name="platform-sample"></a><span data-ttu-id="10abd-214">Exemplo de plataforma</span><span class="sxs-lookup"><span data-stu-id="10abd-214">Platform sample</span></span>

<span data-ttu-id="10abd-215">Em alguns cenários, `struct` e `union` os layouts podem diferir dependendo da plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="10abd-215">In some scenarios, `struct` and `union` layouts can differ depending on the targeted platform.</span></span> <span data-ttu-id="10abd-216">Por exemplo, considere o [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) tipo quando definido em um cenário com:</span><span class="sxs-lookup"><span data-stu-id="10abd-216">For example, consider the [`STRRET`](/windows/win32/api/shtypes/ns-shtypes-strret) type when defined in a COM scenario:</span></span>

```c++
#include <pshpack8.h> /* Defines the packing of the struct */
typedef struct _STRRET
    {
    UINT uType;
    /* [switch_is][switch_type] */ union
        {
        /* [case()][string] */ LPWSTR pOleStr;
        /* [case()] */ UINT uOffset;
        /* [case()] */ char cStr[ 260 ];
        }  DUMMYUNIONNAME;
    }  STRRET;
#include <poppack.h>
```

<span data-ttu-id="10abd-217">O acima `struct` é declarado com cabeçalhos do Windows que influenciam o layout de memória do tipo.</span><span class="sxs-lookup"><span data-stu-id="10abd-217">The above `struct` is declared with Windows' headers that influence the memory layout of the type.</span></span> <span data-ttu-id="10abd-218">Quando definido em um ambiente gerenciado, esses detalhes de layout são necessários para interoperar corretamente com o código nativo.</span><span class="sxs-lookup"><span data-stu-id="10abd-218">When defined in a managed environment, these layout details are needed to properly interoperate with native code.</span></span>

<span data-ttu-id="10abd-219">A definição correta gerenciada desse tipo em um processo de 32 bits é:</span><span class="sxs-lookup"><span data-stu-id="10abd-219">The correct managed definition of this type in a 32-bit process is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 264)]
public struct STRRET_32
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(4)]
    public IntPtr pOleStr;

    [FieldOffset(4)]
    public uint uOffset;

    [FieldOffset(4)]
    public IntPtr cStr;
}
```

<span data-ttu-id="10abd-220">Em um processo de 64 bits, os deslocamentos de tamanho *e* campo são diferentes.</span><span class="sxs-lookup"><span data-stu-id="10abd-220">On a 64-bit process, the size *and* field offsets are different.</span></span> <span data-ttu-id="10abd-221">O layout correto é:</span><span class="sxs-lookup"><span data-stu-id="10abd-221">The correct layout is:</span></span>

``` CSharp
[StructLayout(LayoutKind.Explicit, Size = 272)]
public struct STRRET_64
{
    [FieldOffset(0)]
    public uint uType;

    [FieldOffset(8)]
    public IntPtr pOleStr;

    [FieldOffset(8)]
    public uint uOffset;

    [FieldOffset(8)]
    public IntPtr cStr;
}
```

<span data-ttu-id="10abd-222">A falha em considerar corretamente o layout nativo em um cenário de interoperabilidade pode resultar em falhas aleatórias ou em piores cálculos incorretos.</span><span class="sxs-lookup"><span data-stu-id="10abd-222">Failure to properly consider the native layout in an interop scenario can result in random crashes or worse, incorrect computations.</span></span>

<span data-ttu-id="10abd-223">Por padrão, os assemblies do .NET podem ser executados em uma versão de 32 bits e 64 bits do tempo de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="10abd-223">By default, .NET assemblies can run in both a 32-bit and 64-bit version of the .NET runtime.</span></span> <span data-ttu-id="10abd-224">O aplicativo deve aguardar até que o tempo de execução decida qual das definições anteriores usar.</span><span class="sxs-lookup"><span data-stu-id="10abd-224">The app must wait until run time to decide which of the previous definitions to use.</span></span>

<span data-ttu-id="10abd-225">O trecho de código a seguir mostra um exemplo de como escolher entre a definição de 32 bits e de 64 bits em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="10abd-225">The following code snippet shows an example of how to choose between the 32-bit and 64-bit definition at run time.</span></span>

```CSharp
if (IntPtr.Size == 8)
{
    // Use the STRRET_64 definition
}
else
{
    Debug.Assert(IntPtr.Size == 4);
    // Use the STRRET_32 definition
}
```

## <a name="systime-sample"></a><span data-ttu-id="10abd-226">Exemplo SysTime</span><span class="sxs-lookup"><span data-stu-id="10abd-226">SysTime sample</span></span>

<span data-ttu-id="10abd-227">Este exemplo demonstra como passar um ponteiro para uma classe para uma função não gerenciada que espera um ponteiro para uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="10abd-227">This sample demonstrates how to pass a pointer to a class to an unmanaged function that expects a pointer to a structure.</span></span>

<span data-ttu-id="10abd-228">A amostra de SysTime usa a seguinte função não gerenciada, mostrada com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="10abd-228">The SysTime sample uses the following unmanaged function, shown with its original function declaration:</span></span>

- <span data-ttu-id="10abd-229">**GetSystemTime** exportado de Kernel32.dll.</span><span class="sxs-lookup"><span data-stu-id="10abd-229">**GetSystemTime** exported from Kernel32.dll.</span></span>

    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);
    ```

<span data-ttu-id="10abd-230">A estrutura original passada para a função contém os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="10abd-230">The original structure passed to the function contains the following elements:</span></span>

```cpp
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

<span data-ttu-id="10abd-231">Neste exemplo, a classe `SystemTime` contém os elementos da estrutura original representados como membros de classe.</span><span class="sxs-lookup"><span data-stu-id="10abd-231">In this sample, the `SystemTime` class contains the elements of the original structure represented as class members.</span></span> <span data-ttu-id="10abd-232">O atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> é definido para garantir que os membros sejam organizados na memória em sequência, na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="10abd-232">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>

<span data-ttu-id="10abd-233">A classe `NativeMethods` contém um protótipo gerenciado do método `GetSystemTime`, que passa a classe `SystemTime` como um parâmetro In/Out por padrão.</span><span class="sxs-lookup"><span data-stu-id="10abd-233">The `NativeMethods` class contains a managed prototype of the `GetSystemTime` method, which passes the `SystemTime` class as an In/Out parameter by default.</span></span> <span data-ttu-id="10abd-234">O parâmetro deve ser declarado com os atributos <xref:System.Runtime.InteropServices.InAttribute> e <xref:System.Runtime.InteropServices.OutAttribute> porque as classes, que são tipos de referência, são passadas como parâmetros In por padrão.</span><span class="sxs-lookup"><span data-stu-id="10abd-234">The parameter must be declared with the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes because classes, which are reference types, are passed as In parameters by default.</span></span> <span data-ttu-id="10abd-235">Para o chamador receber os resultados, esses [atributos direcionais](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) devem ser aplicados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="10abd-235">For the caller to receive the results, these [directional attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) must be applied explicitly.</span></span> <span data-ttu-id="10abd-236">A classe `App` cria uma nova instância da classe `SystemTime` e acessa seus campos de dados.</span><span class="sxs-lookup"><span data-stu-id="10abd-236">The `App` class creates a new instance of the `SystemTime` class and accesses its data fields.</span></span>

### <a name="code-samples"></a><span data-ttu-id="10abd-237">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="10abd-237">Code Samples</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#25](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
[!code-csharp[Conceptual.Interop.Marshaling#25](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
[!code-vb[Conceptual.Interop.Marshaling#25](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]

## <a name="outarrayofstructs-sample"></a><span data-ttu-id="10abd-238">Exemplo OutArrayOfStructs</span><span class="sxs-lookup"><span data-stu-id="10abd-238">OutArrayOfStructs sample</span></span>

<span data-ttu-id="10abd-239">Este exemplo mostra como passar uma matriz de estruturas que contém inteiros e cadeias de caracteres como parâmetros Out para uma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="10abd-239">This sample shows how to pass an array of structures that contains integers and strings as Out parameters to an unmanaged function.</span></span>

<span data-ttu-id="10abd-240">Este exemplo demonstra como chamar uma função nativa usando a classe <xref:System.Runtime.InteropServices.Marshal> e usando código não seguro.</span><span class="sxs-lookup"><span data-stu-id="10abd-240">This sample demonstrates how to call a native function by using the <xref:System.Runtime.InteropServices.Marshal> class and by using unsafe code.</span></span>

<span data-ttu-id="10abd-241">Esta amostra usa funções wrapper e invocações de plataforma definidas em [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), também fornecido nos arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="10abd-241">This sample uses a wrapper functions and platform invokes defined in [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll), also provided in the source files.</span></span> <span data-ttu-id="10abd-242">Ela usa a função `TestOutArrayOfStructs` e a estrutura `MYSTRSTRUCT2`.</span><span class="sxs-lookup"><span data-stu-id="10abd-242">It uses the `TestOutArrayOfStructs` function and the `MYSTRSTRUCT2` structure.</span></span> <span data-ttu-id="10abd-243">A estrutura contém os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="10abd-243">The structure contains the following elements:</span></span>

```cpp
typedef struct _MYSTRSTRUCT2
{
   char* buffer;
   UINT size;
} MYSTRSTRUCT2;
```

<span data-ttu-id="10abd-244">A classe `MyStruct` contém um objeto de cadeia de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="10abd-244">The `MyStruct` class contains a string object of ANSI characters.</span></span> <span data-ttu-id="10abd-245">O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> especifica o formato ANSI.</span><span class="sxs-lookup"><span data-stu-id="10abd-245">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field specifies ANSI format.</span></span> <span data-ttu-id="10abd-246">`MyUnsafeStruct` é uma estrutura que contém um tipo <xref:System.IntPtr> em vez de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="10abd-246">`MyUnsafeStruct`, is a structure containing an <xref:System.IntPtr> type instead of a string.</span></span>

<span data-ttu-id="10abd-247">A classe `NativeMethods` contém o método de protótipo `TestOutArrayOfStructs` sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="10abd-247">The `NativeMethods` class contains the overloaded `TestOutArrayOfStructs` prototype method.</span></span> <span data-ttu-id="10abd-248">Se um método declara um ponteiro como um parâmetro, a classe deve ser marcada com a palavra-chave `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="10abd-248">If a method declares a pointer as a parameter, the class should be marked with the `unsafe` keyword.</span></span> <span data-ttu-id="10abd-249">Já que Visual Basic não é capaz de usar código não gerenciado, o método sobrecarregado, o modificador não seguro e a estrutura `MyUnsafeStruct` são desnecessários.</span><span class="sxs-lookup"><span data-stu-id="10abd-249">Because Visual Basic cannot use unsafe code, the overloaded method, unsafe modifier, and the `MyUnsafeStruct` structure are unnecessary.</span></span>

<span data-ttu-id="10abd-250">A classe `App` implementa o método `UsingMarshaling`, que executa todas as tarefas necessárias para passar a matriz.</span><span class="sxs-lookup"><span data-stu-id="10abd-250">The `App` class implements the `UsingMarshaling` method, which performs all the tasks necessary to pass the array.</span></span> <span data-ttu-id="10abd-251">A matriz é marcada com a palavra-chave `out` (`ByRef` no Visual Basic) para indicar que os dados passam do receptor para o chamador.</span><span class="sxs-lookup"><span data-stu-id="10abd-251">The array is marked with the `out` (`ByRef` in Visual Basic) keyword to indicate that data passes from callee to caller.</span></span> <span data-ttu-id="10abd-252">A implementação usa os seguintes métodos de classe <xref:System.Runtime.InteropServices.Marshal>:</span><span class="sxs-lookup"><span data-stu-id="10abd-252">The implementation uses the following <xref:System.Runtime.InteropServices.Marshal> class methods:</span></span>

- <span data-ttu-id="10abd-253"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> para realizar marshaling de dados do buffer não gerenciado para um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="10abd-253"><xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> to marshal data from the unmanaged buffer to a managed object.</span></span>

- <span data-ttu-id="10abd-254"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> para liberar a memória reservada para cadeias de caracteres na estrutura.</span><span class="sxs-lookup"><span data-stu-id="10abd-254"><xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> to release the memory reserved for strings in the structure.</span></span>

- <span data-ttu-id="10abd-255"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> para liberar a memória reservada para a matriz.</span><span class="sxs-lookup"><span data-stu-id="10abd-255"><xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> to release the memory reserved for the array.</span></span>

<span data-ttu-id="10abd-256">Como mencionado anteriormente, o C# permite código não gerenciado e o Visual Basic não.</span><span class="sxs-lookup"><span data-stu-id="10abd-256">As previously mentioned, C# allows unsafe code and Visual Basic does not.</span></span> <span data-ttu-id="10abd-257">Na amostra do C#, `UsingUnsafePointer` é uma implementação de método alternativo que usa ponteiros em vez da classe <xref:System.Runtime.InteropServices.Marshal> para passar de volta a matriz que contém a estrutura `MyUnsafeStruct`.</span><span class="sxs-lookup"><span data-stu-id="10abd-257">In the C# sample, `UsingUnsafePointer` is an alternative method implementation that uses pointers instead of the <xref:System.Runtime.InteropServices.Marshal> class to pass back the array containing the `MyUnsafeStruct` structure.</span></span>

### <a name="declaring-prototypes"></a><span data-ttu-id="10abd-258">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="10abd-258">Declaring Prototypes</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#20](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
[!code-csharp[Conceptual.Interop.Marshaling#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
[!code-vb[Conceptual.Interop.Marshaling#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]

### <a name="calling-functions"></a><span data-ttu-id="10abd-259">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="10abd-259">Calling Functions</span></span>

[!code-cpp[Conceptual.Interop.Marshaling#21](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
[!code-csharp[Conceptual.Interop.Marshaling#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
[!code-vb[Conceptual.Interop.Marshaling#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]

## <a name="see-also"></a><span data-ttu-id="10abd-260">Confira também</span><span class="sxs-lookup"><span data-stu-id="10abd-260">See also</span></span>

- [<span data-ttu-id="10abd-261">Marshaling de dados com invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="10abd-261">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
- [<span data-ttu-id="10abd-262">Realizando marshaling de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="10abd-262">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="10abd-263">Marshaling de diversos tipos de matrizes</span><span class="sxs-lookup"><span data-stu-id="10abd-263">Marshaling Different Types of Arrays</span></span>](marshaling-different-types-of-arrays.md)

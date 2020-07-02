---
title: Marshaling de diversos tipos de matrizes
description: Empacotar tipos de matriz diferentes, como inteiros por valor ou referência, inteiros bidimensionais por valor, cadeias de caracteres por valor e estruturas com números inteiros ou cadeias de caracteres.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: f1473c7917189f0b36c96b2adcf20005c5fd6b48
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621490"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="f838f-103">Marshaling de diversos tipos de matrizes</span><span class="sxs-lookup"><span data-stu-id="f838f-103">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="f838f-104">Uma matriz é um tipo de referência em código gerenciado que contém um ou mais elementos do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="f838f-104">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="f838f-105">Embora as matrizes sejam tipos de referência, elas são passadas como parâmetros para funções não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="f838f-105">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="f838f-106">Esse comportamento é inconsistente com a maneira que matrizes gerenciadas são passadas para objetos gerenciados, que é na forma de parâmetros de In/Out.</span><span class="sxs-lookup"><span data-stu-id="f838f-106">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="f838f-107">Para obter detalhes adicionais, consulte [Copiando e fixando](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="f838f-107">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="f838f-108">A tabela a seguir lista as opções de marshaling para matrizes e descreve o uso delas.</span><span class="sxs-lookup"><span data-stu-id="f838f-108">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="f838f-109">Array</span><span class="sxs-lookup"><span data-stu-id="f838f-109">Array</span></span>|<span data-ttu-id="f838f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f838f-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f838f-111">De inteiros por valor.</span><span class="sxs-lookup"><span data-stu-id="f838f-111">Of integers by value.</span></span>|<span data-ttu-id="f838f-112">Passa uma matriz de inteiros como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="f838f-112">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="f838f-113">De inteiros por referência.</span><span class="sxs-lookup"><span data-stu-id="f838f-113">Of integers by reference.</span></span>|<span data-ttu-id="f838f-114">Passa uma matriz de inteiros como um parâmetro In/Out.</span><span class="sxs-lookup"><span data-stu-id="f838f-114">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="f838f-115">De inteiros por valor (bidimensional).</span><span class="sxs-lookup"><span data-stu-id="f838f-115">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="f838f-116">Passa uma matriz de inteiros como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="f838f-116">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="f838f-117">De cadeias de caracteres por valor.</span><span class="sxs-lookup"><span data-stu-id="f838f-117">Of strings by value.</span></span>|<span data-ttu-id="f838f-118">Passa uma matriz de cadeias de caracteres como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="f838f-118">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="f838f-119">De estruturas com inteiros.</span><span class="sxs-lookup"><span data-stu-id="f838f-119">Of structures with integers.</span></span>|<span data-ttu-id="f838f-120">Passa uma matriz de estruturas que contêm inteiros como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="f838f-120">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="f838f-121">De estruturas com cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f838f-121">Of structures with strings.</span></span>|<span data-ttu-id="f838f-122">Passa uma matriz de estruturas que contêm somente cadeias de caracteres como um parâmetro Entrada/Saída.</span><span class="sxs-lookup"><span data-stu-id="f838f-122">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="f838f-123">Os membros da matriz podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="f838f-123">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f838f-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f838f-124">Example</span></span>  
 <span data-ttu-id="f838f-125">Este exemplo demonstra como passar os seguintes tipos de matrizes:</span><span class="sxs-lookup"><span data-stu-id="f838f-125">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
- <span data-ttu-id="f838f-126">Matriz de inteiros por valor.</span><span class="sxs-lookup"><span data-stu-id="f838f-126">Array of integers by value.</span></span>  
  
- <span data-ttu-id="f838f-127">Matriz de inteiros por referência, que pode ser redimensionada.</span><span class="sxs-lookup"><span data-stu-id="f838f-127">Array of integers by reference, which can be resized.</span></span>  
  
- <span data-ttu-id="f838f-128">Matriz multidimensional de inteiros por valor.</span><span class="sxs-lookup"><span data-stu-id="f838f-128">Multidimensional array (matrix) of integers by value.</span></span>  
  
- <span data-ttu-id="f838f-129">Matriz de cadeias de caracteres por valor.</span><span class="sxs-lookup"><span data-stu-id="f838f-129">Array of strings by value.</span></span>  
  
- <span data-ttu-id="f838f-130">Matriz de estruturas com inteiros.</span><span class="sxs-lookup"><span data-stu-id="f838f-130">Array of structures with integers.</span></span>  
  
- <span data-ttu-id="f838f-131">Matriz de estruturas com cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f838f-131">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="f838f-132">A menos que o marshaling de uma matriz seja realizado explicitamente por referência, o comportamento padrão realizará o marshaling da matriz como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="f838f-132">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="f838f-133">Você pode alterar esse comportamento ao aplicar os atributos <xref:System.Runtime.InteropServices.InAttribute> e <xref:System.Runtime.InteropServices.OutAttribute> explicitamente.</span><span class="sxs-lookup"><span data-stu-id="f838f-133">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="f838f-134">A amostra de matrizes usa as seguintes funções não gerenciadas, mostradas com a sua declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="f838f-134">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
- <span data-ttu-id="f838f-135">**TestArrayOfInts** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="f838f-135">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- <span data-ttu-id="f838f-136">**TestRefArrayOfInts** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="f838f-136">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- <span data-ttu-id="f838f-137">**TestMatrixOfInts** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="f838f-137">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- <span data-ttu-id="f838f-138">**TestArrayOfStrings** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="f838f-138">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- <span data-ttu-id="f838f-139">**TestArrayOfStructs** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="f838f-139">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- <span data-ttu-id="f838f-140">**TestArrayOfStructs2** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="f838f-140">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="f838f-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) é uma biblioteca personalizada não gerenciada que contém implementações para as funções listadas anteriormente e duas variáveis de estrutura, **MYPOINT** e **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="f838f-141">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="f838f-142">As estruturas contêm os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="f838f-142">The structures contain the following elements:</span></span>  
  
```cpp
typedef struct _MYPOINT  
{  
   int x;
   int y;
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;
   char* last;
} MYPERSON;  
```  
  
 <span data-ttu-id="f838f-143">Neste exemplo, as estruturas `MyPoint` e `MyPerson` contêm tipos inseridos.</span><span class="sxs-lookup"><span data-stu-id="f838f-143">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="f838f-144">O atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> é definido para garantir que os membros sejam organizados na memória em sequência, na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="f838f-144">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="f838f-145">A classe `NativeMethods` contém um conjunto de métodos chamados pela classe `App`.</span><span class="sxs-lookup"><span data-stu-id="f838f-145">The `NativeMethods` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="f838f-146">Para obter detalhes específicos sobre passagem de matrizes, consulte os comentários na amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="f838f-146">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="f838f-147">Uma matriz, que é um tipo de referência, é passada por padrão como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="f838f-147">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="f838f-148">Para o chamador receber os resultados, **InAttribute** e **OutAttribute** devem ser aplicados explicitamente ao argumento que contém a matriz.</span><span class="sxs-lookup"><span data-stu-id="f838f-148">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="f838f-149">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="f838f-149">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="f838f-150">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="f838f-150">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="f838f-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f838f-151">See also</span></span>

- [<span data-ttu-id="f838f-152">Tipos de dados de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="f838f-152">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="f838f-153">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="f838f-153">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)

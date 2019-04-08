---
title: Marshaling de diversos tipos de matrizes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef5c9acab6fd8fa852b619eeeee150eb33b69507
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890430"
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="667ce-102">Marshaling de diversos tipos de matrizes</span><span class="sxs-lookup"><span data-stu-id="667ce-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="667ce-103">Uma matriz é um tipo de referência em código gerenciado que contém um ou mais elementos do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="667ce-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="667ce-104">Embora as matrizes sejam tipos de referência, elas são passadas como parâmetros para funções não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="667ce-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="667ce-105">Esse comportamento é inconsistente com a maneira que matrizes gerenciadas são passadas para objetos gerenciados, que é na forma de parâmetros de In/Out.</span><span class="sxs-lookup"><span data-stu-id="667ce-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="667ce-106">Para obter detalhes adicionais, consulte [Copiando e fixando](copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="667ce-106">For additional details, see [Copying and Pinning](copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="667ce-107">A tabela a seguir lista as opções de marshaling para matrizes e descreve o uso delas.</span><span class="sxs-lookup"><span data-stu-id="667ce-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="667ce-108">Matriz</span><span class="sxs-lookup"><span data-stu-id="667ce-108">Array</span></span>|<span data-ttu-id="667ce-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="667ce-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="667ce-110">De inteiros por valor.</span><span class="sxs-lookup"><span data-stu-id="667ce-110">Of integers by value.</span></span>|<span data-ttu-id="667ce-111">Passa uma matriz de inteiros como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="667ce-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="667ce-112">De inteiros por referência.</span><span class="sxs-lookup"><span data-stu-id="667ce-112">Of integers by reference.</span></span>|<span data-ttu-id="667ce-113">Passa uma matriz de inteiros como um parâmetro In/Out.</span><span class="sxs-lookup"><span data-stu-id="667ce-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="667ce-114">De inteiros por valor (bidimensional).</span><span class="sxs-lookup"><span data-stu-id="667ce-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="667ce-115">Passa uma matriz de inteiros como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="667ce-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="667ce-116">De cadeias de caracteres por valor.</span><span class="sxs-lookup"><span data-stu-id="667ce-116">Of strings by value.</span></span>|<span data-ttu-id="667ce-117">Passa uma matriz de cadeias de caracteres como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="667ce-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="667ce-118">De estruturas com inteiros.</span><span class="sxs-lookup"><span data-stu-id="667ce-118">Of structures with integers.</span></span>|<span data-ttu-id="667ce-119">Passa uma matriz de estruturas que contêm inteiros como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="667ce-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="667ce-120">De estruturas com cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="667ce-120">Of structures with strings.</span></span>|<span data-ttu-id="667ce-121">Passa uma matriz de estruturas que contêm somente cadeias de caracteres como um parâmetro Entrada/Saída.</span><span class="sxs-lookup"><span data-stu-id="667ce-121">Passes an array of structures that contain only strings as an In/Out parameter.</span></span> <span data-ttu-id="667ce-122">Os membros da matriz podem ser alterados.</span><span class="sxs-lookup"><span data-stu-id="667ce-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="667ce-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="667ce-123">Example</span></span>  
 <span data-ttu-id="667ce-124">Este exemplo demonstra como passar os seguintes tipos de matrizes:</span><span class="sxs-lookup"><span data-stu-id="667ce-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
-   <span data-ttu-id="667ce-125">Matriz de inteiros por valor.</span><span class="sxs-lookup"><span data-stu-id="667ce-125">Array of integers by value.</span></span>  
  
-   <span data-ttu-id="667ce-126">Matriz de inteiros por referência, que pode ser redimensionada.</span><span class="sxs-lookup"><span data-stu-id="667ce-126">Array of integers by reference, which can be resized.</span></span>  
  
-   <span data-ttu-id="667ce-127">Matriz multidimensional de inteiros por valor.</span><span class="sxs-lookup"><span data-stu-id="667ce-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
-   <span data-ttu-id="667ce-128">Matriz de cadeias de caracteres por valor.</span><span class="sxs-lookup"><span data-stu-id="667ce-128">Array of strings by value.</span></span>  
  
-   <span data-ttu-id="667ce-129">Matriz de estruturas com inteiros.</span><span class="sxs-lookup"><span data-stu-id="667ce-129">Array of structures with integers.</span></span>  
  
-   <span data-ttu-id="667ce-130">Matriz de estruturas com cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="667ce-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="667ce-131">A menos que o marshaling de uma matriz seja realizado explicitamente por referência, o comportamento padrão realizará o marshaling da matriz como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="667ce-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="667ce-132">Você pode alterar esse comportamento ao aplicar os atributos <xref:System.Runtime.InteropServices.InAttribute> e <xref:System.Runtime.InteropServices.OutAttribute> explicitamente.</span><span class="sxs-lookup"><span data-stu-id="667ce-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="667ce-133">A amostra de matrizes usa as seguintes funções não gerenciadas, mostradas com a sua declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="667ce-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="667ce-134">**TestArrayOfInts** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="667ce-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   <span data-ttu-id="667ce-135">**TestRefArrayOfInts** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="667ce-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   <span data-ttu-id="667ce-136">**TestMatrixOfInts** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="667ce-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   <span data-ttu-id="667ce-137">**TestArrayOfStrings** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="667ce-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   <span data-ttu-id="667ce-138">**TestArrayOfStructs** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="667ce-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   <span data-ttu-id="667ce-139">**TestArrayOfStructs2** exportado de PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="667ce-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="667ce-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) é uma biblioteca personalizada não gerenciada que contém implementações para as funções listadas anteriormente e duas variáveis de estrutura, **MYPOINT** e **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="667ce-140">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="667ce-141">As estruturas contêm os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="667ce-141">The structures contain the following elements:</span></span>  
  
```  
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
  
 <span data-ttu-id="667ce-142">Neste exemplo, as estruturas `MyPoint` e `MyPerson` contêm tipos inseridos.</span><span class="sxs-lookup"><span data-stu-id="667ce-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="667ce-143">O atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> é definido para garantir que os membros sejam organizados na memória em sequência, na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="667ce-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="667ce-144">A classe `LibWrap` contém um conjunto de métodos chamados pela classe `App`.</span><span class="sxs-lookup"><span data-stu-id="667ce-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="667ce-145">Para obter detalhes específicos sobre passagem de matrizes, consulte os comentários na amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="667ce-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="667ce-146">Uma matriz, que é um tipo de referência, é passada por padrão como um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="667ce-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="667ce-147">Para o chamador receber os resultados, **InAttribute** e **OutAttribute** devem ser aplicados explicitamente ao argumento que contém a matriz.</span><span class="sxs-lookup"><span data-stu-id="667ce-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="667ce-148">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="667ce-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="667ce-149">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="667ce-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="667ce-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="667ce-150">See also</span></span>
- [<span data-ttu-id="667ce-151">Tipos de dados de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="667ce-151">Platform invoke data types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="667ce-152">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="667ce-152">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)

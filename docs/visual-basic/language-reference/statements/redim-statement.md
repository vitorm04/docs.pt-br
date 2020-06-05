---
title: Instrução ReDim
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: 82f19762865fdf3c3f32a0349e21e3b97bebd567
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404272"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="ce3f2-102">Instrução ReDim (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce3f2-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="ce3f2-103">Realoca espaço de armazenamento para uma variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce3f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce3f2-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ce3f2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ce3f2-105">Parts</span></span>  
  
|<span data-ttu-id="ce3f2-106">Termo</span><span class="sxs-lookup"><span data-stu-id="ce3f2-106">Term</span></span>|<span data-ttu-id="ce3f2-107">Definição</span><span class="sxs-lookup"><span data-stu-id="ce3f2-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="ce3f2-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-108">Optional.</span></span> <span data-ttu-id="ce3f2-109">Modificador usado para preservar os dados na matriz existente quando você altera o tamanho da última dimensão.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="ce3f2-110">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-110">Required.</span></span> <span data-ttu-id="ce3f2-111">Nome da variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-111">Name of the array variable.</span></span> <span data-ttu-id="ce3f2-112">Consulte [nomes de elementos declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ce3f2-112">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="ce3f2-113">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-113">Required.</span></span> <span data-ttu-id="ce3f2-114">Lista de limites de cada dimensão da matriz redefinida.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce3f2-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce3f2-115">Remarks</span></span>  
 <span data-ttu-id="ce3f2-116">Você pode usar a `ReDim` instrução para alterar o tamanho de uma ou mais dimensões de uma matriz que já foi declarada.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="ce3f2-117">Se você tiver uma matriz grande e não precisar mais de alguns de seus elementos, o `ReDim` poderá liberar memória reduzindo o tamanho da matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="ce3f2-118">Por outro lado, se sua matriz precisar de mais elementos, o `ReDim` poderá adicioná-los.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="ce3f2-119">A `ReDim` instrução é destinada apenas a matrizes.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="ce3f2-120">Não é válido em escalares (variáveis que contêm apenas um único valor), coleções ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="ce3f2-121">Observe que, se você declarar uma variável para ser do tipo `Array` , a `ReDim` instrução não terá informações de tipo suficientes para criar a nova matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="ce3f2-122">Você pode usar `ReDim` somente no nível do procedimento.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="ce3f2-123">Portanto, o contexto da declaração para a variável deve ser um procedimento; Ele não pode ser um arquivo de origem, um namespace, uma interface, uma classe, uma estrutura, um módulo ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="ce3f2-124">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ce3f2-124">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ce3f2-125">Regras</span><span class="sxs-lookup"><span data-stu-id="ce3f2-125">Rules</span></span>  
  
- <span data-ttu-id="ce3f2-126">**Várias variáveis.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-126">**Multiple Variables.**</span></span> <span data-ttu-id="ce3f2-127">Você pode redimensionar várias variáveis de matriz na mesma instrução de declaração e especificar as `name` `boundlist` partes e para cada variável.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="ce3f2-128">Várias variáveis são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="ce3f2-129">**Limites de matriz.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-129">**Array Bounds.**</span></span> <span data-ttu-id="ce3f2-130">Cada entrada no `boundlist` pode especificar os limites inferior e superior dessa dimensão.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="ce3f2-131">O limite inferior é sempre 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="ce3f2-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="ce3f2-132">O limite superior é o valor de índice mais alto possível para essa dimensão, não o comprimento da dimensão (que é o limite superior mais um).</span><span class="sxs-lookup"><span data-stu-id="ce3f2-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="ce3f2-133">O índice de cada dimensão pode variar de 0 ao seu valor de limite superior.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="ce3f2-134">O número de dimensões em `boundlist` deve corresponder ao número original de dimensões (classificação) da matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="ce3f2-135">**Tipos de dados.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-135">**Data Types.**</span></span> <span data-ttu-id="ce3f2-136">A `ReDim` instrução não pode alterar o tipo de dados de uma variável de matriz ou seus elementos.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="ce3f2-137">**Initialization.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-137">**Initialization.**</span></span> <span data-ttu-id="ce3f2-138">A `ReDim` instrução não pode fornecer novos valores de inicialização para os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="ce3f2-139">**Fique.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-139">**Rank.**</span></span> <span data-ttu-id="ce3f2-140">A `ReDim` instrução não pode alterar a classificação (o número de dimensões) da matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="ce3f2-141">**Redimensionando com Preserve.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="ce3f2-142">Se você usar `Preserve` o, poderá redimensionar apenas a última dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="ce3f2-143">Para todas as outras dimensões, você deve especificar o limite da matriz existente.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="ce3f2-144">Por exemplo, se a matriz tiver apenas uma dimensão, você poderá redimensionar essa dimensão e ainda preservar todo o conteúdo da matriz, pois você está alterando a última e a única dimensão.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="ce3f2-145">No entanto, se sua matriz tiver duas ou mais dimensões, você poderá alterar o tamanho da última dimensão se usar `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="ce3f2-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="ce3f2-146">**Properties.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-146">**Properties.**</span></span> <span data-ttu-id="ce3f2-147">Você pode usar `ReDim` em uma propriedade que contém uma matriz de valores.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="ce3f2-148">Comportamento</span><span class="sxs-lookup"><span data-stu-id="ce3f2-148">Behavior</span></span>  
  
- <span data-ttu-id="ce3f2-149">**Substituição de matriz.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-149">**Array Replacement.**</span></span> <span data-ttu-id="ce3f2-150">`ReDim`Libera a matriz existente e cria uma nova matriz com a mesma classificação.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="ce3f2-151">A nova matriz substitui a matriz liberada na variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="ce3f2-152">**Inicialização sem preservar.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="ce3f2-153">Se você não especificar `Preserve` , `ReDim` Inicializa os elementos da nova matriz usando o valor padrão para seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="ce3f2-154">**Inicialização com Preserve.**</span><span class="sxs-lookup"><span data-stu-id="ce3f2-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="ce3f2-155">Se você especificar `Preserve` , Visual Basic copiará os elementos da matriz existente para a nova matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce3f2-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ce3f2-156">Example</span></span>  
 <span data-ttu-id="ce3f2-157">O exemplo a seguir aumenta o tamanho da última dimensão de uma matriz dinâmica sem perder os dados existentes na matriz e, em seguida, diminui o tamanho com perda de dados parcial.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="ce3f2-158">Por fim, ele diminui o tamanho de volta para seu valor original e reinicializa todos os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="ce3f2-159">A `Dim` instrução cria uma nova matriz com três dimensões.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="ce3f2-160">Cada dimensão é declarada com um limite de 10, portanto, o índice de matriz para cada dimensão pode variar de 0 a 10.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="ce3f2-161">Na discussão a seguir, as três dimensões são referidas como camada, linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="ce3f2-162">O primeiro `ReDim` cria uma nova matriz que substitui a matriz existente na variável `intArray` .</span><span class="sxs-lookup"><span data-stu-id="ce3f2-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="ce3f2-163">`ReDim`Copia todos os elementos da matriz existente para a nova matriz.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="ce3f2-164">Ele também adiciona mais 10 colunas ao final de cada linha em cada camada e inicializa os elementos nessas novas colunas como 0 (o valor padrão de `Integer` , que é o tipo de elemento da matriz).</span><span class="sxs-lookup"><span data-stu-id="ce3f2-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="ce3f2-165">O segundo `ReDim` cria outra nova matriz e copia todos os elementos que se ajustam.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="ce3f2-166">No entanto, cinco colunas são perdidas do final de cada linha em cada camada.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="ce3f2-167">Isso não será um problema se você tiver terminado de usar essas colunas.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="ce3f2-168">Reduzir o tamanho de uma matriz grande pode liberar memória que você não precisa mais.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="ce3f2-169">O terceiro `ReDim` cria outra nova matriz e remove outras cinco colunas do final de cada linha em cada camada.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="ce3f2-170">Desta vez, ele não copia nenhum elemento existente.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="ce3f2-171">Essa instrução reverte a matriz para seu tamanho original.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="ce3f2-172">Como a instrução não inclui o `Preserve` modificador, ele define todos os elementos de matriz para seus valores padrão originais.</span><span class="sxs-lookup"><span data-stu-id="ce3f2-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="ce3f2-173">Para obter exemplos adicionais, consulte [matrizes](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce3f2-173">For additional examples, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce3f2-174">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce3f2-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="ce3f2-175">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="ce3f2-175">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="ce3f2-176">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="ce3f2-176">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="ce3f2-177">Instrução Erase</span><span class="sxs-lookup"><span data-stu-id="ce3f2-177">Erase Statement</span></span>](erase-statement.md)
- [<span data-ttu-id="ce3f2-178">Nada</span><span class="sxs-lookup"><span data-stu-id="ce3f2-178">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="ce3f2-179">Matrizes</span><span class="sxs-lookup"><span data-stu-id="ce3f2-179">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)

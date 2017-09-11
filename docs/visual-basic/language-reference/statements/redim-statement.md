---
title: "Instrução reDim (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ReDim
- vb.Preserve
dev_langs:
- VB
helpviewer_keywords:
- fixed-length strings, declaring
- ReDim statement, syntax
- dynamic arrays, ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations, dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement
- data types [Visual Basic], assigning
- As keyword, in ReDim statement
- To keyword, ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword, ReDim statement
- storage, allocating
- arrays [Visual Basic], and scalars
- declaration statements
- scalar variables
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
caps.latest.revision: 25
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
ms.openlocfilehash: 2bc0d00be69724996113dd0ee5047ab84147865b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="b4e83-102">Instrução ReDim (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e83-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="b4e83-103">Realoca espaço de armazenamento para uma variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4e83-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4e83-104">Syntax</span></span>  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="b4e83-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b4e83-105">Parts</span></span>  
  
|<span data-ttu-id="b4e83-106">Termo</span><span class="sxs-lookup"><span data-stu-id="b4e83-106">Term</span></span>|<span data-ttu-id="b4e83-107">Definição</span><span class="sxs-lookup"><span data-stu-id="b4e83-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="b4e83-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b4e83-108">Optional.</span></span> <span data-ttu-id="b4e83-109">Modificador usado para preservar os dados na matriz existente quando você alterar o tamanho da dimensão somente última.</span><span class="sxs-lookup"><span data-stu-id="b4e83-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="b4e83-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b4e83-110">Required.</span></span> <span data-ttu-id="b4e83-111">Nome da variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-111">Name of the array variable.</span></span> <span data-ttu-id="b4e83-112">Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="b4e83-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="b4e83-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b4e83-113">Required.</span></span> <span data-ttu-id="b4e83-114">Lista de limites de cada dimensão da matriz redefinida.</span><span class="sxs-lookup"><span data-stu-id="b4e83-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4e83-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4e83-115">Remarks</span></span>  
 <span data-ttu-id="b4e83-116">Você pode usar o `ReDim` instrução para alterar o tamanho de uma ou mais dimensões de um array que já foi declarado.</span><span class="sxs-lookup"><span data-stu-id="b4e83-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="b4e83-117">Se você tiver uma matriz grande e você não precisa mais alguns de seus elementos, `ReDim` pode liberar espaço na memória, reduzindo o tamanho da matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="b4e83-118">Por outro lado, se sua matriz precisa de mais elementos, `ReDim` pode adicioná-los.</span><span class="sxs-lookup"><span data-stu-id="b4e83-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="b4e83-119">O `ReDim` instrução é destinada apenas para matrizes.</span><span class="sxs-lookup"><span data-stu-id="b4e83-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="b4e83-120">Não é válido em estruturas, coleções ou escalares (variáveis que contêm apenas um único valor).</span><span class="sxs-lookup"><span data-stu-id="b4e83-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="b4e83-121">Observe que, se você declarar uma variável para ser do tipo `Array`, o `ReDim` instrução não tem informações de tipo suficientes para criar a nova matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="b4e83-122">Você pode usar `ReDim` somente no nível de procedimento.</span><span class="sxs-lookup"><span data-stu-id="b4e83-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="b4e83-123">Portanto, o contexto da declaração da variável deve ser um procedimento; ele não pode ser um arquivo de origem, um namespace, uma interface, uma classe, uma estrutura, um módulo ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="b4e83-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="b4e83-124">Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b4e83-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b4e83-125">Regras</span><span class="sxs-lookup"><span data-stu-id="b4e83-125">Rules</span></span>  
  
-   <span data-ttu-id="b4e83-126">**Diversas variáveis.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-126">**Multiple Variables.**</span></span> <span data-ttu-id="b4e83-127">Você pode redimensionar diversas variáveis de matriz na mesma instrução de declaração e especificar o `name` e `boundlist` partes para cada variável.</span><span class="sxs-lookup"><span data-stu-id="b4e83-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="b4e83-128">Diversas variáveis são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="b4e83-128">Multiple variables are separated by commas.</span></span>  
  
-   <span data-ttu-id="b4e83-129">**Limites da matriz.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-129">**Array Bounds.**</span></span> <span data-ttu-id="b4e83-130">Cada entrada na `boundlist` pode especificar os limites inferior e superior da dimensão.</span><span class="sxs-lookup"><span data-stu-id="b4e83-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="b4e83-131">O limite inferior é sempre 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="b4e83-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="b4e83-132">O limite superior é o maior valor possível índice da dimensão, não o comprimento da dimensão (que é o limite superior mais um).</span><span class="sxs-lookup"><span data-stu-id="b4e83-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="b4e83-133">O índice para cada dimensão pode variar entre 0 e o valor do limite superior.</span><span class="sxs-lookup"><span data-stu-id="b4e83-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="b4e83-134">O número de dimensões no `boundlist` deve corresponder ao número original de dimensões (classificação) da matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
-   <span data-ttu-id="b4e83-135">**Tipos de dados.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-135">**Data Types.**</span></span> <span data-ttu-id="b4e83-136">O `ReDim` instrução não é possível alterar o tipo de dados de uma variável de matriz ou seus elementos.</span><span class="sxs-lookup"><span data-stu-id="b4e83-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
-   <span data-ttu-id="b4e83-137">**Inicialização.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-137">**Initialization.**</span></span> <span data-ttu-id="b4e83-138">O `ReDim` instrução não pode fornecer novos valores de inicialização para os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
-   <span data-ttu-id="b4e83-139">**Classificação.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-139">**Rank.**</span></span> <span data-ttu-id="b4e83-140">O `ReDim` instrução não é possível alterar a classificação (o número de dimensões) da matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
-   <span data-ttu-id="b4e83-141">**Redimensionando com preservar.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="b4e83-142">Se você usar `Preserve`, você pode redimensionar a última dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="b4e83-143">Para cada dimensão, você deve especificar o limite da matriz existente.</span><span class="sxs-lookup"><span data-stu-id="b4e83-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="b4e83-144">Por exemplo, se a matriz tem apenas uma dimensão, redimensionar dimensão e ainda preservar todo o conteúdo da matriz, porque você está alterando a última e somente a dimensão.</span><span class="sxs-lookup"><span data-stu-id="b4e83-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="b4e83-145">No entanto, se a matriz tem dois ou mais dimensões, você pode alterar o tamanho da dimensão somente última de se você usar `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="b4e83-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
-   <span data-ttu-id="b4e83-146">**Propriedades.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-146">**Properties.**</span></span> <span data-ttu-id="b4e83-147">Você pode usar `ReDim` em uma propriedade que contém uma matriz de valores.</span><span class="sxs-lookup"><span data-stu-id="b4e83-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="b4e83-148">Comportamento</span><span class="sxs-lookup"><span data-stu-id="b4e83-148">Behavior</span></span>  
  
-   <span data-ttu-id="b4e83-149">**Substituição de matriz.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-149">**Array Replacement.**</span></span> <span data-ttu-id="b4e83-150">`ReDim`libera a matriz existente e cria uma nova matriz com a mesma classificação.</span><span class="sxs-lookup"><span data-stu-id="b4e83-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="b4e83-151">Nova matriz substitui a matriz lançada na variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-151">The new array replaces the released array in the array variable.</span></span>  
  
-   <span data-ttu-id="b4e83-152">**Inicialização sem preservar.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="b4e83-153">Se você não especificar `Preserve`, `ReDim` inicializa os elementos da nova matriz usando o valor padrão para seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b4e83-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
-   <span data-ttu-id="b4e83-154">**Inicialização com preservar.**</span><span class="sxs-lookup"><span data-stu-id="b4e83-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="b4e83-155">Se você especificar `Preserve`, Visual Basic copia os elementos da matriz existente para a nova matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4e83-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4e83-156">Example</span></span>  
 <span data-ttu-id="b4e83-157">O exemplo a seguir aumenta o tamanho da última dimensão de uma matriz dinâmica sem perder os dados existentes na matriz e, em seguida, diminui o tamanho com perda de dados parcial.</span><span class="sxs-lookup"><span data-stu-id="b4e83-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="b4e83-158">Por fim, ele diminui o tamanho de volta para seu valor original e reinicializa todos os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 <span data-ttu-id="b4e83-159">[!code-vb[VbVbalrStatements&#52;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b4e83-159">[!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="b4e83-160">O `Dim` instrução cria uma nova matriz com três dimensões.</span><span class="sxs-lookup"><span data-stu-id="b4e83-160">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="b4e83-161">Cada dimensão é declarado com um limite de 10, para que o índice de matriz para cada dimensão pode variar de 0 a 10.</span><span class="sxs-lookup"><span data-stu-id="b4e83-161">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="b4e83-162">Na discussão a seguir, três dimensões são denominadas camada, linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="b4e83-162">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="b4e83-163">A primeira `ReDim` cria uma nova matriz que substitui a matriz existente na variável `intArray`.</span><span class="sxs-lookup"><span data-stu-id="b4e83-163">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="b4e83-164">`ReDim`copia todos os elementos da matriz existente na nova matriz.</span><span class="sxs-lookup"><span data-stu-id="b4e83-164">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="b4e83-165">Também adiciona 10 mais colunas ao final de cada linha em cada camada e inicializa os elementos nessas novas colunas como 0 (o valor padrão de `Integer`, que é o tipo de elemento da matriz).</span><span class="sxs-lookup"><span data-stu-id="b4e83-165">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="b4e83-166">O segundo `ReDim` cria outra nova matriz e copia todos os elementos que se encaixam.</span><span class="sxs-lookup"><span data-stu-id="b4e83-166">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="b4e83-167">No entanto, cinco colunas forem perdidas no final de cada linha em cada camada.</span><span class="sxs-lookup"><span data-stu-id="b4e83-167">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="b4e83-168">Isso não é um problema se você terminar de usar essas colunas.</span><span class="sxs-lookup"><span data-stu-id="b4e83-168">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="b4e83-169">Reduzindo o tamanho de uma matriz grande pode liberar memória que não é mais necessário.</span><span class="sxs-lookup"><span data-stu-id="b4e83-169">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="b4e83-170">A terceira `ReDim` cria outro novo array e remove outro cinco colunas do final de cada linha em cada camada.</span><span class="sxs-lookup"><span data-stu-id="b4e83-170">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="b4e83-171">Neste momento ele não copia os elementos existentes.</span><span class="sxs-lookup"><span data-stu-id="b4e83-171">This time it does not copy any existing elements.</span></span> <span data-ttu-id="b4e83-172">Essa instrução reverte a matriz ao seu tamanho original.</span><span class="sxs-lookup"><span data-stu-id="b4e83-172">This statement reverts the array to its original size.</span></span> <span data-ttu-id="b4e83-173">Como a instrução não inclui o `Preserve` modificador, ele define todos os elementos da matriz para seus valores padrão originais.</span><span class="sxs-lookup"><span data-stu-id="b4e83-173">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="b4e83-174">Para obter exemplos adicionais, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4e83-174">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e83-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4e83-175">See Also</span></span>  
 <span data-ttu-id="b4e83-176"><xref:System.IndexOutOfRangeException></xref:System.IndexOutOfRangeException></span><span class="sxs-lookup"><span data-stu-id="b4e83-176"><xref:System.IndexOutOfRangeException></span></span>   
<span data-ttu-id="b4e83-177"> [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b4e83-177"> [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="b4e83-178"> [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b4e83-178"> [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="b4e83-179"> [Instrução Erase](../../../visual-basic/language-reference/statements/erase-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b4e83-179"> [Erase Statement](../../../visual-basic/language-reference/statements/erase-statement.md) </span></span>  
<span data-ttu-id="b4e83-180"> [Nada](../../../visual-basic/language-reference/nothing.md) </span><span class="sxs-lookup"><span data-stu-id="b4e83-180"> [Nothing](../../../visual-basic/language-reference/nothing.md) </span></span>  
<span data-ttu-id="b4e83-181"> [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)</span><span class="sxs-lookup"><span data-stu-id="b4e83-181"> [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md)</span></span>

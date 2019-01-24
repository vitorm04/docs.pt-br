---
title: Conversões implícitas e explícitas (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 8e0ab9e3818ff4210dc6e349104ea0dcc4c8bfa7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596001"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="31e4d-102">Conversões implícitas e explícitas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31e4d-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="31e4d-103">Uma *conversão implícita* não requer nenhuma sintaxe especial no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="31e4d-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="31e4d-104">No exemplo a seguir, o Visual Basic converte implicitamente o valor de `k` para um valor de ponto flutuante de precisão simples antes de atribuí-lo para `q`.</span><span class="sxs-lookup"><span data-stu-id="31e4d-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="31e4d-105">Uma *conversão explícita* usa uma palavra-chave de conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="31e4d-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="31e4d-106">Visual Basic fornece várias palavras-chave tais, que força uma expressão entre parênteses para o tipo de dados desejado.</span><span class="sxs-lookup"><span data-stu-id="31e4d-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="31e4d-107">Essas palavras-chave atuam como funções, mas o compilador gera o código embutido, portanto, a execução é ligeiramente mais rápida do que com uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="31e4d-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="31e4d-108">Na seguinte extensão do exemplo anterior, o `CInt` palavra-chave converte o valor de `q` volta para um número inteiro antes de atribuí-lo para `k`.</span><span class="sxs-lookup"><span data-stu-id="31e4d-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="31e4d-109">Palavras-chave de conversão</span><span class="sxs-lookup"><span data-stu-id="31e4d-109">Conversion Keywords</span></span>  
 <span data-ttu-id="31e4d-110">A tabela a seguir mostra as palavras-chave de conversão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="31e4d-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="31e4d-111">Palavra-chave de conversão de tipo</span><span class="sxs-lookup"><span data-stu-id="31e4d-111">Type conversion keyword</span></span>|<span data-ttu-id="31e4d-112">Converte uma expressão em tipo de dados</span><span class="sxs-lookup"><span data-stu-id="31e4d-112">Converts an expression to data type</span></span>|<span data-ttu-id="31e4d-113">Tipos de dados permitido de expressão a ser convertido</span><span class="sxs-lookup"><span data-stu-id="31e4d-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="31e4d-114">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="31e4d-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="31e4d-115">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="31e4d-116">Tipo de Dados Byte</span><span class="sxs-lookup"><span data-stu-id="31e4d-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="31e4d-117">Qualquer tipo numérico (incluindo `SByte` e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="31e4d-118">Tipo de Dados de Caractere</span><span class="sxs-lookup"><span data-stu-id="31e4d-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="31e4d-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="31e4d-120">Tipo de Dados de Data</span><span class="sxs-lookup"><span data-stu-id="31e4d-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="31e4d-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="31e4d-122">Tipo de Dados Duplo</span><span class="sxs-lookup"><span data-stu-id="31e4d-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="31e4d-123">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="31e4d-124">Tipo de Dados Decimal</span><span class="sxs-lookup"><span data-stu-id="31e4d-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="31e4d-125">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="31e4d-126">Tipo de Dados Integer</span><span class="sxs-lookup"><span data-stu-id="31e4d-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="31e4d-127">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="31e4d-128">Tipo de Dados Long</span><span class="sxs-lookup"><span data-stu-id="31e4d-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="31e4d-129">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="31e4d-130">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="31e4d-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="31e4d-131">Qualquer tipo</span><span class="sxs-lookup"><span data-stu-id="31e4d-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="31e4d-132">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="31e4d-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="31e4d-133">Qualquer tipo numérico (incluindo `Byte` e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="31e4d-134">Tipo de Dados Short</span><span class="sxs-lookup"><span data-stu-id="31e4d-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="31e4d-135">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="31e4d-136">Tipo de Dados Simples</span><span class="sxs-lookup"><span data-stu-id="31e4d-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="31e4d-137">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="31e4d-138">Tipo de Dados String</span><span class="sxs-lookup"><span data-stu-id="31e4d-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="31e4d-139">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `Char`, `Char` matriz, `Date`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="31e4d-140">Tipo especificado após a vírgula (`,`)</span><span class="sxs-lookup"><span data-stu-id="31e4d-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="31e4d-141">Ao converter para um *tipo de dados elementar* (incluindo uma matriz de um tipo elementar), os mesmos tipos como permitido para a palavra-chave de conversão correspondente</span><span class="sxs-lookup"><span data-stu-id="31e4d-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="31e4d-142">Ao converter para um *tipo de dados composto*, as interfaces que ele implementa e as classes da qual ela herda</span><span class="sxs-lookup"><span data-stu-id="31e4d-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="31e4d-143">Ao converter em uma classe ou estrutura na qual você tenha sobrecarregado `CType`, classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="31e4d-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="31e4d-144">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="31e4d-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="31e4d-145">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="31e4d-146">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="31e4d-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="31e4d-147">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="31e4d-148">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="31e4d-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="31e4d-149">Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="31e4d-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="31e4d-150">A função CType</span><span class="sxs-lookup"><span data-stu-id="31e4d-150">The CType Function</span></span>  
 <span data-ttu-id="31e4d-151">O [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) opera em dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="31e4d-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="31e4d-152">A primeira é a expressão a ser convertida e a segunda é a classe de objeto ou tipo de dados do destino.</span><span class="sxs-lookup"><span data-stu-id="31e4d-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="31e4d-153">Observe que o primeiro argumento deve ser uma expressão, não é um tipo.</span><span class="sxs-lookup"><span data-stu-id="31e4d-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="31e4d-154">`CType` é um *função embutida*, o que significa que o código compilado faz a conversão, muitas vezes sem gerar uma função chamada.</span><span class="sxs-lookup"><span data-stu-id="31e4d-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="31e4d-155">Isso melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="31e4d-155">This improves performance.</span></span>  
  
 <span data-ttu-id="31e4d-156">Para obter uma comparação `CType` com o outro tipo conversão palavras-chave, consulte [operador DirectCast](../../../../visual-basic/language-reference/operators/directcast-operator.md) e [operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="31e4d-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="31e4d-157">Tipos elementares</span><span class="sxs-lookup"><span data-stu-id="31e4d-157">Elementary Types</span></span>  
 <span data-ttu-id="31e4d-158">O exemplo a seguir demonstra o uso de `CType`.</span><span class="sxs-lookup"><span data-stu-id="31e4d-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="31e4d-159">Tipos compostos</span><span class="sxs-lookup"><span data-stu-id="31e4d-159">Composite Types</span></span>  
 <span data-ttu-id="31e4d-160">Você pode usar `CType` para converter valores em tipos de dados compostos, bem como para tipos elementares.</span><span class="sxs-lookup"><span data-stu-id="31e4d-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="31e4d-161">Você também pode usá-lo para forçar uma classe de objeto para o tipo de uma de suas interfaces, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="31e4d-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="31e4d-162">Tipos de matriz</span><span class="sxs-lookup"><span data-stu-id="31e4d-162">Array Types</span></span>  
 <span data-ttu-id="31e4d-163">`CType` também pode converter tipos de dados de matriz, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="31e4d-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 <span data-ttu-id="31e4d-164">Para obter mais informações e um exemplo, consulte [conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="31e4d-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="31e4d-165">Tipos definindo CType</span><span class="sxs-lookup"><span data-stu-id="31e4d-165">Types Defining CType</span></span>  
 <span data-ttu-id="31e4d-166">Você pode definir `CType` em uma classe ou estrutura que você definiu.</span><span class="sxs-lookup"><span data-stu-id="31e4d-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="31e4d-167">Isso permite que você converter valores de e para o tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="31e4d-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="31e4d-168">Para obter mais informações e um exemplo, consulte [como: Definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="31e4d-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31e4d-169">Valores usados com uma palavra-chave de conversão devem ser válidos para o tipo de dados de destino, ou ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="31e4d-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="31e4d-170">Por exemplo, se você tentar converter um `Long` para um `Integer`, o valor da `Long` deve estar dentro do intervalo válido para o `Integer` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="31e4d-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="31e4d-171">Especificando `CType` para converter de um tipo de classe para outra falha no tempo de execução se o tipo de origem não é derivado do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="31e4d-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="31e4d-172">Uma falha gera um <xref:System.InvalidCastException> exceção.</span><span class="sxs-lookup"><span data-stu-id="31e4d-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="31e4d-173">No entanto, se um dos tipos é uma estrutura ou classe definida por você, e se você tiver definido `CType` sobre essa classe ou estrutura, uma conversão pode ser bem-sucedida se ele satisfaz os requisitos de seu `CType`.</span><span class="sxs-lookup"><span data-stu-id="31e4d-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="31e4d-174">Confira [Como Definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="31e4d-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="31e4d-175">Executar uma conversão explícita é também conhecido como *conversão* uma expressão para uma classe de objeto ou tipo de dados especificados.</span><span class="sxs-lookup"><span data-stu-id="31e4d-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e4d-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31e4d-176">See also</span></span>
- [<span data-ttu-id="31e4d-177">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31e4d-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="31e4d-178">Conversões entre Cadeias de Caracteres e Outros Tipos</span><span class="sxs-lookup"><span data-stu-id="31e4d-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="31e4d-179">Como: Converter um objeto em outro tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31e4d-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="31e4d-180">Estruturas</span><span class="sxs-lookup"><span data-stu-id="31e4d-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="31e4d-181">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="31e4d-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="31e4d-182">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="31e4d-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="31e4d-183">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="31e4d-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)

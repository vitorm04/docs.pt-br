---
title: "Conversões (Visual Basic) entre | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- widening conversions
- narrowing conversions
- conversions, type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions, exceptions during conversion
- type conversion, exceptions during conversion
- conversions, data type
- conversions, narrowing
- type conversion, narrowing
- data type conversion, widening
- data type conversion, narrowing
- changing data types
- type conversion, widening
- data type conversion, exceptions during conversion
- conversions, widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
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
ms.openlocfilehash: c00db1c631e1cc71df856407e8646532a73c6d44
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="widening-and-narrowing-conversions-visual-basic"></a><span data-ttu-id="fe81f-102">Conversões de Widening e Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe81f-102">Widening and Narrowing Conversions (Visual Basic)</span></span>
<span data-ttu-id="fe81f-103">Uma consideração importante com uma conversão de tipos é se o resultado da conversão está dentro do intervalo do tipo de dados de destino.</span><span class="sxs-lookup"><span data-stu-id="fe81f-103">An important consideration with a type conversion is whether the result of the conversion is within the range of the destination data type.</span></span>  
  
 <span data-ttu-id="fe81f-104">A *conversões ampliadoras* muda o valor para um tipo de dados que pode permitir que qualquer valor possível dos dados originais.</span><span class="sxs-lookup"><span data-stu-id="fe81f-104">A *widening conversion* changes a value to a data type that can allow for any possible value of the original data.</span></span>  <span data-ttu-id="fe81f-105">Conversões ampliadoras preservar o valor de origem, mas podem alterar sua representação.</span><span class="sxs-lookup"><span data-stu-id="fe81f-105">Widening conversions preserve the source value but can change its representation.</span></span> <span data-ttu-id="fe81f-106">Isso ocorre se você converter de um tipo integral para `Decimal`, ou de `Char` para `String`.</span><span class="sxs-lookup"><span data-stu-id="fe81f-106">This occurs if you convert from an integral type to `Decimal`, or from `Char` to `String`.</span></span>  
  
 <span data-ttu-id="fe81f-107">A *conversão de redução* muda o valor para um tipo de dados que pode não ser capaz de armazenar alguns dos possíveis valores.</span><span class="sxs-lookup"><span data-stu-id="fe81f-107">A *narrowing conversion* changes a value to a data type that might not be able to hold some of the possible values.</span></span> <span data-ttu-id="fe81f-108">Por exemplo, um valor fracionário é arredondado quando ele é convertido em um tipo integral e um tipo numérico sendo convertido em `Boolean` é reduzido para `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="fe81f-108">For example, a fractional value is rounded when it is converted to an integral type, and a numeric type being converted to `Boolean` is reduced to either `True` or `False`.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="fe81f-109">Conversões de expansão</span><span class="sxs-lookup"><span data-stu-id="fe81f-109">Widening Conversions</span></span>  
 <span data-ttu-id="fe81f-110">A tabela a seguir mostra as conversões ampliadoras padrão.</span><span class="sxs-lookup"><span data-stu-id="fe81f-110">The following table shows the standard widening conversions.</span></span>  
  
|<span data-ttu-id="fe81f-111">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="fe81f-111">Data type</span></span>|<span data-ttu-id="fe81f-112">Amplia a tipos de dados <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="fe81f-112">Widens to data types <sup>1</sup></span></span>|  
|---|---|  
|[<span data-ttu-id="fe81f-113">SByte</span><span class="sxs-lookup"><span data-stu-id="fe81f-113">SByte</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="fe81f-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="fe81f-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="fe81f-115">Byte</span><span class="sxs-lookup"><span data-stu-id="fe81f-115">Byte</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="fe81f-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="fe81f-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="fe81f-117">Curto</span><span class="sxs-lookup"><span data-stu-id="fe81f-117">Short</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="fe81f-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="fe81f-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="fe81f-119">UShort</span><span class="sxs-lookup"><span data-stu-id="fe81f-119">UShort</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="fe81f-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="fe81f-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="fe81f-121">Número inteiro</span><span class="sxs-lookup"><span data-stu-id="fe81f-121">Integer</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="fe81f-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="fe81f-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="fe81f-123">UInteger</span><span class="sxs-lookup"><span data-stu-id="fe81f-123">UInteger</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="fe81f-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="fe81f-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="fe81f-125">Longas</span><span class="sxs-lookup"><span data-stu-id="fe81f-125">Long</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="fe81f-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="fe81f-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="fe81f-127">ULong</span><span class="sxs-lookup"><span data-stu-id="fe81f-127">ULong</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="fe81f-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="fe81f-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="fe81f-129">Decimal</span><span class="sxs-lookup"><span data-stu-id="fe81f-129">Decimal</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="fe81f-130">`Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="fe81f-130">`Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="fe81f-131">Simples</span><span class="sxs-lookup"><span data-stu-id="fe81f-131">Single</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="fe81f-132">`Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="fe81f-132">`Single`, `Double`</span></span>|  
|[<span data-ttu-id="fe81f-133">Duplo</span><span class="sxs-lookup"><span data-stu-id="fe81f-133">Double</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|<span data-ttu-id="fe81f-134">Qualquer tipo enumerado ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))</span><span class="sxs-lookup"><span data-stu-id="fe81f-134">Any enumerated type ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))</span></span>|<span data-ttu-id="fe81f-135">Seu tipo integral subjacente e qualquer tipo ao qual o tipo subjacente amplia.</span><span class="sxs-lookup"><span data-stu-id="fe81f-135">Its underlying integral type and any type to which the underlying type widens.</span></span>|  
|[<span data-ttu-id="fe81f-136">Char</span><span class="sxs-lookup"><span data-stu-id="fe81f-136">Char</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="fe81f-137">`Char`, `String`</span><span class="sxs-lookup"><span data-stu-id="fe81f-137">`Char`, `String`</span></span>|  
|<span data-ttu-id="fe81f-138">Matriz `Char`</span><span class="sxs-lookup"><span data-stu-id="fe81f-138">`Char` array</span></span>|<span data-ttu-id="fe81f-139">`Char`matriz,`String`</span><span class="sxs-lookup"><span data-stu-id="fe81f-139">`Char` array, `String`</span></span>|  
|<span data-ttu-id="fe81f-140">Qualquer tipo</span><span class="sxs-lookup"><span data-stu-id="fe81f-140">Any type</span></span>|[<span data-ttu-id="fe81f-141">Objeto</span><span class="sxs-lookup"><span data-stu-id="fe81f-141">Object</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|<span data-ttu-id="fe81f-142">Qualquer tipo derivado</span><span class="sxs-lookup"><span data-stu-id="fe81f-142">Any derived type</span></span>|<span data-ttu-id="fe81f-143">Qualquer tipo do qual ele é derivado de base <sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="fe81f-143">Any base type from which it is derived <sup>3</sup>.</span></span>|  
|<span data-ttu-id="fe81f-144">Qualquer tipo</span><span class="sxs-lookup"><span data-stu-id="fe81f-144">Any type</span></span>|<span data-ttu-id="fe81f-145">Qualquer interface que ele implementa.</span><span class="sxs-lookup"><span data-stu-id="fe81f-145">Any interface it implements.</span></span>|  
|[<span data-ttu-id="fe81f-146">Nothing</span><span class="sxs-lookup"><span data-stu-id="fe81f-146">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)|<span data-ttu-id="fe81f-147">Qualquer tipo de dados ou tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="fe81f-147">Any data type or object type.</span></span>|  
  
 <span data-ttu-id="fe81f-148"><sup>1</sup> por definição, cada tipo de dados amplia a mesmo.</span><span class="sxs-lookup"><span data-stu-id="fe81f-148"><sup>1</sup> By definition, every data type widens to itself.</span></span>  
  
 <span data-ttu-id="fe81f-149"><sup>2</sup> conversões de `Integer`, `UInteger`, `Long`, `ULong`, ou `Decimal` para `Single` ou `Double` pode resultar em perda de precisão, mas nunca na perda de magnitude.</span><span class="sxs-lookup"><span data-stu-id="fe81f-149"><sup>2</sup> Conversions from `Integer`, `UInteger`, `Long`, `ULong`, or `Decimal` to `Single` or `Double` might result in loss of precision, but never in loss of magnitude.</span></span> <span data-ttu-id="fe81f-150">Nesse sentido, elas não provocam perda de informações.</span><span class="sxs-lookup"><span data-stu-id="fe81f-150">In this sense they do not incur information loss.</span></span>  
  
 <span data-ttu-id="fe81f-151"><sup>3</sup> pode parecer estranho que uma conversão de um tipo derivado em um dos seus tipos base é ampliadora.</span><span class="sxs-lookup"><span data-stu-id="fe81f-151"><sup>3</sup> It might seem surprising that a conversion from a derived type to one of its base types is widening.</span></span> <span data-ttu-id="fe81f-152">A justificativa é que o tipo derivado contém todos os membros do tipo base, portanto, ele qualifica como uma instância do tipo base.</span><span class="sxs-lookup"><span data-stu-id="fe81f-152">The justification is that the derived type contains all the members of the base type, so it qualifies as an instance of the base type.</span></span> <span data-ttu-id="fe81f-153">Na direção oposta, o tipo base não contém quaisquer novos membros definidos pelo tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="fe81f-153">In the opposite direction, the base type does not contain any new members defined by the derived type.</span></span>  
  
 <span data-ttu-id="fe81f-154">Conversões de ampliação sempre são bem-sucedidas em tempo de execução e nunca provocam perda de dados.</span><span class="sxs-lookup"><span data-stu-id="fe81f-154">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="fe81f-155">Você pode sempre executá-las implicitamente, se o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) define o tipo de verificação alternar para `On` ou `Off`.</span><span class="sxs-lookup"><span data-stu-id="fe81f-155">You can always perform them implicitly, whether the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `On` or to `Off`.</span></span>  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="fe81f-156">Conversões de redução</span><span class="sxs-lookup"><span data-stu-id="fe81f-156">Narrowing Conversions</span></span>  
 <span data-ttu-id="fe81f-157">As conversões de estreitamento padrão incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fe81f-157">The standard narrowing conversions include the following:</span></span>  
  
-   <span data-ttu-id="fe81f-158">As direções inversas das conversões ampliadoras na anterior tabela (exceto pelo fato de cada tipo amplia a mesmo)</span><span class="sxs-lookup"><span data-stu-id="fe81f-158">The reverse directions of the widening conversions in the preceding table (except that every type widens to itself)</span></span>  
  
-   <span data-ttu-id="fe81f-159">Conversões em ambas as direções entre [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) e qualquer tipo numérico</span><span class="sxs-lookup"><span data-stu-id="fe81f-159">Conversions in either direction between [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) and any numeric type</span></span>  
  
-   <span data-ttu-id="fe81f-160">Conversões de qualquer tipo numérico para qualquer tipo enumerado (`Enum`)</span><span class="sxs-lookup"><span data-stu-id="fe81f-160">Conversions from any numeric type to any enumerated type (`Enum`)</span></span>  
  
-   <span data-ttu-id="fe81f-161">Conversões em ambas as direções entre [sequência](../../../../visual-basic/language-reference/data-types/string-data-type.md) e qualquer tipo numérico, `Boolean`, ou [data](../../../../visual-basic/language-reference/data-types/date-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="fe81f-161">Conversions in either direction between [String](../../../../visual-basic/language-reference/data-types/string-data-type.md) and any numeric type, `Boolean`, or [Date](../../../../visual-basic/language-reference/data-types/date-data-type.md)</span></span>  
  
-   <span data-ttu-id="fe81f-162">Conversões de um tipo de dados ou objeto de tipo para um tipo derivado dele</span><span class="sxs-lookup"><span data-stu-id="fe81f-162">Conversions from a data type or object type to a type derived from it</span></span>  
  
 <span data-ttu-id="fe81f-163">Conversões de estreitamento nem sempre bem-sucedidas em tempo de execução e podem falhar ou provoca perda de dados.</span><span class="sxs-lookup"><span data-stu-id="fe81f-163">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="fe81f-164">Ocorrerá um erro se o tipo de dados de destino não pode receber o valor que está sendo convertido.</span><span class="sxs-lookup"><span data-stu-id="fe81f-164">An error occurs if the destination data type cannot receive the value being converted.</span></span> <span data-ttu-id="fe81f-165">Por exemplo, uma conversão numérica pode resultar em um estouro.</span><span class="sxs-lookup"><span data-stu-id="fe81f-165">For example, a numeric conversion can result in an overflow.</span></span> <span data-ttu-id="fe81f-166">O compilador não permite executar conversões de estreitamento implicitamente, a menos que o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) define o tipo de verificação alternar para `Off`.</span><span class="sxs-lookup"><span data-stu-id="fe81f-166">The compiler does not allow you to perform narrowing conversions implicitly unless the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `Off`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe81f-167">O erro de conversão de estreitamento será suprimido para conversões de elementos em um `For Each…Next` coleção para a variável de controle de loop.</span><span class="sxs-lookup"><span data-stu-id="fe81f-167">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="fe81f-168">Para obter mais informações e exemplos, consulte a seção "Conversões de estreitamento" [para cada uma... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fe81f-168">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="when-to-use-narrowing-conversions"></a><span data-ttu-id="fe81f-169">Quando usar conversões de estreitamento</span><span class="sxs-lookup"><span data-stu-id="fe81f-169">When to Use Narrowing Conversions</span></span>  
 <span data-ttu-id="fe81f-170">Use uma conversão de restrição quando você souber que o valor de origem pode ser convertido no tipo de dados de destino sem erro ou perda de dados.</span><span class="sxs-lookup"><span data-stu-id="fe81f-170">You use a narrowing conversion when you know the source value can be converted to the destination data type without error or data loss.</span></span> <span data-ttu-id="fe81f-171">Por exemplo, se você tiver um `String` que você sabe que contém "Verdadeiro" ou "False", você pode usar o `CBool` palavra-chave para convertê-lo para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="fe81f-171">For example, if you have a `String` that you know contains either "True" or "False," you can use the `CBool` keyword to convert it to `Boolean`.</span></span>  
  
## <a name="exceptions-during-conversion"></a><span data-ttu-id="fe81f-172">Exceções durante conversão</span><span class="sxs-lookup"><span data-stu-id="fe81f-172">Exceptions During Conversion</span></span>  
 <span data-ttu-id="fe81f-173">Como conversões ampliadoras sempre são bem-sucedida, elas não lançam exceções.</span><span class="sxs-lookup"><span data-stu-id="fe81f-173">Because widening conversions always succeed, they do not throw exceptions.</span></span> <span data-ttu-id="fe81f-174">Conversões de restrição, quando elas falham, mais comumente lançam as seguintes exceções:</span><span class="sxs-lookup"><span data-stu-id="fe81f-174">Narrowing conversions, when they fail, most commonly throw the following exceptions:</span></span>  
  
-   <span data-ttu-id="fe81f-175"><xref:System.InvalidCastException>— Se nenhuma conversão for definida entre os dois tipos</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="fe81f-175"><xref:System.InvalidCastException> — if no conversion is defined between the two types</span></span>  
  
-   <span data-ttu-id="fe81f-176"><xref:System.OverflowException>— (tipos integral somente) se o valor convertido é muito grande para o tipo de destino</xref:System.OverflowException></span><span class="sxs-lookup"><span data-stu-id="fe81f-176"><xref:System.OverflowException> — (integral types only) if the converted value is too large for the target type</span></span>  
  
 <span data-ttu-id="fe81f-177">Se uma classe ou estrutura define um [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para servir como um operador de conversão entre classe ou estrutura, que `CType` pode acionar qualquer exceção que achar apropriada.</span><span class="sxs-lookup"><span data-stu-id="fe81f-177">If a class or structure defines a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to serve as a conversion operator to or from that class or structure, that `CType` can throw any exception it deems appropriate.</span></span> <span data-ttu-id="fe81f-178">Além disso, que `CType` pode chamar [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] funções ou [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] métodos, que por sua vez, podem acionar uma variedade de exceções.</span><span class="sxs-lookup"><span data-stu-id="fe81f-178">In addition, that `CType` might call [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] functions or [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] methods, which in turn could throw a variety of exceptions.</span></span>  
  
## <a name="changes-during-reference-type-conversions"></a><span data-ttu-id="fe81f-179">Alterações durante conversões de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="fe81f-179">Changes During Reference Type Conversions</span></span>  
 <span data-ttu-id="fe81f-180">Uma conversão de um *tipo de referência* copia apenas o ponteiro ao valor.</span><span class="sxs-lookup"><span data-stu-id="fe81f-180">A conversion from a *reference type* copies only the pointer to the value.</span></span> <span data-ttu-id="fe81f-181">O valor em si não é copiado nem alterado de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="fe81f-181">The value itself is neither copied nor changed in any way.</span></span> <span data-ttu-id="fe81f-182">A única coisa que pode mudar é o tipo de dados da variável mantendo o ponteiro.</span><span class="sxs-lookup"><span data-stu-id="fe81f-182">The only thing that can change is the data type of the variable holding the pointer.</span></span> <span data-ttu-id="fe81f-183">No exemplo a seguir, o tipo de dados é convertido da classe derivada para sua classe base, mas o objeto que ambas as variáveis apontam está inalterado.</span><span class="sxs-lookup"><span data-stu-id="fe81f-183">In the following example, the data type is converted from the derived class to its base class, but the object that both variables now point to is unchanged.</span></span>  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe81f-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe81f-184">See Also</span></span>  
 <span data-ttu-id="fe81f-185">[Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="fe81f-185">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="fe81f-186"> [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="fe81f-186"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="fe81f-187"> [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="fe81f-187"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="fe81f-188"> [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md) </span><span class="sxs-lookup"><span data-stu-id="fe81f-188"> [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md) </span></span>  
<span data-ttu-id="fe81f-189"> [Como: converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span><span class="sxs-lookup"><span data-stu-id="fe81f-189"> [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span></span>  
<span data-ttu-id="fe81f-190"> [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="fe81f-190"> [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span></span>  
<span data-ttu-id="fe81f-191"> [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="fe81f-191"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="fe81f-192"> [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)</span><span class="sxs-lookup"><span data-stu-id="fe81f-192"> [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)</span></span>

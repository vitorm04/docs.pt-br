---
title: Sobrecargas de operador
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400564"
---
# <a name="operator-overloads"></a><span data-ttu-id="2c4a1-102">Sobrecargas de operador</span><span class="sxs-lookup"><span data-stu-id="2c4a1-102">Operator Overloads</span></span>
<span data-ttu-id="2c4a1-103">As sobrecargas dos operadores permitem que os tipos de estruturas apareçam como se fossem primitivos de linguagem embutidos.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="2c4a1-104">Embora permitido e útil em algumas situações, as sobrecargas do operador devem ser usadas com cautela.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="2c4a1-105">Há muitos casos em que a sobrecarga dos operadores foi abusada, como quando os designers de estruturas começaram a usar operadores para operações que deveriam ser métodos simples.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="2c4a1-106">As seguintes diretrizes devem ajudá-lo a decidir quando e como usar a sobrecarga do operador.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="2c4a1-107">❌EVITE definir sobrecargas de operadores, exceto em tipos que devem parecer tipos primitivos (embutidos).</span><span class="sxs-lookup"><span data-stu-id="2c4a1-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="2c4a1-108">✔️ CONSIDEREm definir sobrecargas de operadores em um tipo que deve parecer um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="2c4a1-109">Por <xref:System.String?displayProperty=nameWithType> exemplo, `operator==` `operator!=` tem e definiu.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="2c4a1-110">✔️ DO definem sobrecargas de operadores em <xref:System.Decimal?displayProperty=nameWithType>estruturas que representam números (como ).</span><span class="sxs-lookup"><span data-stu-id="2c4a1-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="2c4a1-111">❌NÃO seja fofo ao definir sobrecargas do operador.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="2c4a1-112">A sobrecarga do operador é útil nos casos em que é imediatamente óbvio qual será o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="2c4a1-113">Por exemplo, faz sentido ser capaz <xref:System.DateTime> de `DateTime` subtrair <xref:System.TimeSpan>um do outro e obter um .</span><span class="sxs-lookup"><span data-stu-id="2c4a1-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="2c4a1-114">No entanto, não é apropriado usar o operador lógico do sindicato para sociar duas consultas de banco de dados, ou usar o operador de turno para escrever para um fluxo.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="2c4a1-115">❌NÃO forneça sobrecargas ao operador, a menos que pelo menos uma das operações seja do tipo que define a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="2c4a1-116">✔️ os operadores de sobrecarga DO de forma simétrica.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="2c4a1-117">Por exemplo, se `operator==`você sobrecarregar o `operator!=`, você também deve sobrecarregar o .</span><span class="sxs-lookup"><span data-stu-id="2c4a1-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="2c4a1-118">Da mesma forma, `operator<`se você sobrecarregar `operator>`o , você também deve sobrecarregar o , e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="2c4a1-119">✔️ considerem fornecer métodos com nomes amigáveis que correspondam a cada operador sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="2c4a1-120">Muitos idiomas não suportam sobrecarga de operadores.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="2c4a1-121">Por essa razão, recomenda-se que os tipos que sobrecarregam os operadores incluam um método secundário com um nome específico de domínio apropriado que forneça funcionalidade equivalente.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="2c4a1-122">A tabela a seguir contém uma lista de operadores e os nomes de métodos amigáveis correspondentes.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="2c4a1-123">Símbolo do operador C#</span><span class="sxs-lookup"><span data-stu-id="2c4a1-123">C# Operator Symbol</span></span>|<span data-ttu-id="2c4a1-124">Nome de metadados</span><span class="sxs-lookup"><span data-stu-id="2c4a1-124">Metadata Name</span></span>|<span data-ttu-id="2c4a1-125">Nome amigável</span><span class="sxs-lookup"><span data-stu-id="2c4a1-125">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="2c4a1-126">Operador de sobrecarga ==</span><span class="sxs-lookup"><span data-stu-id="2c4a1-126">Overloading Operator ==</span></span>
 <span data-ttu-id="2c4a1-127">Sobrecarga `operator ==` é bastante complicado.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="2c4a1-128">A semântica do operador precisa ser compatível <xref:System.Object.Equals%2A?displayProperty=nameWithType>com vários outros membros, tais como .</span><span class="sxs-lookup"><span data-stu-id="2c4a1-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="2c4a1-129">Operadores de conversão</span><span class="sxs-lookup"><span data-stu-id="2c4a1-129">Conversion Operators</span></span>
 <span data-ttu-id="2c4a1-130">Os operadores de conversão são operadores não ários que permitem a conversão de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="2c4a1-131">Os operadores devem ser definidos como membros estáticos no operato ou no tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="2c4a1-132">Existem dois tipos de operadores de conversão: implícito e explícito.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="2c4a1-133">❌NÃO forneça um operador de conversão se tal conversão não for claramente esperada pelos usuários finais.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="2c4a1-134">❌NÃO defina operadores de conversão fora do domínio de um tipo.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="2c4a1-135">Por <xref:System.Int32>exemplo, <xref:System.Double>e <xref:System.Decimal> são todos os tipos <xref:System.DateTime> numéricos, enquanto que não são.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="2c4a1-136">Portanto, não deve haver operador de `Double(long)` conversão `DateTime`para converter a para a .</span><span class="sxs-lookup"><span data-stu-id="2c4a1-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="2c4a1-137">Um construtor é preferido nesse caso.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="2c4a1-138">❌NÃO forneça um operador de conversão implícita se a conversão for potencialmente perdida.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="2c4a1-139">Por exemplo, não deve haver `Double` uma `Int32` `Double` conversão implícita de `Int32`para porque tem um alcance maior do que .</span><span class="sxs-lookup"><span data-stu-id="2c4a1-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="2c4a1-140">Um operador de conversão explícita pode ser fornecido mesmo que a conversão seja potencialmente deficitária.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="2c4a1-141">❌NÃO jogue exceções de moldes implícitos.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="2c4a1-142">É muito difícil para os usuários finais entenderem o que está acontecendo, porque eles podem não estar cientes de que uma conversão está ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="2c4a1-143">✔️ DO <xref:System.InvalidCastException?displayProperty=nameWithType> jogar se uma chamada para um operador de elenco resultar em uma conversão de perda e o contrato do operador não permite conversões de perdas.</span><span class="sxs-lookup"><span data-stu-id="2c4a1-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="2c4a1-144">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="2c4a1-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="2c4a1-145">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="2c4a1-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="2c4a1-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="2c4a1-146">See also</span></span>

- [<span data-ttu-id="2c4a1-147">Diretrizes de design de membro</span><span class="sxs-lookup"><span data-stu-id="2c4a1-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="2c4a1-148">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="2c4a1-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

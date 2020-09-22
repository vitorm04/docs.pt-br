---
title: A cópia do parâmetro '<parametername>' do valor 'ByRef' de volta para o argumento correspondente é restrita do tipo '<typename1>' para o tipo '<typename2>'
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: 971110c505800b0ceba73506f2b2702516a7a23a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874546"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a><span data-ttu-id="bc6f1-102">A cópia do parâmetro '\<parametername>' do valor 'ByRef' de volta para o argumento correspondente é restrita do tipo '\<typename1>' para o tipo '\<typename2>'</span><span class="sxs-lookup"><span data-stu-id="bc6f1-102">Copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument narrows from type '\<typename1>' to type '\<typename2>'</span></span>

<span data-ttu-id="bc6f1-103">Um procedimento é chamado com um argumento que amplia o tipo de parâmetro correspondente e a conversão do parâmetro para o argumento é restrita.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="bc6f1-104">Quando você define uma classe ou estrutura, pode definir um ou mais operadores de conversão para converter essa classe ou tipo de estrutura em outros tipos.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="bc6f1-105">Você também pode definir operadores de conversão reverso para converter esses outros tipos de volta para o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="bc6f1-106">Quando você usa seu tipo de classe ou estrutura em uma chamada de procedimento, Visual Basic pode usar esses operadores de conversão para converter o tipo de um argumento para o tipo de seu parâmetro correspondente.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-106">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="bc6f1-107">Se você passar o argumento [ByRef](../modifiers/byref.md), o Visual Basic às vezes copiará o valor do argumento em uma variável local no procedimento em vez de passar uma referência.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-107">If you pass the argument [ByRef](../modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="bc6f1-108">Nesse caso, quando o procedimento retorna, Visual Basic deve copiar o valor da variável local de volta para o argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-108">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="bc6f1-109">Se um `ByRef` valor de argumento for copiado para o procedimento e o argumento e o parâmetro forem do mesmo tipo, nenhuma conversão será necessária.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="bc6f1-110">Mas se os tipos forem diferentes, Visual Basic deverá converter em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-110">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="bc6f1-111">Se um dos tipos for seu tipo de classe ou estrutura, Visual Basic deverá convertê-lo de e para o outro tipo.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-111">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="bc6f1-112">Se uma dessas conversões estiver ampliando, a conversão reversa poderá ser restrita.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="bc6f1-113">**ID do erro:** BC32053</span><span class="sxs-lookup"><span data-stu-id="bc6f1-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc6f1-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bc6f1-114">To correct this error</span></span>  
  
- <span data-ttu-id="bc6f1-115">Se possível, use um argumento de chamada do mesmo tipo que o parâmetro de procedimento, portanto Visual Basic não precisa fazer nenhuma conversão.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-115">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="bc6f1-116">Se você precisar chamar o procedimento com um tipo de argumento diferente do tipo de parâmetro, mas não precisar retornar um valor para o argumento de chamada, defina o parâmetro como [ByVal](../modifiers/byval.md) em vez de `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="bc6f1-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>  
  
- <span data-ttu-id="bc6f1-117">Se você precisar retornar um valor para o argumento de chamada, defina o operador de conversão reversa como [ampliação](../modifiers/widening.md), se possível.</span><span class="sxs-lookup"><span data-stu-id="bc6f1-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6f1-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="bc6f1-118">See also</span></span>

- [<span data-ttu-id="bc6f1-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="bc6f1-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="bc6f1-120">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="bc6f1-120">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bc6f1-121">Passar argumentos por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="bc6f1-121">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="bc6f1-122">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="bc6f1-122">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="bc6f1-123">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="bc6f1-123">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="bc6f1-124">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="bc6f1-124">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="bc6f1-125">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="bc6f1-125">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="bc6f1-126">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc6f1-126">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="bc6f1-127">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="bc6f1-127">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

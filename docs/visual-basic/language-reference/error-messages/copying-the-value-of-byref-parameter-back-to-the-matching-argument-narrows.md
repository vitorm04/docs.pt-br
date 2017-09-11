---
title: "Copiar o valor do parâmetro &quot;ByRef&quot; &quot;&lt;parametername&gt;&quot;para o argumento correspondente limita do tipo&quot;&lt;typename1&gt;&quot; no tipo&quot;&lt;typename2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
dev_langs:
- VB
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
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
ms.openlocfilehash: 10ad4af689c11f3e4defe43c4fed9ed579ba5305
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="6f335-102">Copiar o valor do parâmetro 'ByRef' '&lt;parametername&gt;'para o argumento correspondente limita do tipo'&lt;typename1&gt;' no tipo'&lt;typename2&gt;'</span><span class="sxs-lookup"><span data-stu-id="6f335-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="6f335-103">Um procedimento é chamado com um argumento que amplia para o tipo de parâmetro correspondente e a conversão do parâmetro para o argumento é restritiva.</span><span class="sxs-lookup"><span data-stu-id="6f335-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="6f335-104">Quando você define uma classe ou estrutura, você pode definir um ou mais operadores de conversão para converter esse tipo de classe ou estrutura para outros tipos.</span><span class="sxs-lookup"><span data-stu-id="6f335-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="6f335-105">Você também pode definir operadores de conversão reversa para converter esses tipos de volta para sua classe ou tipo de estrutura.</span><span class="sxs-lookup"><span data-stu-id="6f335-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="6f335-106">Quando você usa o tipo de classe ou estrutura em uma chamada de procedimento [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pode usar esses operadores de conversão para converter o tipo de um argumento para o tipo de seu parâmetro correspondente.</span><span class="sxs-lookup"><span data-stu-id="6f335-106">When you use your class or structure type in a procedure call, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="6f335-107">Se você passar o argumento [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] algumas vezes copia o valor do argumento para uma variável local no procedimento em vez de passar uma referência.</span><span class="sxs-lookup"><span data-stu-id="6f335-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="6f335-108">Nesse caso, quando o procedimento retorna, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve copiar o valor da variável local novamente para o argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="6f335-108">In such a case, when the procedure returns, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="6f335-109">Se um `ByRef` o valor do argumento é copiado no procedimento e o argumento e parâmetro são do mesmo tipo, nenhuma conversão é necessária.</span><span class="sxs-lookup"><span data-stu-id="6f335-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="6f335-110">Mas se os tipos forem diferentes, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve converter em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="6f335-110">But if the types are different, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must convert in both directions.</span></span> <span data-ttu-id="6f335-111">Se um dos tipos é o tipo de classe ou estrutura, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] deve convertê-lo para e de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="6f335-111">If one of the types is your class or structure type, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must convert it both to and from the other type.</span></span> <span data-ttu-id="6f335-112">Se uma dessas conversões está ampliando, a conversão reversa pode estar restringindo.</span><span class="sxs-lookup"><span data-stu-id="6f335-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="6f335-113">**ID do erro:** BC32053</span><span class="sxs-lookup"><span data-stu-id="6f335-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6f335-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6f335-114">To correct this error</span></span>  
  
-   <span data-ttu-id="6f335-115">Se possível, use um argumento chamando do mesmo tipo que o parâmetro do procedimento, dessa forma [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não precisa fazer nenhuma conversão.</span><span class="sxs-lookup"><span data-stu-id="6f335-115">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="6f335-116">Se você precisar chamar o procedimento com um argumento de tipo diferente do tipo de parâmetro mas não precisa retornar um valor para o argumento de chamada, defina o parâmetro para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) em vez de `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="6f335-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="6f335-117">Se você precisar retornar um valor para o argumento de chamada, defina o operador de conversão inversa como [Widening](../../../visual-basic/language-reference/modifiers/widening.md), se possível.</span><span class="sxs-lookup"><span data-stu-id="6f335-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f335-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f335-118">See Also</span></span>  
 <span data-ttu-id="6f335-119">[Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span><span class="sxs-lookup"><span data-stu-id="6f335-119">[Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span></span>  
<span data-ttu-id="6f335-120"> [Argumentos e parâmetros de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="6f335-120"> [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="6f335-121"> [Passando argumentos por valor e por referência](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6f335-121"> [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="6f335-122"> [Procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="6f335-122"> [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span></span>  
<span data-ttu-id="6f335-123"> [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="6f335-123"> [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="6f335-124"> [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="6f335-124"> [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="6f335-125"> [Como: definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="6f335-125"> [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="6f335-126"> [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="6f335-126"> [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="6f335-127"> [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="6f335-127"> [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>

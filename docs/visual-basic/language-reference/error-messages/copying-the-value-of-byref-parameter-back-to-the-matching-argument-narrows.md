---
title: "Copiar o valor de &#39; ByRef &#39; parâmetro &#39; &lt;parametername&gt;&#39; volta para a correspondência restringe de argumento de tipo de &#39;&lt; typename1&gt;&#39; para o tipo &#39;&lt; typename2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords: BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4bf993639007162e2e17d4b8cb9dfe8d5316acaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="04766-102">Copiar o valor de &#39; ByRef &#39; parâmetro &#39; &lt;parametername&gt;&#39; volta para a correspondência restringe de argumento de tipo de &#39;&lt; typename1&gt;&#39; para o tipo &#39;&lt; typename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="04766-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="04766-103">Um procedimento é chamado com um argumento que amplia para o tipo do parâmetro correspondente, e a conversão do parâmetro para o argumento é restritiva.</span><span class="sxs-lookup"><span data-stu-id="04766-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="04766-104">Quando você define uma classe ou estrutura, você pode definir um ou mais operadores de conversão para converter esse tipo de classe ou estrutura para outros tipos.</span><span class="sxs-lookup"><span data-stu-id="04766-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="04766-105">Você também pode definir operadores de conversão inversa para converter esses tipos de volta para sua classe ou tipo de estrutura.</span><span class="sxs-lookup"><span data-stu-id="04766-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="04766-106">Quando você usa o tipo de classe ou estrutura em uma chamada de procedimento, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pode usar esses operadores de conversão para converter o tipo de um argumento para o tipo de seu parâmetro correspondente.</span><span class="sxs-lookup"><span data-stu-id="04766-106">When you use your class or structure type in a procedure call, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="04766-107">Se você passar o argumento [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] algumas vezes copia o valor do argumento para uma variável local no procedimento em vez de passar uma referência.</span><span class="sxs-lookup"><span data-stu-id="04766-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="04766-108">Nesse caso, quando o procedimento retorna, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deve copiar o valor da variável local novamente para o argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="04766-108">In such a case, when the procedure returns, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="04766-109">Se um `ByRef` o valor do argumento é copiado para o procedimento e o argumento e parâmetro são do mesmo tipo, nenhuma conversão é necessária.</span><span class="sxs-lookup"><span data-stu-id="04766-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="04766-110">Porém, se os tipos forem diferentes, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deve converter em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="04766-110">But if the types are different, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert in both directions.</span></span> <span data-ttu-id="04766-111">Se um dos tipos é o tipo de classe ou estrutura, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] deve converter para e o outro tipo.</span><span class="sxs-lookup"><span data-stu-id="04766-111">If one of the types is your class or structure type, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert it both to and from the other type.</span></span> <span data-ttu-id="04766-112">Se um dessas conversões está ampliando, a conversão reversa pode estar restringindo.</span><span class="sxs-lookup"><span data-stu-id="04766-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="04766-113">**ID do erro:** BC32053</span><span class="sxs-lookup"><span data-stu-id="04766-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04766-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="04766-114">To correct this error</span></span>  
  
-   <span data-ttu-id="04766-115">Se possível, use um argumento chamando do mesmo tipo que o parâmetro do procedimento, portanto [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não precisa fazer nenhuma conversão.</span><span class="sxs-lookup"><span data-stu-id="04766-115">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="04766-116">Se você precisar chamar o procedimento com um argumento de tipo diferente do tipo de parâmetro, mas não precisa retornar um valor para o argumento de chamada, defina o parâmetro para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) em vez de `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="04766-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="04766-117">Se você precisar retornar um valor para o argumento de chamada, defina o operador de conversão inversa como [Widening](../../../visual-basic/language-reference/modifiers/widening.md), se possível.</span><span class="sxs-lookup"><span data-stu-id="04766-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04766-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04766-118">See Also</span></span>  
 [<span data-ttu-id="04766-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="04766-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="04766-120">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="04766-120">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="04766-121">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="04766-121">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="04766-122">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="04766-122">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="04766-123">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="04766-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="04766-124">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="04766-124">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="04766-125">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="04766-125">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="04766-126">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="04766-126">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="04766-127">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="04766-127">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

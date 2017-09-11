---
title: Tipo de dados inteiro (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
dev_langs:
- VB
helpviewer_keywords:
- numbers, whole
- enumerated values
- whole numbers
- integral data types
- integer numbers
- numbers, integer
- integers, data types
- literal type characters, I
- integers, types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters, %
- I literal type character
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
caps.latest.revision: 22
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
ms.openlocfilehash: 1e6f441420a05224ebf261a36749917641eb2e47
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="28893-102">Tipo de dados inteiro (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28893-102">Integer Data Type (Visual Basic)</span></span>
<span data-ttu-id="28893-103">Armazena inteiros de 32 bits (4 bytes) com sinal que variam em valor de -2.147.483.648 a 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="28893-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28893-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="28893-104">Remarks</span></span>  
 <span data-ttu-id="28893-105">O tipo de dados `Integer` proporciona um desempenho ideal em um processador de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="28893-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="28893-106">Os outros tipos integrais são mais lentos para carregar e armazenar na memória.</span><span class="sxs-lookup"><span data-stu-id="28893-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="28893-107">O valor padrão de `Integer` é 0.</span><span class="sxs-lookup"><span data-stu-id="28893-107">The default value of `Integer` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="28893-108">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="28893-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="28893-109">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="28893-109">**Interop Considerations.**</span></span> <span data-ttu-id="28893-110">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, lembre-se de que `Integer` possui uma largura de dados diferente (16 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="28893-110">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="28893-111">Se você estiver passando um argumento de 16 bits para esse componente, declare-o como `Short` em vez de `Integer` no seu novo código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="28893-111">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="28893-112">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="28893-112">**Widening.**</span></span> <span data-ttu-id="28893-113">O tipo de dados `Integer` é ampliado para `Long`, `Decimal`, `Single` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="28893-113">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="28893-114">Isso significa que você pode converter `Integer` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="28893-114">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="28893-115">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="28893-115">**Type Characters.**</span></span> <span data-ttu-id="28893-116">Acrescentar o caractere de tipo literal `I` a um literal o força ao tipo de dados `Integer`.</span><span class="sxs-lookup"><span data-stu-id="28893-116">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="28893-117">Acrescentar o caractere de tipo identificador `%` a qualquer identificador o força ao tipo `Integer`.</span><span class="sxs-lookup"><span data-stu-id="28893-117">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
-   <span data-ttu-id="28893-118">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="28893-118">**Framework Type.**</span></span> <span data-ttu-id="28893-119">O tipo correspondente no .NET Framework é o <xref:System.Int32?displayProperty=fullName>estrutura.</xref:System.Int32?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="28893-119">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=fullName> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="28893-120">Intervalo</span><span class="sxs-lookup"><span data-stu-id="28893-120">Range</span></span>  
 <span data-ttu-id="28893-121">Se você tentar definir uma variável de um tipo integral para um número fora do intervalo para esse tipo, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="28893-121">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="28893-122">Se você tentar defini-lo como uma fração, o número será arredondado para cima ou para baixo para o valor inteiro mais próximo.</span><span class="sxs-lookup"><span data-stu-id="28893-122">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="28893-123">Se o número for igualmente próximo de dois valores inteiros, o valor será arredondado para o inteiro par mais próximo.</span><span class="sxs-lookup"><span data-stu-id="28893-123">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="28893-124">Esse comportamento minimiza erros de arredondamento gerados ao arredondar consistentemente um valor de ponto médio em uma única direção.</span><span class="sxs-lookup"><span data-stu-id="28893-124">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="28893-125">O código a seguir mostra exemplos de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="28893-125">The following code shows examples of rounding.</span></span>  
  
```  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```  
  
## <a name="see-also"></a><span data-ttu-id="28893-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28893-126">See Also</span></span>  
 <span data-ttu-id="28893-127"><xref:System.Int32?displayProperty=fullName></xref:System.Int32?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="28893-127"><xref:System.Int32?displayProperty=fullName></span></span>   
<span data-ttu-id="28893-128"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="28893-128"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="28893-129"> [Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="28893-129"> [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md) </span></span>  
<span data-ttu-id="28893-130"> [Tipo de dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="28893-130"> [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md) </span></span>  
<span data-ttu-id="28893-131"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="28893-131"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="28893-132"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="28893-132"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="28893-133"> [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="28893-133"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>

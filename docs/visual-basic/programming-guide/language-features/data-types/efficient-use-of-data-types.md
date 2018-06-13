---
title: Uso eficiente de tipos de dados (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 6e71c4e2225bbcde3bb2bd20ae098f5600990051
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647755"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="8a2eb-102">Uso eficiente de tipos de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a2eb-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="8a2eb-103">Variáveis não declaradas e declaradas sem um tipo de dados são atribuídas a `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="8a2eb-104">Isso facilita escrever programas rapidamente, mas isso pode causar a execução mais lenta.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="8a2eb-105">Tipagem forte</span><span class="sxs-lookup"><span data-stu-id="8a2eb-105">Strong Typing</span></span>  
 <span data-ttu-id="8a2eb-106">Especificar tipos de dados para todas as variáveis é conhecido como *tipagem forte*.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="8a2eb-107">Usar tipagem forte apresenta várias vantagens:</span><span class="sxs-lookup"><span data-stu-id="8a2eb-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="8a2eb-108">Ele permite o suporte ao IntelliSense para suas variáveis.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="8a2eb-109">Isso permite que você veja suas propriedades e outros membros conforme você digita no código.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="8a2eb-110">Tira proveito da verificação de tipo do compilador.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="8a2eb-111">Captura instruções que podem falhar em tempo de execução devido a erros, como o estouro.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="8a2eb-112">Também captura chamadas para métodos em objetos que não dão suporte a eles.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="8a2eb-113">Isso resulta em execução mais rápida do seu código.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="8a2eb-114">Tipos de dados mais eficientes</span><span class="sxs-lookup"><span data-stu-id="8a2eb-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="8a2eb-115">Para variáveis que nunca contêm frações, os tipos de dados integrais são mais eficientes do que os tipos não integral.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="8a2eb-116">No Visual Basic, `Integer` e `UInteger` são os tipos numéricos mais eficientes.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="8a2eb-117">Para números fracionários, `Double` é o tipo de dados mais eficiente, porque os processadores em plataformas atuais executam operações de ponto flutuante de precisão dupla.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="8a2eb-118">No entanto, as operações com `Double` não são tão rápidas como com os tipos integrais como `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="8a2eb-119">Especificar o tipo de dados</span><span class="sxs-lookup"><span data-stu-id="8a2eb-119">Specifying Data Type</span></span>  
 <span data-ttu-id="8a2eb-120">Use o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para declarar uma variável de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="8a2eb-121">Você pode especificar simultaneamente seu nível de acesso usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegidos](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), ou [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="8a2eb-122">Conversão de caracteres</span><span class="sxs-lookup"><span data-stu-id="8a2eb-122">Character Conversion</span></span>  
 <span data-ttu-id="8a2eb-123">O `AscW` e `ChrW` funções operam em Unicode.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="8a2eb-124">Você deve usá-las preferencialmente a `Asc` e `Chr`, que devem traduzir de e para Unicode.</span><span class="sxs-lookup"><span data-stu-id="8a2eb-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a2eb-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a2eb-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="8a2eb-126">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="8a2eb-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="8a2eb-127">Tipos de Dados Numéricos</span><span class="sxs-lookup"><span data-stu-id="8a2eb-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="8a2eb-128">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="8a2eb-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="8a2eb-129">Usando o IntelliSense</span><span class="sxs-lookup"><span data-stu-id="8a2eb-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)

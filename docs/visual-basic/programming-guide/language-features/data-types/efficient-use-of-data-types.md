---
title: Uso eficiente de tipos de dados
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
ms.openlocfilehash: 7f446b264dcb5c05ed6ddfba34acbbf66be0e447
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084106"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="ab3b1-102">Uso eficiente de tipos de dados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab3b1-102">Efficient Use of Data Types (Visual Basic)</span></span>

<span data-ttu-id="ab3b1-103">Variáveis não declaradas e variáveis declaradas sem um tipo de dados recebem o `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="ab3b1-104">Isso facilita escrever programas rapidamente, mas pode fazer com que eles sejam executados mais lentamente.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="ab3b1-105">Tipagem forte</span><span class="sxs-lookup"><span data-stu-id="ab3b1-105">Strong Typing</span></span>

 <span data-ttu-id="ab3b1-106">Especificar tipos de dados para todas as suas variáveis é conhecido como tipagem *forte*.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="ab3b1-107">O uso de rigidez de tipos tem várias vantagens:</span><span class="sxs-lookup"><span data-stu-id="ab3b1-107">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="ab3b1-108">Ele habilita o suporte IntelliSense para suas variáveis.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="ab3b1-109">Isso permite que você veja suas propriedades e outros membros enquanto digita no código.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-109">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="ab3b1-110">Ele aproveita a verificação do tipo de compilador.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="ab3b1-111">Isso captura instruções que podem falhar em tempo de execução devido a erros como overflow.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="ab3b1-112">Ele também captura chamadas para métodos em objetos que não dão suporte a eles.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-112">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="ab3b1-113">Isso resulta em uma execução mais rápida do seu código.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-113">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="ab3b1-114">Tipos de dados mais eficientes</span><span class="sxs-lookup"><span data-stu-id="ab3b1-114">Most Efficient Data Types</span></span>

 <span data-ttu-id="ab3b1-115">Para variáveis que nunca contêm frações, os tipos de dados integral são mais eficientes do que os tipos não integrais.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="ab3b1-116">No Visual Basic, `Integer` e `UInteger` são os tipos numéricos mais eficientes.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="ab3b1-117">Para números fracionários, `Double` é o tipo de dados mais eficiente, porque os processadores em plataformas atuais executam operações de ponto flutuante em precisão dupla.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="ab3b1-118">No entanto, as operações com `Double` não são tão rápidas quanto com os tipos integrais, como `Integer` .</span><span class="sxs-lookup"><span data-stu-id="ab3b1-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="ab3b1-119">Especificando o tipo de dados</span><span class="sxs-lookup"><span data-stu-id="ab3b1-119">Specifying Data Type</span></span>

 <span data-ttu-id="ab3b1-120">Use a [instrução Dim](../../../language-reference/statements/dim-statement.md) para declarar uma variável de um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-120">Use the [Dim Statement](../../../language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="ab3b1-121">Você pode especificar simultaneamente seu nível de acesso usando a palavra-chave [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md)ou [Private](../../../language-reference/modifiers/private.md) , como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-121">You can simultaneously specify its access level by using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="ab3b1-122">Conversão de caracteres</span><span class="sxs-lookup"><span data-stu-id="ab3b1-122">Character Conversion</span></span>

 <span data-ttu-id="ab3b1-123">As `AscW` `ChrW` funções e operam em Unicode.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="ab3b1-124">Você deve usá-los em preferência ao `Asc` e `Chr` , que devem ser traduzidos para dentro e fora do Unicode.</span><span class="sxs-lookup"><span data-stu-id="ab3b1-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab3b1-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="ab3b1-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="ab3b1-126">Data Types</span><span class="sxs-lookup"><span data-stu-id="ab3b1-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="ab3b1-127">Tipos de dados numéricos</span><span class="sxs-lookup"><span data-stu-id="ab3b1-127">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="ab3b1-128">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="ab3b1-128">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="ab3b1-129">Usando o IntelliSense</span><span class="sxs-lookup"><span data-stu-id="ab3b1-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)

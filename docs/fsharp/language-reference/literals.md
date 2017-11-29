---
title: Literais (F#)
description: "Saiba mais sobre os tipos de literal em F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4b1d6e9d-f933-4cd4-966d-d643152c27e4
ms.openlocfilehash: 6bb1f233b6846e226c4e73aee00b8cf77735fe2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="literals"></a><span data-ttu-id="de0c0-104">Literais</span><span class="sxs-lookup"><span data-stu-id="de0c0-104">Literals</span></span>

> [!NOTE]
<span data-ttu-id="de0c0-105">Os links de referência de API neste artigo levará você ao MSDN (até o momento).</span><span class="sxs-lookup"><span data-stu-id="de0c0-105">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="de0c0-106">Este tópico fornece uma tabela que mostra como especificar o tipo de um literal em F #.</span><span class="sxs-lookup"><span data-stu-id="de0c0-106">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="de0c0-107">Tipos literais</span><span class="sxs-lookup"><span data-stu-id="de0c0-107">Literal Types</span></span>
<span data-ttu-id="de0c0-108">A tabela a seguir mostra os tipos de literal em F #.</span><span class="sxs-lookup"><span data-stu-id="de0c0-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="de0c0-109">Caracteres que representam os dígitos em notação hexadecimal não diferenciam maiusculas de minúsculas; caracteres que identifica o tipo diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="de0c0-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="de0c0-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="de0c0-110">Type</span></span>|<span data-ttu-id="de0c0-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="de0c0-111">Description</span></span>|<span data-ttu-id="de0c0-112">Prefixo ou sufixo</span><span class="sxs-lookup"><span data-stu-id="de0c0-112">Suffix or prefix</span></span>|<span data-ttu-id="de0c0-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="de0c0-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="de0c0-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="de0c0-114">sbyte</span></span>|<span data-ttu-id="de0c0-115">inteiro assinado de 8 bits</span><span class="sxs-lookup"><span data-stu-id="de0c0-115">signed 8-bit integer</span></span>|<span data-ttu-id="de0c0-116">y</span><span class="sxs-lookup"><span data-stu-id="de0c0-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="de0c0-117">byte</span><span class="sxs-lookup"><span data-stu-id="de0c0-117">byte</span></span>|<span data-ttu-id="de0c0-118">número de natural de 8 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="de0c0-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="de0c0-119">uy</span><span class="sxs-lookup"><span data-stu-id="de0c0-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="de0c0-120">int16</span><span class="sxs-lookup"><span data-stu-id="de0c0-120">int16</span></span>|<span data-ttu-id="de0c0-121">Inteiro assinado de 16 bits</span><span class="sxs-lookup"><span data-stu-id="de0c0-121">signed 16-bit integer</span></span>|<span data-ttu-id="de0c0-122">s</span><span class="sxs-lookup"><span data-stu-id="de0c0-122">s</span></span>|`86s`|
|<span data-ttu-id="de0c0-123">uint16</span><span class="sxs-lookup"><span data-stu-id="de0c0-123">uint16</span></span>|<span data-ttu-id="de0c0-124">número de natural de 16 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="de0c0-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="de0c0-125">us</span><span class="sxs-lookup"><span data-stu-id="de0c0-125">us</span></span>|`86us`|
|<span data-ttu-id="de0c0-126">int</span><span class="sxs-lookup"><span data-stu-id="de0c0-126">int</span></span><br /><br /><span data-ttu-id="de0c0-127">int32</span><span class="sxs-lookup"><span data-stu-id="de0c0-127">int32</span></span>|<span data-ttu-id="de0c0-128">Inteiro assinado de 32 bits</span><span class="sxs-lookup"><span data-stu-id="de0c0-128">signed 32-bit integer</span></span>|<span data-ttu-id="de0c0-129">l ou none</span><span class="sxs-lookup"><span data-stu-id="de0c0-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="de0c0-130">uint</span><span class="sxs-lookup"><span data-stu-id="de0c0-130">uint</span></span><br /><br /><span data-ttu-id="de0c0-131">uint32</span><span class="sxs-lookup"><span data-stu-id="de0c0-131">uint32</span></span>|<span data-ttu-id="de0c0-132">número de natural de 32 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="de0c0-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="de0c0-133">u ou ul</span><span class="sxs-lookup"><span data-stu-id="de0c0-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="de0c0-134">unativeint</span><span class="sxs-lookup"><span data-stu-id="de0c0-134">unativeint</span></span>|<span data-ttu-id="de0c0-135">ponteiro nativo como um número sem sinal de natural</span><span class="sxs-lookup"><span data-stu-id="de0c0-135">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="de0c0-136">Cancelar</span><span class="sxs-lookup"><span data-stu-id="de0c0-136">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="de0c0-137">int64</span><span class="sxs-lookup"><span data-stu-id="de0c0-137">int64</span></span>|<span data-ttu-id="de0c0-138">inteiro assinado de 64 bits</span><span class="sxs-lookup"><span data-stu-id="de0c0-138">signed 64-bit integer</span></span>|<span data-ttu-id="de0c0-139">L</span><span class="sxs-lookup"><span data-stu-id="de0c0-139">L</span></span>|`86L`|
|<span data-ttu-id="de0c0-140">uint64</span><span class="sxs-lookup"><span data-stu-id="de0c0-140">uint64</span></span>|<span data-ttu-id="de0c0-141">número de natural de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="de0c0-141">unsigned 64-bit natural number</span></span>|<span data-ttu-id="de0c0-142">UL</span><span class="sxs-lookup"><span data-stu-id="de0c0-142">UL</span></span>|`86UL`|
|<span data-ttu-id="de0c0-143">único, float32</span><span class="sxs-lookup"><span data-stu-id="de0c0-143">single, float32</span></span>|<span data-ttu-id="de0c0-144">número de ponto flutuante de 32 bits</span><span class="sxs-lookup"><span data-stu-id="de0c0-144">32-bit floating point number</span></span>|<span data-ttu-id="de0c0-145">F ou f</span><span class="sxs-lookup"><span data-stu-id="de0c0-145">F or f</span></span>|<span data-ttu-id="de0c0-146">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="de0c0-146">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="de0c0-147">LF</span><span class="sxs-lookup"><span data-stu-id="de0c0-147">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="de0c0-148">float; duplo</span><span class="sxs-lookup"><span data-stu-id="de0c0-148">float; double</span></span>|<span data-ttu-id="de0c0-149">número de ponto flutuante de 64 bits</span><span class="sxs-lookup"><span data-stu-id="de0c0-149">64-bit floating point number</span></span>|<span data-ttu-id="de0c0-150">nenhum</span><span class="sxs-lookup"><span data-stu-id="de0c0-150">none</span></span>|<span data-ttu-id="de0c0-151">`4.14`ou `2.3E+32` ou`2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="de0c0-151">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="de0c0-152">LF</span><span class="sxs-lookup"><span data-stu-id="de0c0-152">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="de0c0-153">bigint</span><span class="sxs-lookup"><span data-stu-id="de0c0-153">bigint</span></span>|<span data-ttu-id="de0c0-154">inteiro que não se limitam a representação de 64 bits</span><span class="sxs-lookup"><span data-stu-id="de0c0-154">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="de0c0-155">I</span><span class="sxs-lookup"><span data-stu-id="de0c0-155">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="de0c0-156">decimal</span><span class="sxs-lookup"><span data-stu-id="de0c0-156">decimal</span></span>|<span data-ttu-id="de0c0-157">número fracionário representado como um ponto fixo ou um número racional</span><span class="sxs-lookup"><span data-stu-id="de0c0-157">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="de0c0-158">M ou m</span><span class="sxs-lookup"><span data-stu-id="de0c0-158">M or m</span></span>|<span data-ttu-id="de0c0-159">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="de0c0-159">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="de0c0-160">Char</span><span class="sxs-lookup"><span data-stu-id="de0c0-160">Char</span></span>|<span data-ttu-id="de0c0-161">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="de0c0-161">Unicode character</span></span>|<span data-ttu-id="de0c0-162">nenhum</span><span class="sxs-lookup"><span data-stu-id="de0c0-162">none</span></span>|`'a'`|
|<span data-ttu-id="de0c0-163">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="de0c0-163">String</span></span>|<span data-ttu-id="de0c0-164">Cadeia de caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="de0c0-164">Unicode string</span></span>|<span data-ttu-id="de0c0-165">nenhum</span><span class="sxs-lookup"><span data-stu-id="de0c0-165">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="de0c0-166">ou</span><span class="sxs-lookup"><span data-stu-id="de0c0-166">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="de0c0-167">ou</span><span class="sxs-lookup"><span data-stu-id="de0c0-167">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="de0c0-168">ou</span><span class="sxs-lookup"><span data-stu-id="de0c0-168">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="de0c0-169">Consulte também [cadeias de caracteres](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="de0c0-169">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="de0c0-170">byte</span><span class="sxs-lookup"><span data-stu-id="de0c0-170">byte</span></span>|<span data-ttu-id="de0c0-171">Caracteres ASCII</span><span class="sxs-lookup"><span data-stu-id="de0c0-171">ASCII character</span></span>|<span data-ttu-id="de0c0-172">B</span><span class="sxs-lookup"><span data-stu-id="de0c0-172">B</span></span>|`'a'B`|
|<span data-ttu-id="de0c0-173">byte[]</span><span class="sxs-lookup"><span data-stu-id="de0c0-173">byte[]</span></span>|<span data-ttu-id="de0c0-174">Cadeia de caracteres ASCII</span><span class="sxs-lookup"><span data-stu-id="de0c0-174">ASCII string</span></span>|<span data-ttu-id="de0c0-175">B</span><span class="sxs-lookup"><span data-stu-id="de0c0-175">B</span></span>|`"text"B`|
|<span data-ttu-id="de0c0-176">Cadeia de caracteres ou byte]</span><span class="sxs-lookup"><span data-stu-id="de0c0-176">String or byte[]</span></span>|<span data-ttu-id="de0c0-177">cadeia de caracteres textual</span><span class="sxs-lookup"><span data-stu-id="de0c0-177">verbatim string</span></span>|<span data-ttu-id="de0c0-178">prefixo @</span><span class="sxs-lookup"><span data-stu-id="de0c0-178">@ prefix</span></span>|<span data-ttu-id="de0c0-179">`@"\\server\share"`(Unicode)</span><span class="sxs-lookup"><span data-stu-id="de0c0-179">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="de0c0-180">`@"\\server\share"B`(ASCII)</span><span class="sxs-lookup"><span data-stu-id="de0c0-180">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="de0c0-181">Comentários</span><span class="sxs-lookup"><span data-stu-id="de0c0-181">Remarks</span></span>
<span data-ttu-id="de0c0-182">Cadeias de caracteres Unicode podem conter codificações explícitas que você pode especificar usando `\u` seguido por um código hexadecimal de 16 bits ou UTF-32 codificações que você pode especificar usando `\U` seguido por um código hexadecimal de 32 bits que representa um Unicode par substituto.</span><span class="sxs-lookup"><span data-stu-id="de0c0-182">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="de0c0-183">A partir do F # 3.1, você pode usar o `+` entrar para combinar os literais de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="de0c0-183">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="de0c0-184">Você também pode usar o bit a bit ou (`|||`) operador para combinar os sinalizadores de enum.</span><span class="sxs-lookup"><span data-stu-id="de0c0-184">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="de0c0-185">Por exemplo, o código a seguir é legal no F # 3.1:</span><span class="sxs-lookup"><span data-stu-id="de0c0-185">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="de0c0-186">Não é permitido o uso de outros operadores bit a bit.</span><span class="sxs-lookup"><span data-stu-id="de0c0-186">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="de0c0-187">Literais nomeadas</span><span class="sxs-lookup"><span data-stu-id="de0c0-187">Named Literals</span></span>
<span data-ttu-id="de0c0-188">Os valores que devem ser constantes podem ser marcados com o [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atributo.</span><span class="sxs-lookup"><span data-stu-id="de0c0-188">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="de0c0-189">Este atributo tem o efeito de causar um valor a ser compilado como uma constante.</span><span class="sxs-lookup"><span data-stu-id="de0c0-189">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="de0c0-190">No padrão de correspondência de expressões, identificadores que começam com caracteres minúsculos sempre são tratados como variáveis a ser associado, em vez de como literais, portanto, você deve usar maiusculas iniciais ao definir literais.</span><span class="sxs-lookup"><span data-stu-id="de0c0-190">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="de0c0-191">Números inteiros em outras Bases</span><span class="sxs-lookup"><span data-stu-id="de0c0-191">Integers In Other Bases</span></span>

<span data-ttu-id="de0c0-192">Inteiros de 32 bits com sinal também podem ser especificados em hexadecimal, octal ou binário usando um `0x`, `0o` ou `0b` prefixo respectivamente.</span><span class="sxs-lookup"><span data-stu-id="de0c0-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="de0c0-193">Sublinhados em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="de0c0-193">Underscores in Numeric Literals</span></span>

<span data-ttu-id="de0c0-194">A partir do F # 4.1, você pode separar dígitos com o caractere de sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="de0c0-194">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="de0c0-195">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de0c0-195">See Also</span></span>

[<span data-ttu-id="de0c0-196">Classe Core. literalattribute</span><span class="sxs-lookup"><span data-stu-id="de0c0-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

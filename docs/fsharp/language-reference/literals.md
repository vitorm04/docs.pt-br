---
title: Literais
description: 'Saiba mais sobre os tipos literais na linguagem de programação F #.'
ms.date: 06/28/2019
ms.openlocfilehash: 98d609a1cf0beb00c0dd4d45ea343aaa2280b62e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855017"
---
# <a name="literals"></a><span data-ttu-id="f3f10-103">Literais</span><span class="sxs-lookup"><span data-stu-id="f3f10-103">Literals</span></span>

<span data-ttu-id="f3f10-104">Este artigo fornece uma tabela que mostra como especificar o tipo de um literal em F #.</span><span class="sxs-lookup"><span data-stu-id="f3f10-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

> [!NOTE]
> <span data-ttu-id="f3f10-105">A referência da API docs.microsoft.com para F # não está completa.</span><span class="sxs-lookup"><span data-stu-id="f3f10-105">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="f3f10-106">Se você encontrar links desfeitos, consulte a [documentação da biblioteca principal F #](https://fsharp.github.io/fsharp-core-docs/) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f3f10-106">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="literal-types"></a><span data-ttu-id="f3f10-107"> Tipos literais</span><span class="sxs-lookup"><span data-stu-id="f3f10-107">Literal types</span></span>

<span data-ttu-id="f3f10-108">A tabela a seguir mostra os tipos literais em F #.</span><span class="sxs-lookup"><span data-stu-id="f3f10-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="f3f10-109">Os caracteres que representam dígitos na notação hexadecimal não diferenciam maiúsculas de minúsculas; os caracteres que identificam o tipo diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f3f10-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="f3f10-110">Type</span><span class="sxs-lookup"><span data-stu-id="f3f10-110">Type</span></span>|<span data-ttu-id="f3f10-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3f10-111">Description</span></span>|<span data-ttu-id="f3f10-112">Sufixo ou prefixo</span><span class="sxs-lookup"><span data-stu-id="f3f10-112">Suffix or prefix</span></span>|<span data-ttu-id="f3f10-113">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f3f10-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="f3f10-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="f3f10-114">sbyte</span></span>|<span data-ttu-id="f3f10-115">inteiro de 8 bits assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-115">signed 8-bit integer</span></span>|<span data-ttu-id="f3f10-116">a</span><span class="sxs-lookup"><span data-stu-id="f3f10-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="f3f10-117">byte</span><span class="sxs-lookup"><span data-stu-id="f3f10-117">byte</span></span>|<span data-ttu-id="f3f10-118">número natural de 8 bits não assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="f3f10-119">uy</span><span class="sxs-lookup"><span data-stu-id="f3f10-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="f3f10-120">int16</span><span class="sxs-lookup"><span data-stu-id="f3f10-120">int16</span></span>|<span data-ttu-id="f3f10-121">inteiro de 16 bits assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-121">signed 16-bit integer</span></span>|<span data-ttu-id="f3f10-122">s</span><span class="sxs-lookup"><span data-stu-id="f3f10-122">s</span></span>|`86s`|
|<span data-ttu-id="f3f10-123">uint16</span><span class="sxs-lookup"><span data-stu-id="f3f10-123">uint16</span></span>|<span data-ttu-id="f3f10-124">número natural de 16 bits não assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="f3f10-125">us</span><span class="sxs-lookup"><span data-stu-id="f3f10-125">us</span></span>|`86us`|
|<span data-ttu-id="f3f10-126">int</span><span class="sxs-lookup"><span data-stu-id="f3f10-126">int</span></span><br /><br /><span data-ttu-id="f3f10-127">int32</span><span class="sxs-lookup"><span data-stu-id="f3f10-127">int32</span></span>|<span data-ttu-id="f3f10-128">inteiro de 32 bits assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-128">signed 32-bit integer</span></span>|<span data-ttu-id="f3f10-129">l ou None</span><span class="sxs-lookup"><span data-stu-id="f3f10-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="f3f10-130">uint</span><span class="sxs-lookup"><span data-stu-id="f3f10-130">uint</span></span><br /><br /><span data-ttu-id="f3f10-131">uint32</span><span class="sxs-lookup"><span data-stu-id="f3f10-131">uint32</span></span>|<span data-ttu-id="f3f10-132">número natural de 32 bits não assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="f3f10-133">u ou UL</span><span class="sxs-lookup"><span data-stu-id="f3f10-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="f3f10-134">nativeint</span><span class="sxs-lookup"><span data-stu-id="f3f10-134">nativeint</span></span>|<span data-ttu-id="f3f10-135">ponteiro nativo para um número natural assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-135">native pointer to a signed natural number</span></span>|<span data-ttu-id="f3f10-136">n</span><span class="sxs-lookup"><span data-stu-id="f3f10-136">n</span></span>|`123n`|
|<span data-ttu-id="f3f10-137">unativeint</span><span class="sxs-lookup"><span data-stu-id="f3f10-137">unativeint</span></span>|<span data-ttu-id="f3f10-138">ponteiro nativo como um número natural não assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-138">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="f3f10-139">anula</span><span class="sxs-lookup"><span data-stu-id="f3f10-139">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="f3f10-140">int64</span><span class="sxs-lookup"><span data-stu-id="f3f10-140">int64</span></span>|<span data-ttu-id="f3f10-141">inteiro de 64 bits assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-141">signed 64-bit integer</span></span>|<span data-ttu-id="f3f10-142">L</span><span class="sxs-lookup"><span data-stu-id="f3f10-142">L</span></span>|`86L`|
|<span data-ttu-id="f3f10-143">uint64</span><span class="sxs-lookup"><span data-stu-id="f3f10-143">uint64</span></span>|<span data-ttu-id="f3f10-144">número natural de 64 bits não assinado</span><span class="sxs-lookup"><span data-stu-id="f3f10-144">unsigned 64-bit natural number</span></span>|<span data-ttu-id="f3f10-145">UL</span><span class="sxs-lookup"><span data-stu-id="f3f10-145">UL</span></span>|`86UL`|
|<span data-ttu-id="f3f10-146">único, float32</span><span class="sxs-lookup"><span data-stu-id="f3f10-146">single, float32</span></span>|<span data-ttu-id="f3f10-147">número de ponto flutuante de 32 bits</span><span class="sxs-lookup"><span data-stu-id="f3f10-147">32-bit floating point number</span></span>|<span data-ttu-id="f3f10-148">F ou f</span><span class="sxs-lookup"><span data-stu-id="f3f10-148">F or f</span></span>|<span data-ttu-id="f3f10-149">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="f3f10-149">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="f3f10-150">alimentação</span><span class="sxs-lookup"><span data-stu-id="f3f10-150">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="f3f10-151">barra Clique</span><span class="sxs-lookup"><span data-stu-id="f3f10-151">float; double</span></span>|<span data-ttu-id="f3f10-152">número de ponto flutuante de 64 bits</span><span class="sxs-lookup"><span data-stu-id="f3f10-152">64-bit floating point number</span></span>|<span data-ttu-id="f3f10-153">nenhum</span><span class="sxs-lookup"><span data-stu-id="f3f10-153">none</span></span>|<span data-ttu-id="f3f10-154">`4.14` ou `2.3E+32` ou `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="f3f10-154">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="f3f10-155">ALIMENTAÇÃO</span><span class="sxs-lookup"><span data-stu-id="f3f10-155">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="f3f10-156">BIGINT</span><span class="sxs-lookup"><span data-stu-id="f3f10-156">bigint</span></span>|<span data-ttu-id="f3f10-157">inteiro não limitado à representação de 64 bits</span><span class="sxs-lookup"><span data-stu-id="f3f10-157">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="f3f10-158">I</span><span class="sxs-lookup"><span data-stu-id="f3f10-158">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="f3f10-159">decimal</span><span class="sxs-lookup"><span data-stu-id="f3f10-159">decimal</span></span>|<span data-ttu-id="f3f10-160">número fracionário representado como um ponto fixo ou um número racional</span><span class="sxs-lookup"><span data-stu-id="f3f10-160">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="f3f10-161">M ou m</span><span class="sxs-lookup"><span data-stu-id="f3f10-161">M or m</span></span>|<span data-ttu-id="f3f10-162">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="f3f10-162">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="f3f10-163">Char</span><span class="sxs-lookup"><span data-stu-id="f3f10-163">Char</span></span>|<span data-ttu-id="f3f10-164">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="f3f10-164">Unicode character</span></span>|<span data-ttu-id="f3f10-165">nenhum</span><span class="sxs-lookup"><span data-stu-id="f3f10-165">none</span></span>|<span data-ttu-id="f3f10-166">`'a'` ou `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="f3f10-166">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="f3f10-167">String</span><span class="sxs-lookup"><span data-stu-id="f3f10-167">String</span></span>|<span data-ttu-id="f3f10-168">Cadeia de caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="f3f10-168">Unicode string</span></span>|<span data-ttu-id="f3f10-169">nenhum</span><span class="sxs-lookup"><span data-stu-id="f3f10-169">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="f3f10-170">ou o</span><span class="sxs-lookup"><span data-stu-id="f3f10-170">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="f3f10-171">ou o</span><span class="sxs-lookup"><span data-stu-id="f3f10-171">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="f3f10-172">ou o</span><span class="sxs-lookup"><span data-stu-id="f3f10-172">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="f3f10-173">Consulte também [cadeias de caracteres](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="f3f10-173">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="f3f10-174">byte</span><span class="sxs-lookup"><span data-stu-id="f3f10-174">byte</span></span>|<span data-ttu-id="f3f10-175">Caractere ASCII</span><span class="sxs-lookup"><span data-stu-id="f3f10-175">ASCII character</span></span>|<span data-ttu-id="f3f10-176">B</span><span class="sxs-lookup"><span data-stu-id="f3f10-176">B</span></span>|`'a'B`|
|<span data-ttu-id="f3f10-177">byte[]</span><span class="sxs-lookup"><span data-stu-id="f3f10-177">byte[]</span></span>|<span data-ttu-id="f3f10-178">Cadeia de caracteres ASCII</span><span class="sxs-lookup"><span data-stu-id="f3f10-178">ASCII string</span></span>|<span data-ttu-id="f3f10-179">B</span><span class="sxs-lookup"><span data-stu-id="f3f10-179">B</span></span>|`"text"B`|
|<span data-ttu-id="f3f10-180">Cadeia de caracteres ou byte []</span><span class="sxs-lookup"><span data-stu-id="f3f10-180">String or byte[]</span></span>|<span data-ttu-id="f3f10-181">Cadeia de caracteres textual</span><span class="sxs-lookup"><span data-stu-id="f3f10-181">verbatim string</span></span>|<span data-ttu-id="f3f10-182">@ prefix</span><span class="sxs-lookup"><span data-stu-id="f3f10-182">@ prefix</span></span>|<span data-ttu-id="f3f10-183">`@"\\server\share"`Unicode</span><span class="sxs-lookup"><span data-stu-id="f3f10-183">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="f3f10-184">`@"\\server\share"B`LOCALIZADOS</span><span class="sxs-lookup"><span data-stu-id="f3f10-184">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="f3f10-185">Literais nomeadas</span><span class="sxs-lookup"><span data-stu-id="f3f10-185">Named literals</span></span>

<span data-ttu-id="f3f10-186">Os valores que se destinam a serem constantes podem ser marcados com o atributo [literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) .</span><span class="sxs-lookup"><span data-stu-id="f3f10-186">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="f3f10-187">Esse atributo tem o efeito de fazer com que um valor seja compilado como uma constante.</span><span class="sxs-lookup"><span data-stu-id="f3f10-187">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="f3f10-188">Em expressões de correspondência de padrões, os identificadores que começam com caracteres minúsculos são sempre tratados como variáveis a serem associadas, e não como literais, de modo que você geralmente deve usar maiúsculas iniciais ao definir literais.</span><span class="sxs-lookup"><span data-stu-id="f3f10-188">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a><span data-ttu-id="f3f10-189">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3f10-189">Remarks</span></span>

<span data-ttu-id="f3f10-190">As cadeias de caracteres Unicode podem conter codificações explícitas que você pode especificar usando `\u` seguido por um código hexadecimal de 16 bits (0000-ffff) ou codificações UTF-32 que você pode especificar usando `\U` seguido por um código hexadecimal de 32 bits que representa qualquer ponto de código Unicode (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="f3f10-190">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="f3f10-191">O uso de outros outros operadores bit a não `|||` é permitido.</span><span class="sxs-lookup"><span data-stu-id="f3f10-191">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="f3f10-192">Inteiros em outras bases</span><span class="sxs-lookup"><span data-stu-id="f3f10-192">Integers in other bases</span></span>

<span data-ttu-id="f3f10-193">Os inteiros de 32 bits assinados também podem ser especificados em hexadecimal, octal ou binário usando um `0x` `0o` prefixo, ou `0b` respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f3f10-193">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="f3f10-194">Sublinhados em literais numéricos</span><span class="sxs-lookup"><span data-stu-id="f3f10-194">Underscores in numeric literals</span></span>

<span data-ttu-id="f3f10-195">Você pode separar dígitos com o caractere de sublinhado ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="f3f10-195">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="f3f10-196">Confira também</span><span class="sxs-lookup"><span data-stu-id="f3f10-196">See also</span></span>

- [<span data-ttu-id="f3f10-197">Classe Core. LiteralAttribute</span><span class="sxs-lookup"><span data-stu-id="f3f10-197">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

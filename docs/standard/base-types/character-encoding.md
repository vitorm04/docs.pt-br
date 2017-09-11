---
title: "Codificação de caracteres no .NET"
description: "Codificação de caracteres no .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bce54e41-e9dc-493a-8988-1cbadc340fe8
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: a8f42fa6a37f8de6f13186ea2ac17b2b2ced1601
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="character-encoding-in-net"></a><span data-ttu-id="d1217-104">Codificação de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="d1217-104">Character encoding in .NET</span></span>

<span data-ttu-id="d1217-105">Os caracteres são entidades abstratas que podem ser representadas de muitas maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="d1217-105">Characters are abstract entities that can be represented in many different ways.</span></span> <span data-ttu-id="d1217-106">Uma codificação de caracteres é um sistema que emparelha cada caractere em um conjunto de caracteres com suporte com algum valor que representa esse caractere.</span><span class="sxs-lookup"><span data-stu-id="d1217-106">A character encoding is a system that pairs each character in a supported character set with some value that represents that character.</span></span> <span data-ttu-id="d1217-107">Por exemplo, o código Morse é uma codificação de caracteres que emparelha cada caractere do alfabeto romano com um padrão de pontos e traços adequados para transmissão por linhas telegráficas.</span><span class="sxs-lookup"><span data-stu-id="d1217-107">For example, Morse code is a character encoding that pairs each character in the Roman alphabet with a pattern of dots and dashes that are suitable for transmission over telegraph lines.</span></span> <span data-ttu-id="d1217-108">Uma codificação de caracteres para computadores emparelha cada caractere em um conjunto de caracteres com suporte com um valor numérico que representa esse caractere.</span><span class="sxs-lookup"><span data-stu-id="d1217-108">A character encoding for computers pairs each character in a supported character set with a numeric value that represents that character.</span></span> <span data-ttu-id="d1217-109">Uma codificação de caracteres tem dois componentes distintos:</span><span class="sxs-lookup"><span data-stu-id="d1217-109">A character encoding has two distinct components:</span></span>

* <span data-ttu-id="d1217-110">Um codificador, que converte uma sequência de caracteres em uma sequência de valores numéricos (bytes).</span><span class="sxs-lookup"><span data-stu-id="d1217-110">An encoder, which translates a sequence of characters into a sequence of numeric values (bytes).</span></span>

* <span data-ttu-id="d1217-111">Um decodificador, que converte uma sequência de bytes em uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-111">A decoder, which translates a sequence of bytes into a sequence of characters.</span></span>

<span data-ttu-id="d1217-112">A codificação de caracteres descreve as regras por meio das quais um codificador e um decodificador são operados.</span><span class="sxs-lookup"><span data-stu-id="d1217-112">Character encoding describes the rules by which an encoder and a decoder operate.</span></span> <span data-ttu-id="d1217-113">Por exemplo, a classe [UTF8Encoding](xref:System.Text.UTF8Encoding) descreve as regras de codificação para UTF-8 (Formato de Transformação Unicode de 8 bits), e de decodificação desse formato, que usa de um a quatro bytes para representar um único caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="d1217-113">For example, the [UTF8Encoding](xref:System.Text.UTF8Encoding) class describes the rules for encoding to, and decoding from, 8-bit Unicode Transformation Format (UTF-8), which uses one to four bytes to represent a single Unicode character.</span></span> <span data-ttu-id="d1217-114">Codificar e decodificar também podem incluir a validação.</span><span class="sxs-lookup"><span data-stu-id="d1217-114">Encoding and decoding can also include validation.</span></span> <span data-ttu-id="d1217-115">Por exemplo, a classe [UnicodeEncoding](xref:System.Text.UnicodeEncoding) verifica todos os substitutos para certificar-se de eles constituem pares alternativos válidos.</span><span class="sxs-lookup"><span data-stu-id="d1217-115">For example, the [UnicodeEncoding](xref:System.Text.UnicodeEncoding) class checks all surrogates to make sure they constitute valid surrogate pairs.</span></span> <span data-ttu-id="d1217-116">(Um par alternativo consiste em um caractere com um ponto de código que varia de U+D800 a U+DBFF seguido por um caractere com um ponto de código que varia de U+DC00 a U+DFFF.) Uma estratégia de fallback determina como um codificador lida com caracteres inválidos ou como um decodificador lida com bytes inválidos.</span><span class="sxs-lookup"><span data-stu-id="d1217-116">(A surrogate pair consists of a character with a code point that ranges from U+D800 to U+DBFF followed by a character with a code point that ranges from U+DC00 to U+DFFF.) A fallback strategy determines how an encoder handles invalid characters or how a decoder handles invalid bytes.</span></span> 

> [!WARNING]
> <span data-ttu-id="d1217-117">As classes de codificação .NET fornecem uma maneira de armazenar e converter dados de caractere.</span><span class="sxs-lookup"><span data-stu-id="d1217-117">The .NET encoding classes provide a way to store and convert character data.</span></span> <span data-ttu-id="d1217-118">Elas não devem ser usadas para armazenar dados binários no formato de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-118">They should not be used to store binary data in string form.</span></span> <span data-ttu-id="d1217-119">Dependendo da codificação usada, a conversão de dados binários em formato de cadeia de caracteres com classes de codificação pode introduzir um comportamento inesperado e produzir dados imprecisos ou corrompidos.</span><span class="sxs-lookup"><span data-stu-id="d1217-119">Depending on the encoding used, converting binary data to string format with the encoding classes can introduce unexpected behavior and produce inaccurate or corrupted data.</span></span> <span data-ttu-id="d1217-120">Para converter dados binários em um formato de cadeia de caracteres, use o método [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="d1217-120">To convert binary data to a string form, use the [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])) method.</span></span> 
 
<span data-ttu-id="d1217-121">O .NET usa a codificação UTF-16 (representado pela classe [UnicodeEncoding](xref:System.Text.UnicodeEncoding)) para representar caracteres e cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-121">.NET uses the UTF-16 encoding (represented by the [UnicodeEncoding](xref:System.Text.UnicodeEncoding) class) to represent characters and strings.</span></span> <span data-ttu-id="d1217-122">Aplicativos que segmentam o Common Language Runtime e usam codificadores para mapear representações de caracteres Unicode com suporte pelo common language runtime para outros esquemas de codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-122">Applications that target the common language runtime use encoders to map Unicode character representations supported by the common language runtime to other encoding schemes.</span></span> <span data-ttu-id="d1217-123">Eles usam decodificadores para mapear caracteres de codificações não Unicode para Unicode.</span><span class="sxs-lookup"><span data-stu-id="d1217-123">They use decoders to map characters from non-Unicode encodings to Unicode.</span></span>

<span data-ttu-id="d1217-124">Este tópico é composto pelas seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="d1217-124">This topic consists of the following sections:</span></span>

* [<span data-ttu-id="d1217-125">Codificações no .NET</span><span class="sxs-lookup"><span data-stu-id="d1217-125">Encodings in .NET</span></span>](#encodings-in-net)

* [<span data-ttu-id="d1217-126">Selecionando uma classe de codificação</span><span class="sxs-lookup"><span data-stu-id="d1217-126">Selecting an encoding class</span></span>](#selecting-an-encoding-class)

* [<span data-ttu-id="d1217-127">Usando um objeto de codificação</span><span class="sxs-lookup"><span data-stu-id="d1217-127">Using an encoding object</span></span>](#using-an-encoding-object)

* [<span data-ttu-id="d1217-128">Escolhendo uma estratégia de fallback</span><span class="sxs-lookup"><span data-stu-id="d1217-128">Choosing a fallback strategy</span></span>](#choosing-a-fallback-strategy)

* [<span data-ttu-id="d1217-129">Implementando uma estratégia de fallback personalizada</span><span class="sxs-lookup"><span data-stu-id="d1217-129">Implementing a custom fallback strategy</span></span>](#implementing-a-custom-fallback-strategy)

## <a name="encodings-in-net"></a><span data-ttu-id="d1217-130">Codificações no .NET</span><span class="sxs-lookup"><span data-stu-id="d1217-130">Encodings in .NET</span></span>

<span data-ttu-id="d1217-131">Todos as classes de codificação de caracteres no .NET são herdadas da classe [System.Text.Encoding](xref:System.Text.Encoding), uma classe abstrata que define a funcionalidade comum a todas as codificações de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-131">All character encoding classes in .NET inherit from the [System.Text.Encoding](xref:System.Text.Encoding) class, which is an abstract class that defines the functionality common to all character encodings.</span></span> <span data-ttu-id="d1217-132">Para acessar os objetos de codificação individuais implementados no .NET, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d1217-132">To access the individual encoding objects implemented in .NET, do the following:</span></span>

* <span data-ttu-id="d1217-133">Usar propriedades estáticas da classe [Encoding](xref:System.Text.Encoding), que retornam objetos que representam as codificações de caracteres padrão disponíveis no .NET (ASCII, UTF-7, UTF-8, UTF-16 e UTF-32).</span><span class="sxs-lookup"><span data-stu-id="d1217-133">Use the static properties of the [Encoding](xref:System.Text.Encoding) class, which return objects that represent the standard character encodings available in .NET (ASCII, UTF-7, UTF-8, UTF-16, and UTF-32).</span></span> <span data-ttu-id="d1217-134">Por exemplo, a propriedade [Encoding. Unicode](xref:System.Text.Encoding.Unicode) retorna um objeto [UnicodeEncoding](xref:System.Text.UnicodeEncoding).</span><span class="sxs-lookup"><span data-stu-id="d1217-134">For example, the [Encoding.Unicode](xref:System.Text.Encoding.Unicode) property returns a [UnicodeEncoding](xref:System.Text.UnicodeEncoding) object.</span></span> <span data-ttu-id="d1217-135">Cada objeto usa o fallback de substituição para lidar com cadeias de caracteres que ele não consegue codificar e bytes que ele não consegue decodificar.</span><span class="sxs-lookup"><span data-stu-id="d1217-135">Each object uses replacement fallback to handle strings that it cannot encode and bytes that it cannot decode.</span></span> <span data-ttu-id="d1217-136">(Para obter mais informações, consulte a seção [Fallback de substituição](#replacement-fallback).)</span><span class="sxs-lookup"><span data-stu-id="d1217-136">(For more information, see the [Replacement fallback](#replacement-fallback) section.)</span></span>

* <span data-ttu-id="d1217-137">Chame o construtor de classe da codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-137">Call the encoding's class constructor.</span></span> <span data-ttu-id="d1217-138">A instância de objetos para as codificações ASCII, UTF-7, UTF-8, UTF-16 e UTF-32 podem ser criadas dessa forma.</span><span class="sxs-lookup"><span data-stu-id="d1217-138">Objects for the ASCII, UTF-7, UTF-8, UTF-16, and UTF-32 encodings can be instantiated in this way.</span></span> <span data-ttu-id="d1217-139">Por padrão, cada objeto usa fallback de substituição para manipular as cadeias de caracteres que ele não consegue codificar e bytes que ele não consegue decodificar, mas, em vez disso, você pode especificar que uma exceção seja gerada.</span><span class="sxs-lookup"><span data-stu-id="d1217-139">By default, each object uses replacement fallback to handle strings that it cannot encode and bytes that it cannot decode, but you can specify that an exception should be thrown instead.</span></span> <span data-ttu-id="d1217-140">(Para obter mais informações, consulte as seções [Fallback de substituição](#replacement-fallback) e [Fallback de exceção](#exception-fallback).)</span><span class="sxs-lookup"><span data-stu-id="d1217-140">(For more information, see the [Replacement fallback](#replacement-fallback) and [Exception fallback](#exception-fallback) sections.)</span></span>

* <span data-ttu-id="d1217-141">Chame o construtor [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) e passe por ele um inteiro que represente a codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-141">Call the [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) constructor and pass it an integer that represents the encoding.</span></span> <span data-ttu-id="d1217-142">Os objetos de codificação padrão usam o fallback de substituição e a página de código e o DBCS (conjunto de caracteres de dois bytes) que codificam objetos usam o fallback que melhor se ajusta para manipular cadeias de caracteres que eles não conseguem codificar e bytes que eles não conseguem decodificar.</span><span class="sxs-lookup"><span data-stu-id="d1217-142">Standard encoding objects use replacement fallback, and code page and double-byte character set (DBCS) encoding objects use best-fit fallback to handle strings that they cannot encode and bytes that they cannot decode.</span></span> <span data-ttu-id="d1217-143">(Para obter mais informações, consulte a seção [Fallback de melhor ajuste](#best-fit-fallback).)</span><span class="sxs-lookup"><span data-stu-id="d1217-143">(For more information, see the [Best-Fit fallback](#best-fit-fallback) section.)</span></span>

* <span data-ttu-id="d1217-144">Chame o método [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)), que retorna qualquer padrão, página de código ou codificação DBCS disponível no .NET.</span><span class="sxs-lookup"><span data-stu-id="d1217-144">Call the [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)) method, which returns any standard, code page, or DBCS encoding available in .NET.</span></span> <span data-ttu-id="d1217-145">As sobrecargas permitem especificar um objeto de fallback para o codificador e o decodificador.</span><span class="sxs-lookup"><span data-stu-id="d1217-145">Overloads let you specify a fallback object for both the encoder and the decoder.</span></span>

> [!NOTE]
> <span data-ttu-id="d1217-146">O padrão Unicode atribui um ponto de código (um número) e um nome a cada caractere em todos os scripts com suporte.</span><span class="sxs-lookup"><span data-stu-id="d1217-146">The Unicode Standard assigns a code point (a number) and a name to each character in every supported script.</span></span> <span data-ttu-id="d1217-147">Por exemplo, o caractere "A" é representado pelo ponto de código de U+0041 e o nome "LETRA MAIÚSCULA LATINA A".</span><span class="sxs-lookup"><span data-stu-id="d1217-147">For example, the character "A" is represented by the code point U+0041 and the name "LATIN CAPITAL LETTER A".</span></span> <span data-ttu-id="d1217-148">As codificações UTF (Unicode Transformation Format) definem maneiras de codificar esse ponto de código em uma sequência de um ou mais bytes.</span><span class="sxs-lookup"><span data-stu-id="d1217-148">The Unicode Transformation Format (UTF) encodings define ways to encode that code point into a sequence of one or more bytes.</span></span> <span data-ttu-id="d1217-149">Um esquema de codificação Unicode simplifica o desenvolvimento de aplicativos prontos para o mundo, porque ele permite que qualquer conjunto de caracteres sejam representados em uma única codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-149">A Unicode encoding scheme simplifies world-ready application development because it allows characters from any character set to be represented in a single encoding.</span></span> <span data-ttu-id="d1217-150">Os desenvolvedores de aplicativos não precisam mais controlar o esquema de codificação usado para gerar caracteres para um idioma específico ou sistema de gravação e os dados podem ser compartilhados entre sistemas internacionalmente sem serem corrompidos.</span><span class="sxs-lookup"><span data-stu-id="d1217-150">Application developers no longer have to keep track of the encoding scheme that was used to produce characters for a specific language or writing system, and data can be shared among systems internationally without being corrupted.</span></span>
>
>  <span data-ttu-id="d1217-151">O .NET dá suporte a três codificações definidas pelo padrão Unicode: UTF-8, UTF-16 e UTF-32.</span><span class="sxs-lookup"><span data-stu-id="d1217-151">.NET supports three encodings defined by the Unicode standard: UTF-8, UTF-16, and UTF-32.</span></span> <span data-ttu-id="d1217-152">Para obter mais informações, consulte Padrão Unicode na página inicial [Unicode](http://www.unicode.org/).</span><span class="sxs-lookup"><span data-stu-id="d1217-152">For more information, see The Unicode Standard at the [Unicode](http://www.unicode.org/) home page.</span></span>
 
<span data-ttu-id="d1217-153">O .NET dá suporte aos sistemas de codificação de caracteres listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="d1217-153">.NET supports the character encoding systems listed in the following table.</span></span>

<span data-ttu-id="d1217-154">Codificando</span><span class="sxs-lookup"><span data-stu-id="d1217-154">Encoding</span></span> | <span data-ttu-id="d1217-155">Classe</span><span class="sxs-lookup"><span data-stu-id="d1217-155">Class</span></span> | <span data-ttu-id="d1217-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1217-156">Description</span></span> | <span data-ttu-id="d1217-157">Vantagens/desvantagens</span><span class="sxs-lookup"><span data-stu-id="d1217-157">Advantages/disadvantages</span></span>
-------- | ----- | ----------- | ------------------------ 
<span data-ttu-id="d1217-158">ASCII</span><span class="sxs-lookup"><span data-stu-id="d1217-158">ASCII</span></span> | [<span data-ttu-id="d1217-159">ASCIIEncoding</span><span class="sxs-lookup"><span data-stu-id="d1217-159">ASCIIEncoding</span></span>](xref:System.Text.ASCIIEncoding) | <span data-ttu-id="d1217-160">Codifica um intervalo limitado de caracteres usando os menores sete bits de um byte.</span><span class="sxs-lookup"><span data-stu-id="d1217-160">Encodes a limited range of characters by using the lower seven bits of a byte.</span></span> | <span data-ttu-id="d1217-161">Como essa codificação só dá suporte a valores de caracteres de U+0000 a U+007F, na maioria dos casos, ela é inadequada para aplicativos internacionalizados.</span><span class="sxs-lookup"><span data-stu-id="d1217-161">Because this encoding only supports character values from U+0000 through U+007F, in most cases it is inadequate for internationalized applications.</span></span>
<span data-ttu-id="d1217-162">UTF-7</span><span class="sxs-lookup"><span data-stu-id="d1217-162">UTF-7</span></span> | [<span data-ttu-id="d1217-163">UTF7Encoding</span><span class="sxs-lookup"><span data-stu-id="d1217-163">UTF7Encoding</span></span>](xref:System.Text.UTF7Encoding) | <span data-ttu-id="d1217-164">Representa caracteres como sequências de caracteres ASCII de 7 bits.</span><span class="sxs-lookup"><span data-stu-id="d1217-164">Represents characters as sequences of 7-bit ASCII characters.</span></span> <span data-ttu-id="d1217-165">Caracteres Unicode não ASCII são representados por uma sequência de escape de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="d1217-165">Non-ASCII Unicode characters are represented by an escape sequence of ASCII characters.</span></span> | <span data-ttu-id="d1217-166">O UTF-7 dá suporte a protocolos como email e protocolos de grupos de notícias.</span><span class="sxs-lookup"><span data-stu-id="d1217-166">UTF-7 supports protocols such as e-mail and newsgroup protocols.</span></span> <span data-ttu-id="d1217-167">No entanto, o UTF-7 não é particularmente seguro ou robusto.</span><span class="sxs-lookup"><span data-stu-id="d1217-167">However, UTF-7 is not particularly secure or robust.</span></span> <span data-ttu-id="d1217-168">Em alguns casos, alterar um bit pode alterar radicalmente a interpretação de toda uma cadeia de caracteres UTF-7.</span><span class="sxs-lookup"><span data-stu-id="d1217-168">In some cases, changing one bit can radically alter the interpretation of an entire UTF-7 string.</span></span> <span data-ttu-id="d1217-169">Em outros casos, diferentes cadeias de caracteres UTF-7 podem codificar o mesmo texto.</span><span class="sxs-lookup"><span data-stu-id="d1217-169">In other cases, different UTF-7 strings can encode the same text.</span></span> <span data-ttu-id="d1217-170">Para as sequências que incluem caracteres não ASCII, o UTF-7 requer mais espaço do que o UTF-8 e a codificação/decodificação é mais lenta.</span><span class="sxs-lookup"><span data-stu-id="d1217-170">For sequences that include non-ASCII characters, UTF-7 requires more space than UTF-8, and encoding/decoding is slower.</span></span> <span data-ttu-id="d1217-171">Consequentemente, você deve usar o UTF-8 em vez do UTF-7, se possível.</span><span class="sxs-lookup"><span data-stu-id="d1217-171">Consequently, you should use UTF-8 instead of UTF-7 if possible.</span></span>
<span data-ttu-id="d1217-172">UTF-8</span><span class="sxs-lookup"><span data-stu-id="d1217-172">UTF-8</span></span> | [<span data-ttu-id="d1217-173">UTF8Encoding</span><span class="sxs-lookup"><span data-stu-id="d1217-173">UTF8Encoding</span></span>](xref:System.Text.UTF8Encoding) | <span data-ttu-id="d1217-174">Representa cada ponto de código Unicode como uma sequência de um a quatro bytes.</span><span class="sxs-lookup"><span data-stu-id="d1217-174">Represents each Unicode code point as a sequence of one to four bytes.</span></span> | <span data-ttu-id="d1217-175">O UTF-8 dá suporte a tamanhos de dados de 8 bits e funciona bem com muitos sistemas operacionais existentes.</span><span class="sxs-lookup"><span data-stu-id="d1217-175">UTF-8 supports 8-bit data sizes and works well with many existing operating systems.</span></span> <span data-ttu-id="d1217-176">Para o intervalo de caracteres ASCII, o UTF-8 é idêntico à codificação ASCII e permite um conjunto mais amplo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-176">For the ASCII range of characters, UTF-8 is identical to ASCII encoding and allows a broader set of characters.</span></span> <span data-ttu-id="d1217-177">No entanto, para scripts CJK (chinês-japonês-coreano), o UTF-8 pode exigir três bytes para cada caractere e pode eventualmente gerar tamanhos de dados maiores do que o UTF-16.</span><span class="sxs-lookup"><span data-stu-id="d1217-177">However, for Chinese-Japanese-Korean (CJK) scripts, UTF-8 can require three bytes for each character, and can potentially cause larger data sizes than UTF-16.</span></span> <span data-ttu-id="d1217-178">Observe que, às vezes, a quantidade de dados ASCII, como tags HTML, justifica o tamanho maior do intervalo CJK.</span><span class="sxs-lookup"><span data-stu-id="d1217-178">Note that sometimes the amount of ASCII data, such as HTML tags, justifies the increased size for the CJK range.</span></span>
<span data-ttu-id="d1217-179">UTF-16</span><span class="sxs-lookup"><span data-stu-id="d1217-179">UTF-16</span></span> | [<span data-ttu-id="d1217-180">UnicodeEncoding</span><span class="sxs-lookup"><span data-stu-id="d1217-180">UnicodeEncoding</span></span>](xref:System.Text.UnicodeEncoding) | <span data-ttu-id="d1217-181">Representa cada ponto de código Unicode como uma sequência de um a dois inteiros de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="d1217-181">Represents each Unicode code point as a sequence of one or two 16-bit integers.</span></span> <span data-ttu-id="d1217-182">Os caracteres Unicode mais comuns exigem apenas um ponto de código UTF-16, embora os caracteres suplementares Unicode (U+10000 e maiores) exigem dois pontos de código UTF-16 alternativos.</span><span class="sxs-lookup"><span data-stu-id="d1217-182">Most common Unicode characters require only one UTF-16 code point, although Unicode supplementary characters (U+10000 and greater) require two UTF-16 surrogate code points.</span></span> <span data-ttu-id="d1217-183">Há suporte para as ordens de byte little endian e big endian.</span><span class="sxs-lookup"><span data-stu-id="d1217-183">Both little-endian and big-endian byte orders are supported.</span></span> | <span data-ttu-id="d1217-184">A codificação UTF-16 é usada pelo Common Language Runtime para representar os valores Char e String e é usada pelo sistema operacional Windows para representar valores WCHAR.</span><span class="sxs-lookup"><span data-stu-id="d1217-184">UTF-16 encoding is used by the common language runtime to represent Char and String values, and it is used by the Windows operating system to represent WCHAR values.</span></span>
<span data-ttu-id="d1217-185">UTF-32</span><span class="sxs-lookup"><span data-stu-id="d1217-185">UTF-32</span></span> | [<span data-ttu-id="d1217-186">UTF32Encoding</span><span class="sxs-lookup"><span data-stu-id="d1217-186">UTF32Encoding</span></span>](xref:System.Text.UTF32Encoding) | <span data-ttu-id="d1217-187">Representa cada ponto de código Unicode como um inteiro de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d1217-187">Represents each Unicode code point as a 32-bit integer.</span></span> <span data-ttu-id="d1217-188">Há suporte para as ordens de byte little endian e big endian.</span><span class="sxs-lookup"><span data-stu-id="d1217-188">Both little-endian and big-endian byte orders are supported.</span></span> | <span data-ttu-id="d1217-189">A codificação UTF-32 é usada quando aplicativos desejam evitar o comportamento do ponto de código alternativo de codificação UTF-16 em sistemas operacionais para os quais o espaço codificado é muito importante.</span><span class="sxs-lookup"><span data-stu-id="d1217-189">UTF-32 encoding is used when applications want to avoid the surrogate code point behavior of UTF-16 encoding on operating systems for which encoded space is too important.</span></span> <span data-ttu-id="d1217-190">Glifos únicos renderizados em uma tela ainda podem ser codificados com mais de um caractere UTF-32.</span><span class="sxs-lookup"><span data-stu-id="d1217-190">Single glyphs rendered on a display can still be encoded with more than one UTF-32 character.</span></span>

<span data-ttu-id="d1217-191">Essas codificações permitem que você trabalhe com caracteres Unicode, bem como com codificações mais comumente usadas em aplicativos herdados.</span><span class="sxs-lookup"><span data-stu-id="d1217-191">These encodings enable you to work with Unicode characters as well as with encodings that are most commonly used in legacy applications.</span></span> <span data-ttu-id="d1217-192">Além disso, você pode criar uma codificação personalizada definindo uma classe que deriva de [Encoding](xref:System.Text.Encoding) e substituindo seus membros.</span><span class="sxs-lookup"><span data-stu-id="d1217-192">In addition, you can create a custom encoding by defining a class that derives from [Encoding](xref:System.Text.Encoding) and overriding its members.</span></span>

> [!NOTE]
> <span data-ttu-id="d1217-193">Por padrão, o .NET Core não disponibiliza nenhuma codificação de página de código diferente de página de código 28591 e das codificações Unicode, como UTF-8 e UTF-16.</span><span class="sxs-lookup"><span data-stu-id="d1217-193">By default, .NET Core does not make available any code page encodings other than code page 28591 and the Unicode encodings, such as UTF-8 and UTF-16.</span></span> <span data-ttu-id="d1217-194">No entanto, você pode adicionar as codificações de página de código encontradas em aplicativos do Windows padrão que direcionam o .NET Framework ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d1217-194">However, you can add the code page encodings found in standard Windows apps that target the .NET Framework to your app.</span></span> <span data-ttu-id="d1217-195">Para obter informações completas, consulte o tópico [EncodingProvider](xref:System.Text.EncodingProvider).</span><span class="sxs-lookup"><span data-stu-id="d1217-195">For complete information, see the [EncodingProvider](xref:System.Text.EncodingProvider) topic.</span></span> 

## <a name="selecting-an-encoding-class"></a><span data-ttu-id="d1217-196">Selecionando uma classe de codificação</span><span class="sxs-lookup"><span data-stu-id="d1217-196">Selecting an Encoding class</span></span>

<span data-ttu-id="d1217-197">Se você tiver a oportunidade de escolher a codificação a ser usada pelo seu aplicativo, você deverá usar a codificação Unicode, preferencialmente [UTF8Encoding](xref:System.Text.UTF8Encoding) ou [UnicodeEncoding](xref:System.Text.UnicodeEncoding).</span><span class="sxs-lookup"><span data-stu-id="d1217-197">If you have the opportunity to choose the encoding to be used by your application, you should use a Unicode encoding, preferably either [UTF8Encoding](xref:System.Text.UTF8Encoding) or [UnicodeEncoding](xref:System.Text.UnicodeEncoding).</span></span> <span data-ttu-id="d1217-198">(O .NET também dá suporte a uma terceira codificação Unicode, [UTF32Encoding](xref:System.Text.UTF32Encoding).)</span><span class="sxs-lookup"><span data-stu-id="d1217-198">(.NET also supports a third Unicode encoding, [UTF32Encoding](xref:System.Text.UTF32Encoding).)</span></span> 

<span data-ttu-id="d1217-199">Se você estiver planejando usar uma codificação ASCII ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)), escolha [UTF8Encoding](xref:System.Text.UTF8Encoding) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d1217-199">If you are planning to use an ASCII encoding ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)), choose [UTF8Encoding](xref:System.Text.UTF8Encoding) instead.</span></span> <span data-ttu-id="d1217-200">As duas codificações são idênticas para o conjunto de caracteres ASCII, mas o [UTF8Encoding](xref:System.Text.UTF8Encoding) tem as seguintes vantagens:</span><span class="sxs-lookup"><span data-stu-id="d1217-200">The two encodings are identical for the ASCII character set, but [UTF8Encoding](xref:System.Text.UTF8Encoding) has the following advantages:</span></span> 

* <span data-ttu-id="d1217-201">Ele pode representar todos os caracteres Unicode, enquanto o [ASCIIEncoding](xref:System.Text.ASCIIEncoding) dá suporte apenas aos valores de caracteres Unicode entre U+0000 e U+007F.</span><span class="sxs-lookup"><span data-stu-id="d1217-201">It can represent every Unicode character, whereas [ASCIIEncoding](xref:System.Text.ASCIIEncoding) supports only the Unicode character values between U+0000 and U+007F.</span></span>

* <span data-ttu-id="d1217-202">Ele fornece detecção de erros e melhor segurança.</span><span class="sxs-lookup"><span data-stu-id="d1217-202">It provides error detection and better security.</span></span>

* <span data-ttu-id="d1217-203">Ele foi ajustado para ser o mais rápido possível e deve ser mais rápido do que qualquer outra codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-203">It has been tuned to be as fast as possible and should be faster than any other encoding.</span></span> <span data-ttu-id="d1217-204">Mesmo para o conteúdo totalmente ASCII, as operações executadas com o [UTF8Encoding](xref:System.Text.UTF8Encoding) são mais rápidas que as operações executadas com o [ASCIIEncoding](xref:System.Text.ASCIIEncoding).</span><span class="sxs-lookup"><span data-stu-id="d1217-204">Even for content that is entirely ASCII, operations performed with [UTF8Encoding](xref:System.Text.UTF8Encoding) are faster than operations performed with [ASCIIEncoding](xref:System.Text.ASCIIEncoding).</span></span>

<span data-ttu-id="d1217-205">Você deve considerar usar o [ASCIIEncoding](xref:System.Text.ASCIIEncoding) apenas para aplicativos herdados.</span><span class="sxs-lookup"><span data-stu-id="d1217-205">You should consider using [ASCIIEncoding](xref:System.Text.ASCIIEncoding) only for legacy applications.</span></span> <span data-ttu-id="d1217-206">No entanto, mesmo para aplicativos herdados, o [UTF8Encoding](xref:System.Text.UTF8Encoding) pode ser uma escolha melhor pelos seguintes motivos (supondo as configurações padrão):</span><span class="sxs-lookup"><span data-stu-id="d1217-206">However, even for legacy applications, [UTF8Encoding](xref:System.Text.UTF8Encoding) might be a better choice for the following reasons (assuming default settings):</span></span>

* <span data-ttu-id="d1217-207">Se seu aplicativo tiver conteúdo que não é estritamente ASCII e codificá-lo com o [ASCIIEncoding](xref:System.Text.ASCIIEncoding), cada caractere não ASCII codificará como um ponto de interrogação (?).</span><span class="sxs-lookup"><span data-stu-id="d1217-207">If your application has content that is not strictly ASCII and encodes it with [ASCIIEncoding](xref:System.Text.ASCIIEncoding), each non-ASCII character encodes as a question mark (?).</span></span> <span data-ttu-id="d1217-208">Se o aplicativo decodificar esses dados, as informações serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="d1217-208">If the application then decodes this data, the information is lost.</span></span>


* <span data-ttu-id="d1217-209">Se seu aplicativo tiver conteúdo que não é estritamente ASCII e codificá-lo com o [UTF8Encoding](xref:System.Text.UTF8Encoding), o resultado parecerá ininteligível se interpretado como ASCII.</span><span class="sxs-lookup"><span data-stu-id="d1217-209">If your application has content that is not strictly ASCII and encodes it with [UTF8Encoding](xref:System.Text.UTF8Encoding), the result seems unintelligible if interpreted as ASCII.</span></span> <span data-ttu-id="d1217-210">No entanto, se o aplicativo usar um decodificador de UTF-8 para decodificar esses dados, os dados executarão uma viagem de ida e volta com êxito.</span><span class="sxs-lookup"><span data-stu-id="d1217-210">However, if the application then uses a UTF-8 decoder to decode this data, the data performs a round trip successfully.</span></span>

<span data-ttu-id="d1217-211">Em um aplicativo Web, os caracteres enviados ao cliente em resposta a uma solicitação da Web devem refletir a codificação usada no cliente.</span><span class="sxs-lookup"><span data-stu-id="d1217-211">In a web application, characters sent to the client in response to a web request should reflect the encoding used on the client.</span></span> <span data-ttu-id="d1217-212">Na maioria dos casos, você deve definir a propriedades [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) como o valor retornado pela propriedade [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) para exibir texto na codificação que o usuário espera.</span><span class="sxs-lookup"><span data-stu-id="d1217-212">In most cases, you should set the [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) property to the value returned by the [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) property to display text in the encoding that the user expects.</span></span>

## <a name="using-an-encoding-object"></a><span data-ttu-id="d1217-213">Usando um objeto de codificação</span><span class="sxs-lookup"><span data-stu-id="d1217-213">Using an encoding object</span></span>

<span data-ttu-id="d1217-214">Um codificador converte uma cadeia de caracteres (mais comumente, caracteres Unicode) em seu equivalente numérico (byte).</span><span class="sxs-lookup"><span data-stu-id="d1217-214">An encoder converts a string of characters (most commonly, Unicode characters) to its numeric (byte) equivalent.</span></span> <span data-ttu-id="d1217-215">Por exemplo, você pode usar um codificador ASCII para converter caracteres Unicode em ASCII para que eles possam ser exibidos no console.</span><span class="sxs-lookup"><span data-stu-id="d1217-215">For example, you might use an ASCII encoder to convert Unicode characters to ASCII so that they can be displayed at the console.</span></span> <span data-ttu-id="d1217-216">Para executar a conversão, você chama o método [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])).</span><span class="sxs-lookup"><span data-stu-id="d1217-216">To perform the conversion, you call the [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])) method.</span></span> <span data-ttu-id="d1217-217">Se você desejar determinar quantos bytes são necessários para armazenar os caracteres codificados antes de executar a codificação, você poderá chamar o método [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])).</span><span class="sxs-lookup"><span data-stu-id="d1217-217">If you want to determine how many bytes are needed to store the encoded characters before performing the encoding, you can call the [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])) method.</span></span>

<span data-ttu-id="d1217-218">O exemplo a seguir usa uma matriz de byte único para codificar cadeias de caracteres em duas operações separadas.</span><span class="sxs-lookup"><span data-stu-id="d1217-218">The following example uses a single byte array to encode strings in two separate operations.</span></span> <span data-ttu-id="d1217-219">Ela mantém um índice que indica a posição inicial na matriz de bytes para o próximo conjunto de bytes codificados em ASCII.</span><span class="sxs-lookup"><span data-stu-id="d1217-219">It maintains an index that indicates the starting position in the byte array for the next set of ASCII-encoded bytes.</span></span> <span data-ttu-id="d1217-220">Ela chama o método [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) para garantir que a matriz de bytes seja grande o suficiente para acomodar a cadeia de caracteres codificada.</span><span class="sxs-lookup"><span data-stu-id="d1217-220">It calls the [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) method to ensure that the byte array is large enough to accommodate the encoded string.</span></span> <span data-ttu-id="d1217-221">Depois, ela chama o método [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) para codificar caracteres na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-221">It then calls the [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) method to encode the characters in the string.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings= { "This is the first sentence. ", 
                          "This is the second sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;

      // Create array of adequate size.
      byte[] bytes = new byte[49];
      // Create index for current position of array.
      int index = 0;

      Console.WriteLine("Strings to encode:");
      foreach (var stringValue in strings) {
         Console.WriteLine("   {0}", stringValue);

         int count = asciiEncoding.GetByteCount(stringValue);
         if (count + index >=  bytes.Length)
            Array.Resize(ref bytes, bytes.Length + 50);

         int written = asciiEncoding.GetBytes(stringValue, 0, 
                                              stringValue.Length, 
                                              bytes, index);    

         index = index + written; 
      } 
      Console.WriteLine("\nEncoded bytes:");
      Console.WriteLine("{0}", ShowByteValues(bytes, index));
      Console.WriteLine();

      // Decode Unicode byte array to a string.
      string newString = asciiEncoding.GetString(bytes, 0, index);
      Console.WriteLine("Decoded: {0}", newString);
   }

   private static string ShowByteValues(byte[] bytes, int last ) 
   {
      string returnString = "   ";
      for (int ctr = 0; ctr <= last - 1; ctr++) {
         if (ctr % 20 == 0)
            returnString += "\n   ";
         returnString += String.Format("{0:X2} ", bytes[ctr]);
      }
      return returnString;
   }
}
// The example displays the following output:
//       Strings to encode:
//          This is the first sentence.
//          This is the second sentence.
//       
//       Encoded bytes:
//       
//          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
//          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
//       
//       Decoded: This is the first sentence. This is the second sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII

      ' Create array of adequate size.
      Dim bytes(50) As Byte
      ' Create index for current position of array.
      Dim index As Integer = 0

      Console.WriteLine("Strings to encode:")
      For Each stringValue In strings
         Console.WriteLine("   {0}", stringValue)

         Dim count As Integer = asciiEncoding.GetByteCount(stringValue)
         If count + index >=  bytes.Length Then
            Array.Resize(bytes, bytes.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetBytes(stringValue, 0, 
                                                         stringValue.Length, 
                                                         bytes, index)    

         index = index + written 
      Next 
      Console.WriteLine()
      Console.WriteLine("Encoded bytes:")
      Console.WriteLine("{0}", ShowByteValues(bytes, index))
      Console.WriteLine()

      ' Decode Unicode byte array to a string.
      Dim newString As String = asciiEncoding.GetString(bytes, 0, index)
      Console.WriteLine("Decoded: {0}", newString)
   End Sub

   Private Function ShowByteValues(bytes As Byte(), last As Integer) As String
      Dim returnString As String = "   "
      For ctr As Integer = 0 To last - 1
         If ctr Mod 20 = 0 Then returnString += vbCrLf + "   "
         returnString += String.Format("{0:X2} ", bytes(ctr))
      Next
      Return returnString
   End Function
End Module
' The example displays the following output:
'       Strings to encode:
'          This is the first sentence.
'          This is the second sentence.
'       
'       Encoded bytes:
'       
'          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
'          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
'       
'       Decoded: This is the first sentence. This is the second sentence.
```

<span data-ttu-id="d1217-222">Um decodificador converte uma matriz de bytes que reflete uma codificação de caracteres específica em um conjunto de caracteres, seja em uma matriz de caracteres ou em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-222">A decoder converts a byte array that reflects a particular character encoding into a set of characters, either in a character array or in a string.</span></span> <span data-ttu-id="d1217-223">Para decodificar uma matriz de bytes em uma matriz de caracteres, chame o método [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="d1217-223">To decode a byte array into a character array, you call the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) method.</span></span> <span data-ttu-id="d1217-224">Para decodificar uma matriz de bytes em uma cadeia de caracteres, chame o método [GetString](xref:System.Text.Encoding.GetString(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="d1217-224">To decode a byte array into a string, you call the [GetString](xref:System.Text.Encoding.GetString(System.Byte[])) method.</span></span> <span data-ttu-id="d1217-225">Se você desejar determinar quantos caracteres são necessários para armazenar os bytes decodificados antes de executar a decodificação, você poderá chamar o método [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="d1217-225">If you want to determine how many characters are needed to store the decoded bytes before performing the decoding, you can call the [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) method.</span></span>

<span data-ttu-id="d1217-226">O exemplo a seguir codifica três cadeias de caracteres e, em seguida, as decodifica em uma única matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-226">The following example encodes three strings and then decodes them into a single array of characters.</span></span> <span data-ttu-id="d1217-227">Ela mantém um índice que indica a posição inicial na matriz de bytes para o próximo conjunto de caracteres codificados.</span><span class="sxs-lookup"><span data-stu-id="d1217-227">It maintains an index that indicates the starting position in the character array for the next set of decoded characters.</span></span> <span data-ttu-id="d1217-228">Ela chama o método [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) para garantir que a matriz de caracteres seja grande o suficiente para acomodar todos os caracteres decodificados.</span><span class="sxs-lookup"><span data-stu-id="d1217-228">It calls the [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) method to ensure that the character array is large enough to accommodate all the decoded characters.</span></span> <span data-ttu-id="d1217-229">Depois, ela chama o método [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) para decodificar a matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="d1217-229">It then calls the [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method to decode the byte array.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings = { "This is the first sentence. ", 
                           "This is the second sentence. ",
                           "This is the third sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;
      // Array to hold encoded bytes.
      byte[] bytes;
      // Array to hold decoded characters.
      char[] chars = new char[50];
      // Create index for current position of character array.
      int index = 0;     

      foreach (var stringValue in strings) {
         Console.WriteLine("String to Encode: {0}", stringValue);
         // Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue);
         // Display the encoded bytes.
         Console.Write("Encoded bytes: ");
         for (int ctr = 0; ctr < bytes.Length; ctr++)
            Console.Write(" {0}{1:X2}", 
                          ctr % 20 == 0 ? Environment.NewLine : "", 
                          bytes[ctr]);
         Console.WriteLine();

         // Decode the bytes to a single character array.
         int count = asciiEncoding.GetCharCount(bytes);
         if (count + index >=  chars.Length)
            Array.Resize(ref chars, chars.Length + 50);

         int written = asciiEncoding.GetChars(bytes, 0, 
                                              bytes.Length, 
                                              chars, index);              
         index = index + written;
         Console.WriteLine();       
      }

      // Instantiate a single string containing the characters.
      string decodedString = new string(chars, 0, index - 1);
      Console.WriteLine("Decoded string: ");
      Console.WriteLine(decodedString);
   }
}
// The example displays the following output:
//    String to Encode: This is the first sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the second sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
//    65 6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the third sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    Decoded string:
//    This is the first sentence. This is the second sentence. This is the third sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. ",
                                  "This is the third sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII
      ' Array to hold encoded bytes.
      Dim bytes() As Byte
      ' Array to hold decoded characters.
      Dim chars(50) As Char
      ' Create index for current position of character array.
      Dim index As Integer     

      For Each stringValue In strings
         Console.WriteLine("String to Encode: {0}", stringValue)
         ' Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue)
         ' Display the encoded bytes.
         Console.Write("Encoded bytes: ")
         For ctr As Integer = 0 To bytes.Length - 1
            Console.Write(" {0}{1:X2}", If(ctr Mod 20 = 0, vbCrLf, ""), 
                                        bytes(ctr))
         Next         
         Console.WriteLine()

         ' Decode the bytes to a single character array.
         Dim count As Integer = asciiEncoding.GetCharCount(bytes)
         If count + index >=  chars.Length Then
            Array.Resize(chars, chars.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetChars(bytes, 0, 
                                                         bytes.Length, 
                                                         chars, index)              
         index = index + written
         Console.WriteLine()       
      Next

      ' Instantiate a single string containing the characters.
      Dim decodedString As New String(chars, 0, index - 1)
      Console.WriteLine("Decoded string: ")
      Console.WriteLine(decodedString)
   End Sub
End Module
' The example displays the following output:
'    String to Encode: This is the first sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the second sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
'    65 6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the third sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    Decoded string:
'    This is the first sentence. This is the second sentence. This is the third sentence.
```

<span data-ttu-id="d1217-230">Os métodos de codificação e decodificação de uma classe derivada de [Encoding](xref:System.Text.Encoding) foram criados para funcionar em um conjunto completo de dados; ou seja, todos os dados a serem codificados ou decodificados são fornecido em uma única chamada de método.</span><span class="sxs-lookup"><span data-stu-id="d1217-230">The encoding and decoding methods of a class derived from [Encoding](xref:System.Text.Encoding) are designed to work on a complete set of data; that is, all the data to be encoded or decoded is supplied in a single method call.</span></span> <span data-ttu-id="d1217-231">No entanto, em alguns casos, os dados estão disponíveis em um fluxo e os dados a serem codificados ou decodificados podem estar disponíveis somente em operações de leitura separadas.</span><span class="sxs-lookup"><span data-stu-id="d1217-231">However, in some cases, data is available in a stream, and the data to be encoded or decoded may be available only from separate read operations.</span></span> <span data-ttu-id="d1217-232">Isso requer a operação de codificação ou decodificação para lembrar qualquer estado salvo em sua invocação anterior.</span><span class="sxs-lookup"><span data-stu-id="d1217-232">This requires the encoding or decoding operation to remember any saved state from its previous invocation.</span></span> <span data-ttu-id="d1217-233">Métodos de classes derivados de [Encoder](xref:System.Text.Encoder) e [Decoder](xref:System.Text.Decoder) são capazes de lidar com as operações de codificação e decodificação que abrangem várias chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="d1217-233">Methods of classes derived from [Encoder](xref:System.Text.Encoder) and [Decoder](xref:System.Text.Decoder) are able to handle encoding and decoding operations that span multiple method calls.</span></span>

<span data-ttu-id="d1217-234">Um objeto [Encoder](xref:System.Text.Encoder) de uma determinada codificação está disponível na propriedade [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) dessa codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-234">An [Encoder](xref:System.Text.Encoder) object for a particular encoding is available from that encoding's [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) property.</span></span> <span data-ttu-id="d1217-235">Um objeto [Decoder](xref:System.Text.Decoder) da uma determinada codificação está disponível na propriedade [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) dessa codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-235">A [Decoder](xref:System.Text.Decoder) object for a particular encoding is available from that encoding's [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) property.</span></span> <span data-ttu-id="d1217-236">Para operações de decodificação, observe que as classes derivadas de [Decoder](xref:System.Text.Decoder) incluem um método [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)), mas elas não têm um método que corresponde a [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])).</span><span class="sxs-lookup"><span data-stu-id="d1217-236">For decoding operations, note that classes derived from [Decoder](xref:System.Text.Decoder) include a [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method, but they do not have a method that corresponds to [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])).</span></span>

<span data-ttu-id="d1217-237">O exemplo a seguir ilustra a diferença entre usar os métodos [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) e [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) para decodificar uma matriz de bytes Unicode.</span><span class="sxs-lookup"><span data-stu-id="d1217-237">The following example illustrates the difference between using the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) and [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) methods for decoding a Unicode byte array.</span></span> <span data-ttu-id="d1217-238">O exemplo codifica uma cadeia de caracteres que contém alguns caracteres Unicode em um arquivo e, em seguida, usa os dois métodos de decodificação para decodificá-los dez bytes por vez.</span><span class="sxs-lookup"><span data-stu-id="d1217-238">The example encodes a string that contains some Unicode characters to a file, and then uses the two decoding methods to decode them ten bytes at a time.</span></span> <span data-ttu-id="d1217-239">Como um par alternativo ocorre nos bytes décimo e décimo primeiro, ele é decodificado em chamadas de método separadas.</span><span class="sxs-lookup"><span data-stu-id="d1217-239">Because a surrogate pair occurs in the tenth and eleventh bytes, it is decoded in separate method calls.</span></span> <span data-ttu-id="d1217-240">Como mostra a saída, o método [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) não é capaz de decodificar corretamente os bytes e, em vez disso, os substitui por U+FFFD (CARACTERE DE SUBSTITUIÇÃO).</span><span class="sxs-lookup"><span data-stu-id="d1217-240">As the output shows, the [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) method is not able to correctly decode the bytes and instead replaces them with U+FFFD (REPLACEMENT CHARACTER).</span></span> <span data-ttu-id="d1217-241">Por outro lado, o método [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) é capaz de decodificar com êxito a matriz de bytes para obter a cadeia de caracteres original.</span><span class="sxs-lookup"><span data-stu-id="d1217-241">On the other hand, the [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) method is able to successfully decode the byte array to get the original string.</span></span>

```csharp
using System;
using System.IO;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Use default replacement fallback for invalid encoding.
      UnicodeEncoding enc = new UnicodeEncoding(true, false, false);

      // Define a string with various Unicode characters.
      string str1 = "AB YZ 19 \uD800\udc05 \u00e4"; 
      str1 += "Unicode characters. \u00a9 \u010C s \u0062\u0308"; 
      Console.WriteLine("Created original string...\n");

      // Convert string to byte array.                     
      byte[] bytes = enc.GetBytes(str1);

      FileStream fs = File.Create(@".\characters.bin");
      BinaryWriter bw = new BinaryWriter(fs);
      bw.Write(bytes);
      bw.Close();

      // Read bytes from file.
      FileStream fsIn = File.OpenRead(@".\characters.bin");
      BinaryReader br = new BinaryReader(fsIn);

      const int count = 10;            // Number of bytes to read at a time. 
      byte[] bytesRead = new byte[10]; // Buffer (byte array).
      int read;                        // Number of bytes actually read. 
      string str2 = String.Empty;      // Decoded string.

      // Try using Encoding object for all operations.
      do { 
         read = br.Read(bytesRead, 0, count);
         str2 += enc.GetString(bytesRead, 0, read); 
      } while (read == count);
      br.Close();
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...");
      CompareForEquality(str1, str2);
      Console.WriteLine();

      // Use Decoder for all operations.
      fsIn = File.OpenRead(@".\characters.bin");
      br = new BinaryReader(fsIn);
      Decoder decoder = enc.GetDecoder();
      char[] chars = new char[50];
      int index = 0;                   // Next character to write in array.
      int written = 0;                 // Number of chars written to array.
      do { 
         read = br.Read(bytesRead, 0, count);
         if (index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length) 
            Array.Resize(ref chars, chars.Length + 50);

         written = decoder.GetChars(bytesRead, 0, read, chars, index);
         index += written;                          
      } while (read == count);
      br.Close();            
      // Instantiate a string with the decoded characters.
      string str3 = new String(chars, 0, index); 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...");
      CompareForEquality(str1, str3); 
   }

   private static void CompareForEquality(string original, string decoded)
   {
      bool result = original.Equals(decoded);
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal));
      if (! result) {
         Console.WriteLine("Code points in original string:");
         foreach (var ch in original)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();

         Console.WriteLine("Code points in decoded string:");
         foreach (var ch in decoded)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Created original string...
//    
//    Decoded string using UnicodeEncoding.GetString()...
//    original = decoded: False
//    Code points in original string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    Code points in decoded string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    
//    Decoded string using UnicodeEncoding.Decoder.GetString()...
//    original = decoded: True
```

```vb
Imports System.IO
Imports System.Text

Module Example
   Public Sub Main()
      ' Use default replacement fallback for invalid encoding.
      Dim enc As New UnicodeEncoding(True, False, False)

      ' Define a string with various Unicode characters.
      Dim str1 As String = String.Format("AB YZ 19 {0}{1} {2}", 
                                         ChrW(&hD800), ChrW(&hDC05), ChrW(&h00e4))
      str1 += String.Format("Unicode characters. {0} {1} s {2}{3}", 
                            ChrW(&h00a9), ChrW(&h010C), ChrW(&h0062), ChrW(&h0308))
      Console.WriteLine("Created original string...")
      Console.WriteLine()

      ' Convert string to byte array.                     
      Dim bytes() As Byte = enc.GetBytes(str1)

      Dim fs As FileStream = File.Create(".\characters.bin")
      Dim bw As New BinaryWriter(fs)
      bw.Write(bytes)
      bw.Close()

      ' Read bytes from file.
      Dim fsIn As FileStream = File.OpenRead(".\characters.bin")
      Dim br As New BinaryReader(fsIn)

      Const count As Integer = 10      ' Number of bytes to read at a time. 
      Dim bytesRead(9) As Byte         ' Buffer (byte array).
      Dim read As Integer              ' Number of bytes actually read. 
      Dim str2 As String = ""          ' Decoded string.

      ' Try using Encoding object for all operations.
      Do 
         read = br.Read(bytesRead, 0, count)
         str2 += enc.GetString(bytesRead, 0, read) 
      Loop While read = count
      br.Close()
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...")
      CompareForEquality(str1, str2)
      Console.WriteLine()

      ' Use Decoder for all operations.
      fsIn = File.OpenRead(".\characters.bin")
      br = New BinaryReader(fsIn)
      Dim decoder As Decoder = enc.GetDecoder()
      Dim chars(50) As Char
      Dim index As Integer = 0         ' Next character to write in array.
      Dim written As Integer = 0       ' Number of chars written to array.
      Do 
         read = br.Read(bytesRead, 0, count)
         If index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length Then 
            Array.Resize(chars, chars.Length + 50)
         End If   
         written = decoder.GetChars(bytesRead, 0, read, chars, index)
         index += written                          
      Loop While read = count
      br.Close()            
      ' Instantiate a string with the decoded characters.
      Dim str3 As New String(chars, 0, index) 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...")
      CompareForEquality(str1, str3) 
   End Sub

   Private Sub CompareForEquality(original As String, decoded As String)
      Dim result As Boolean = original.Equals(decoded)
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal))
      If Not result Then
         Console.WriteLine("Code points in original string:")
         For Each ch In original
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()

         Console.WriteLine("Code points in decoded string:")
         For Each ch In decoded
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
' The example displays the following output:
'    Created original string...
'    
'    Decoded string using UnicodeEncoding.GetString()...
'    original = decoded: False
'    Code points in original string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    Code points in decoded string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    
'    Decoded string using UnicodeEncoding.Decoder.GetString()...
'    original = decoded: True
```

## <a name="choosing-a-fallback-strategy"></a><span data-ttu-id="d1217-242">Escolhendo uma estratégia de fallback</span><span class="sxs-lookup"><span data-stu-id="d1217-242">Choosing a fallback strategy</span></span>

<span data-ttu-id="d1217-243">Quando um método tenta codificar ou decodificar um caractere, mas não existe nenhum mapeamento, ele deve implementar uma estratégia de fallback que determine como o mapeamento com falha deva ser tratado.</span><span class="sxs-lookup"><span data-stu-id="d1217-243">When a method tries to encode or decode a character but no mapping exists, it must implement a fallback strategy that determines how the failed mapping should be handled.</span></span> <span data-ttu-id="d1217-244">Há três tipos de estratégias de fallback:</span><span class="sxs-lookup"><span data-stu-id="d1217-244">There are three types of fallback strategies:</span></span> 

* <span data-ttu-id="d1217-245">Fallback de melhor ajuste</span><span class="sxs-lookup"><span data-stu-id="d1217-245">Best-fit fallback</span></span>

* <span data-ttu-id="d1217-246">Fallback de substituição</span><span class="sxs-lookup"><span data-stu-id="d1217-246">Replacement fallback</span></span>

* <span data-ttu-id="d1217-247">Fallback de exceção</span><span class="sxs-lookup"><span data-stu-id="d1217-247">Exception fallback</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1217-248">Os problemas mais comuns em operações de codificação ocorrem quando um caractere Unicode não pode ser mapeado para uma determinada codificação de página de código.</span><span class="sxs-lookup"><span data-stu-id="d1217-248">The most common problems in encoding operations occur when a Unicode character cannot be mapped to a particular code page encoding.</span></span> <span data-ttu-id="d1217-249">Os problemas mais comuns em operações de decodificação ocorrem quando sequências de bytes inválidas não podem ser convertidas em caracteres Unicode válidos.</span><span class="sxs-lookup"><span data-stu-id="d1217-249">The most common problems in decoding operations occur when invalid byte sequences cannot be translated into valid Unicode characters.</span></span> <span data-ttu-id="d1217-250">Por esses motivos, você deve saber qual estratégia de fallback um objeto de codificação específico usa.</span><span class="sxs-lookup"><span data-stu-id="d1217-250">For these reasons, you should know which fallback strategy a particular encoding object uses.</span></span> <span data-ttu-id="d1217-251">Sempre que possível, você deve especificar a estratégia de fallback usada por um objeto de codificação quando você criar uma instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="d1217-251">Whenever possible, you should specify the fallback strategy used by an encoding object when you instantiate the object.</span></span>
 
### <a name="best-fit-fallback"></a><span data-ttu-id="d1217-252">Fallback de melhor ajuste</span><span class="sxs-lookup"><span data-stu-id="d1217-252">Best-fit fallback</span></span>

<span data-ttu-id="d1217-253">Quando um caractere não tiver uma correspondência exata na codificação de destino, o codificador pode tentar mapeá-lo para um caractere semelhante.</span><span class="sxs-lookup"><span data-stu-id="d1217-253">When a character does not have an exact match in the target encoding, the encoder can try to map it to a similar character.</span></span> <span data-ttu-id="d1217-254">(O fallback de melhor ajuste é sobretudo uma codificação em vez de um problema de decodificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-254">(Best-fit fallback is mostly an encoding rather than a decoding issue.</span></span> <span data-ttu-id="d1217-255">Há poucas páginas de código que contêm caracteres que não podem ser mapeados com êxito para Unicode.) O fallback de melhor ajuste é o padrão para a página de código e para codificações de conjuntos de caracteres recuperados pelas sobrecargas [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) e [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)).</span><span class="sxs-lookup"><span data-stu-id="d1217-255">There are very few code pages that contain characters that cannot be successfully mapped to Unicode.) Best-fit fallback is the default for code page and double-byte character set encodings that are retrieved by the [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) and [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)) overloads.</span></span>

> [!NOTE]
> <span data-ttu-id="d1217-256">Na teoria, as classes de codificação Unicode fornecidas no .NET ([UTF8Encoding](xref:System.Text.UTF8Encoding), [UnicodeEncoding](xref:System.Text.UnicodeEncoding) e [UTF32Encoding](xref:System.Text.UTF32Encoding)) dão suporte a todos os caracteres em cada conjunto de caracteres para que eles possam ser usados para eliminar problemas de fallback de melhor ajuste.</span><span class="sxs-lookup"><span data-stu-id="d1217-256">In theory, the Unicode encoding classes provided in .NET ([UTF8Encoding](xref:System.Text.UTF8Encoding), [UnicodeEncoding](xref:System.Text.UnicodeEncoding), and [UTF32Encoding](xref:System.Text.UTF32Encoding)) support every character in every character set, so they can be used to eliminate best-fit fallback issues.</span></span> 
 

<span data-ttu-id="d1217-257">As estratégias de melhor ajuste variam de acordo com as diferentes páginas de código e não são documentadas detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="d1217-257">Best-fit strategies vary for different code pages, and they are not documented in detail.</span></span> <span data-ttu-id="d1217-258">Por exemplo, para algumas páginas de código, caracteres latinos de largura inteira mapeiam para os caracteres latinos de meia largura mais comuns.</span><span class="sxs-lookup"><span data-stu-id="d1217-258">For example, for some code pages, full-width Latin characters map to the more common half-width Latin characters.</span></span> <span data-ttu-id="d1217-259">Para outras páginas de código, esse mapeamento não é feito.</span><span class="sxs-lookup"><span data-stu-id="d1217-259">For other code pages, this mapping is not made.</span></span> <span data-ttu-id="d1217-260">Mesmo em uma estratégia de melhor ajuste agressiva, não há nenhum ajuste imaginável para alguns caracteres em algumas codificações.</span><span class="sxs-lookup"><span data-stu-id="d1217-260">Even under an aggressive best-fit strategy, there is no imaginable fit for some characters in some encodings.</span></span> <span data-ttu-id="d1217-261">Por exemplo, um ideograma chinês tem nenhum mapeamento razoável para a página de código 1252.</span><span class="sxs-lookup"><span data-stu-id="d1217-261">For example, a Chinese ideograph has no reasonable mapping to code page 1252.</span></span> <span data-ttu-id="d1217-262">Nesse caso, é usada uma cadeia de caracteres de substituição.</span><span class="sxs-lookup"><span data-stu-id="d1217-262">In this case, a replacement string is used.</span></span> <span data-ttu-id="d1217-263">Por padrão, essa cadeia de caracteres é apenas um PONTO DE INTERROGAÇÃO (U+003F).</span><span class="sxs-lookup"><span data-stu-id="d1217-263">By default, this string is just a single QUESTION MARK (U+003F).</span></span>

<span data-ttu-id="d1217-264">O exemplo a seguir usa a página de código 1252 (a página de código do Windows para idiomas da Europa Ocidental) para ilustrar o mapeamento de melhor ajuste e suas desvantagens.</span><span class="sxs-lookup"><span data-stu-id="d1217-264">The following example uses code page 1252 (the Windows code page for Western European languages) to illustrate best-fit mapping and its drawbacks.</span></span> <span data-ttu-id="d1217-265">O método [Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) é usado para recuperar um objeto de codificação para a página de código 1252.</span><span class="sxs-lookup"><span data-stu-id="d1217-265">The [Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) method is used to retrieve an encoding object for code page 1252.</span></span> <span data-ttu-id="d1217-266">Por padrão, ele usa um mapeamento de melhor ajuste para caracteres Unicode aos quais ele não dá suporte.</span><span class="sxs-lookup"><span data-stu-id="d1217-266">By default, it uses a best-fit mapping for Unicode characters that it does not support.</span></span> <span data-ttu-id="d1217-267">O exemplo cria uma instância de uma cadeia de caracteres que contém três caracteres não ASCII – LETRA MAIÚSCULA LATINA S CIRCULADA (U+24C8), CINCO SOBRESCRITO (U+2075) e INFINITO (U+221E) – separados por espaços.</span><span class="sxs-lookup"><span data-stu-id="d1217-267">The example instantiates a string that contains three non-ASCII characters - CIRCLED LATIN CAPITAL LETTER S (U+24C8), SUPERSCRIPT FIVE (U+2075), and INFINITY (U+221E) - separated by spaces.</span></span> <span data-ttu-id="d1217-268">Como mostra a saída de exemplo, quando a cadeia de caracteres é codificada, os três caracteres originais sem espaço são substituídos pelo PONTO DE INTERROGAÇÃO (U+003F), DÍGITO CINCO (U+0035) e DÍGITO OITO (U+0038).</span><span class="sxs-lookup"><span data-stu-id="d1217-268">As the output from the example shows, when the string is encoded, the three original non-space characters are replaced by QUESTION MARK (U+003F), DIGIT FIVE (U+0035), and DIGIT EIGHT (U+0038).</span></span> <span data-ttu-id="d1217-269">DÍGITO OITO é um substituto especialmente ruim para o caractere INFINITO sem suporte e o PONTO DE INTERROGAÇÃO indica que nenhum mapeamento estava disponível para o caractere original.</span><span class="sxs-lookup"><span data-stu-id="d1217-269">DIGIT EIGHT is a particularly poor replacement for the unsupported INFINITY character, and QUESTION MARK indicates that no mapping was available for the original character.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Get an encoding for code page 1252 (Western Europe character set).
      Encoding cp1252 = Encoding.GetEncoding(1252);

      // Define and display a string.
      string str = "\u24c8 \u2075 \u221e";
      Console.WriteLine("Original string: " + str);
      Console.Write("Code points in string: ");
      foreach (var ch in str)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");   

      // Encode a Unicode string.
      Byte[] bytes = cp1252.GetBytes(str);
      Console.Write("Encoded bytes: ");
      foreach (byte byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the string.
      string str2 = cp1252.GetString(bytes);
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2));
      if (! str.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
      }
   }
}
// The example displays the following output:
//       Original string: Ⓢ ⁵ ∞
//       Code points in string: 24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 35 20 38
//       
//       String round-tripped: False
//       ? 5 8
//       003F 0020 0035 0020 0038
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      ' Get an encoding for code page 1252 (Western Europe character set).
      Dim cp1252 As Encoding = Encoding.GetEncoding(1252)

      ' Define and display a string.
      Dim str As String = String.Format("{0} {1} {2}", ChrW(&h24c8), ChrW(&H2075), ChrW(&h221E))
      Console.WriteLine("Original string: " + str)
      Console.Write("Code points in string: ")
      For Each ch In str
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next
      Console.WriteLine()   
      Console.WriteLine()

      ' Encode a Unicode string.
      Dim bytes() As Byte = cp1252.GetBytes(str)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the string.
      Dim str2 As String = cp1252.GetString(bytes)
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2))
      If Not str.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Original string: Ⓢ ⁵ ∞
'       Code points in string: 24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 35 20 38
'       
'       String round-tripped: False
'       ? 5 8
'       003F 0020 0035 0020 0038
```

<span data-ttu-id="d1217-270">O mapeamento de melhor ajuste é o comportamento padrão para um objeto [Encoding](xref:System.Text.Encoding) que codifica dados Unicode em dados da página de código e há aplicativos herdados que se baseiam nesse comportamento.</span><span class="sxs-lookup"><span data-stu-id="d1217-270">Best-fit mapping is the default behavior for an [Encoding](xref:System.Text.Encoding) object that encodes Unicode data into code page data, and there are legacy applications that rely on this behavior.</span></span> <span data-ttu-id="d1217-271">No entanto, a maioria dos novos aplicativos devem evitar o comportamento de melhor ajuste por motivos de segurança.</span><span class="sxs-lookup"><span data-stu-id="d1217-271">However, most new applications should avoid best-fit behavior for security reasons.</span></span> <span data-ttu-id="d1217-272">Por exemplo, os aplicativos não devem colocar um nome de domínio por meio de uma codificação de melhor ajuste.</span><span class="sxs-lookup"><span data-stu-id="d1217-272">For example, applications should not put a domain name through a best-fit encoding.</span></span>

> [!Note]
> <span data-ttu-id="d1217-273">Você também pode implementar um mapeamento de fallback de melhor ajuste personalizado para uma codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-273">You can also implement a custom best-fit fallback mapping for an encoding.</span></span> <span data-ttu-id="d1217-274">Para obter mais informações, consulte a seção [Implementando uma estratégia de fallback personalizada](#implementing-a-custom-fallback-strategy).</span><span class="sxs-lookup"><span data-stu-id="d1217-274">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="d1217-275">Se o fallback de melhor ajuste for o padrão para um objeto de codificação, você poderá escolher outra estratégia de fallback quando você recuperar um objeto [Encoding](xref:System.Text.Encoding) chamando a sobrecarga [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) ou [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)).</span><span class="sxs-lookup"><span data-stu-id="d1217-275">If best-fit fallback is the default for an encoding object, you can choose another fallback strategy when you retrieve an [Encoding](xref:System.Text.Encoding) object by calling the [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) or [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) overload.</span></span> <span data-ttu-id="d1217-276">A seção a seguir inclui um exemplo que substitui cada caractere que não pode ser mapeado para a página de código 1252 com um asterisco (\*).</span><span class="sxs-lookup"><span data-stu-id="d1217-276">The following section includes an example that replaces each character that cannot be mapped to code page 1252 with an asterisk (\*).</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

### <a name="replacement-fallback"></a><span data-ttu-id="d1217-277">Fallback de substituição</span><span class="sxs-lookup"><span data-stu-id="d1217-277">Replacement fallback</span></span>

<span data-ttu-id="d1217-278">Quando um caractere não tem uma correspondência exata do esquema de destino, mas não há nenhum caractere apropriado para o qual ele pode ser mapeado, o aplicativo pode especificar um caractere ou uma cadeia de caracteres de substituição.</span><span class="sxs-lookup"><span data-stu-id="d1217-278">When a character does not have an exact match in the target scheme, but there is no appropriate character that it can be mapped to, the application can specify a replacement character or string.</span></span> <span data-ttu-id="d1217-279">Esse é o comportamento padrão para o decodificador de Unicode, que substitui qualquer sequência de dois bytes que ele não pode decodificar por REPLACEMENT_CHARACTER (U+FFFD).</span><span class="sxs-lookup"><span data-stu-id="d1217-279">This is the default behavior for the Unicode decoder, which replaces any two-byte sequence that it cannot decode with REPLACEMENT_CHARACTER (U+FFFD).</span></span> <span data-ttu-id="d1217-280">Também é o comportamento padrão da classe [ASCIIEncoding](xref:System.Text.ASCIIEncoding), que substitui cada caractere que ela não pode codificar ou decodificar por um ponto de interrogação.</span><span class="sxs-lookup"><span data-stu-id="d1217-280">It is also the default behavior of the [ASCIIEncoding](xref:System.Text.ASCIIEncoding) class, which replaces each character that it cannot encode or decode with a question mark.</span></span> <span data-ttu-id="d1217-281">O exemplo a seguir ilustra a substituição de caracteres para a cadeia de caracteres Unicode do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="d1217-281">The following example illustrates character replacement for the Unicode string from the previous example.</span></span> <span data-ttu-id="d1217-282">Como mostra a saída, cada caractere que não puder ser decodificado em um valor de bytes ASCII é substituído por 0x3F, que é o código ASCII para um ponto de interrogação.</span><span class="sxs-lookup"><span data-stu-id="d1217-282">As the output shows, each character that cannot be decoded into an ASCII byte value is replaced by 0x3F, which is the ASCII code for a question mark.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.ASCII;

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 3F 20 3F
//       
//       Round-trip: False
//       ? ? ?
//       003F 0020 003F 0020 003F
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.Ascii

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 3F 20 3F
'       
'       Round-trip: False
'       ? ? ?
'       003F 0020 003F 0020 003F
```

<span data-ttu-id="d1217-283">O .NET inclui as classes [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) e [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback), que substituem uma cadeia de caracteres de substituição se um caractere não mapear exatamente em uma operação de codificação ou decodificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-283">.NET includes the [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) and [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) classes, which substitute a replacement string if a character does not map exactly in an encoding or decoding operation.</span></span> <span data-ttu-id="d1217-284">Por padrão, essa cadeia de caracteres de substituição é um ponto de interrogação, mas você pode chamar uma sobrecarga do construtor de classes para escolher uma cadeia de caracteres diferente.</span><span class="sxs-lookup"><span data-stu-id="d1217-284">By default, this replacement string is a question mark, but you can call a class constructor overload to choose a different string.</span></span> <span data-ttu-id="d1217-285">Normalmente, a cadeia de caracteres de substituição é um único caractere, embora isso não seja um requisito.</span><span class="sxs-lookup"><span data-stu-id="d1217-285">Typically, the replacement string is a single character, although this is not a requirement.</span></span> <span data-ttu-id="d1217-286">O exemplo a seguir altera o comportamento do codificador da página de código 1252 criando uma instância de um objeto [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) que usa um asterisco (\*) como uma cadeia de caracteres de substituição.</span><span class="sxs-lookup"><span data-stu-id="d1217-286">The following example changes the behavior of the code page 1252 encoder by instantiating an [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) object that uses an asterisk (\*) as a replacement string.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

> [!NOTE]
> <span data-ttu-id="d1217-287">Você também pode implementar uma classe de substituição para uma codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-287">You can also implement a replacement class for an encoding.</span></span> <span data-ttu-id="d1217-288">Para obter mais informações, consulte a seção [Implementando uma estratégia de fallback personalizada](#implementing-a-custom-fallback-strategy).</span><span class="sxs-lookup"><span data-stu-id="d1217-288">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="d1217-289">Além de PONTO DE INTERROGAÇÃO (U+003F), o CARACTERE DE SUBSTITUIÇÃO Unicode (U+FFFD) normalmente é usado como uma cadeia de caracteres de substituição, especialmente ao decodificar sequências de bytes que não podem ser convertidas com êxito em caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="d1217-289">In addition to QUESTION MARK (U+003F), the Unicode REPLACEMENT CHARACTER (U+FFFD) is commonly used as a replacement string, particularly when decoding byte sequences that cannot be successfully translated into Unicode characters.</span></span> <span data-ttu-id="d1217-290">No entanto, você está livre para escolher qualquer cadeia de caracteres de substituição e ela pode conter vários caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-290">However, you are free to choose any replacement string, and it can contain multiple characters.</span></span>

### <a name="exception-fallback"></a><span data-ttu-id="d1217-291">Fallback de exceção</span><span class="sxs-lookup"><span data-stu-id="d1217-291">Exception fallback</span></span>

<span data-ttu-id="d1217-292">Em vez de oferecer um fallback de melhor ajuste ou uma cadeia de caracteres de substituição, um codificador pode lançar uma [EncoderFallbackException](xref:System.Text.EncoderFallbackException) se não for possível codificar um conjunto de caracteres e um decodificador pode lançar uma [DecoderFallbackException](xref:System.Text.DecoderFallbackException) se não for possível decodificar uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="d1217-292">Instead of providing a best-fit fallback or a replacement string, an encoder can throw an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) if it is unable to encode a set of characters, and a decoder can throw a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) if it is unable to decode a byte array.</span></span> <span data-ttu-id="d1217-293">Para lançar uma exceção nas operações de codificação e decodificação, você deve fornecer um objeto [EncoderFallbackException](xref:System.Text.EncoderFallbackException) e um objeto [DecoderFallbackException](xref:System.Text.DecoderFallbackException), respectivamente, para o método [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)).</span><span class="sxs-lookup"><span data-stu-id="d1217-293">To throw an exception in encoding and decoding operations, you supply an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) object and a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) object, respectively, to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method.</span></span> <span data-ttu-id="d1217-294">O exemplo a seguir ilustra a o fallback de exceção com a classe ASCIIEncoding.</span><span class="sxs-lookup"><span data-stu-id="d1217-294">The following example illustrates exception fallback with the ASCIIEncoding class.</span></span>

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", 
                                          new EncoderExceptionFallback(), 
                                          new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = {};
      try {
         bytes = enc.GetBytes(str1);
         Console.Write("Encoded bytes: ");
         foreach (var byt in bytes)
            Console.Write("{0:X2} ", byt);

         Console.WriteLine();
      }
      catch (EncoderFallbackException e) {
         Console.Write("Exception: ");
         if (e.IsUnknownSurrogate())
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index);
         else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index);
         return;
      }
      Console.WriteLine();

      // Decode the ASCII bytes.
      try {
         string str2 = enc.GetString(bytes);
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
         if (! str1.Equals(str2)) {
            Console.WriteLine(str2);
            foreach (var ch in str2)
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

            Console.WriteLine();
         } 
      }
      catch (DecoderFallbackException e) {
         Console.Write("Unable to decode byte(s) ");
         foreach (byte unknown in e.BytesUnknown)
            Console.Write("0x{0:X2} ");

         Console.WriteLine("at index {0}", e.Index);
      }
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Exception: Unable to encode 0x24C8 at index 0.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", 
                                                 New EncoderExceptionFallback(), 
                                                 New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = {}
      Try
         bytes = enc.GetBytes(str1)
         Console.Write("Encoded bytes: ")
         For Each byt In bytes
            Console.Write("{0:X2} ", byt)
         Next
         Console.WriteLine()
      Catch e As EncoderFallbackException
         Console.Write("Exception: ")
         If e.IsUnknownSurrogate() Then
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index)
         Else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index)
         End If                              
         Exit Sub
      End Try
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Try
         Dim str2 As String = enc.GetString(bytes)
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
         If Not str1.Equals(str2) Then
            Console.WriteLine(str2)
            For Each ch In str2
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
            Next    
            Console.WriteLine()
         End If 
      Catch e As DecoderFallbackException
         Console.Write("Unable to decode byte(s) ")
         For Each unknown As Byte In e.BytesUnknown
            Console.Write("0x{0:X2} ")
         Next
         Console.WriteLine("at index {0}", e.Index)
      End Try
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Exception: Unable to encode 0x24C8 at index 0.
```

> [!NOTE]
> <span data-ttu-id="d1217-295">Você também pode implementar um manipulador de exceção personalizado para uma operação de codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-295">You can also implement a custom exception handler for an encoding operation.</span></span> <span data-ttu-id="d1217-296">Para obter mais informações, consulte a seção [Implementando uma estratégia de fallback personalizada](#implementing-a-custom-fallback-strategy).</span><span class="sxs-lookup"><span data-stu-id="d1217-296">For more information, see the [Implementing a custom fallback strategy](#implementing-a-custom-fallback-strategy) section.</span></span>
 
<span data-ttu-id="d1217-297">Os objetos [EncoderFallbackException](xref:System.Text.EncoderFallbackException) e [DecoderFallbackException](xref:System.Text.DecoderFallbackException) fornecem as seguintes informações sobre a condição que causou a exceção:</span><span class="sxs-lookup"><span data-stu-id="d1217-297">The [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) objects provide the following information about the condition that caused the exception:</span></span> 

* <span data-ttu-id="d1217-298">O objeto [EncoderFallbackException](xref:System.Text.EncoderFallbackException) inclui um método [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate), que indica se o caractere ou caracteres que não podem ser codificados representam um par alternativo desconhecido (nesse caso, o método retorna `true`) ou um único caractere desconhecido (nesse caso, o método retorna `false`).</span><span class="sxs-lookup"><span data-stu-id="d1217-298">The [EncoderFallbackException](xref:System.Text.EncoderFallbackException) object includes an [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate) method, which indicates whether the character or characters that cannot be encoded represent an unknown surrogate pair (in which case, the method returns `true`) or an unknown single character (in which case, the method returns `false`).</span></span> <span data-ttu-id="d1217-299">Os caracteres do par alternativo estão disponíveis nas propriedades [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) e [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow).</span><span class="sxs-lookup"><span data-stu-id="d1217-299">The characters in the surrogate pair are available from the [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) and [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow) properties.</span></span> <span data-ttu-id="d1217-300">O único caractere desconhecido está disponível na propriedade [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown).</span><span class="sxs-lookup"><span data-stu-id="d1217-300">The unknown single character is available from the [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown) property.</span></span> <span data-ttu-id="d1217-301">A propriedade [EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) indica a posição na cadeia de caracteres na qual o primeiro caractere que não pôde ser codificado foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="d1217-301">The [EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) property indicates the position in the string at which the first character that could not be encoded was found.</span></span>

* <span data-ttu-id="d1217-302">O objeto [DecoderFallbackException](xref:System.Text.DecoderFallbackException) inclui uma propriedade [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) que retorna uma matriz de bytes que não pode ser decodificada.</span><span class="sxs-lookup"><span data-stu-id="d1217-302">The [DecoderFallbackException](xref:System.Text.DecoderFallbackException) object includes a [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) property that returns an array of bytes that cannot be decoded.</span></span> <span data-ttu-id="d1217-303">A propriedade [DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) indica a posição inicial dos bytes desconhecidos.</span><span class="sxs-lookup"><span data-stu-id="d1217-303">The [DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) property indicates the starting position of the unknown bytes.</span></span>

<span data-ttu-id="d1217-304">Embora os objetos [EncoderFallbackException](xref:System.Text.EncoderFallbackException) e [DecoderFallbackException](xref:System.Text.DecoderFallbackException) forneçam informações de diagnóstico adequadas sobre a exceção, eles não fornecem acesso ao buffer de codificação ou decodificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-304">Although the [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) objects provide adequate diagnostic information about the exception, they do not provide access to the encoding or decoding buffer.</span></span> <span data-ttu-id="d1217-305">Portanto, eles não permitem que dados inválidos sejam substituídos ou corrigidos dentro do método de codificação ou de decodificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-305">Therefore, they do not allow invalid data to be replaced or corrected within the encoding or decoding method.</span></span>

## <a name="implementing-a-custom-fallback-strategy"></a><span data-ttu-id="d1217-306">Implementando uma estratégia de fallback personalizada</span><span class="sxs-lookup"><span data-stu-id="d1217-306">Implementing a custom fallback strategy</span></span>

<span data-ttu-id="d1217-307">Além do mapeamento de melhor ajuste implementado internamente por páginas de código, o .NET inclui as seguintes classes para implementar uma estratégia de fallback:</span><span class="sxs-lookup"><span data-stu-id="d1217-307">In addition to the best-fit mapping that is implemented internally by code pages, .NET includes the following classes for implementing a fallback strategy:</span></span>

* <span data-ttu-id="d1217-308">Use [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) e [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) para substituir caracteres em operações de codificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-308">Use [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) and [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) to replace characters in encoding operations.</span></span>

* <span data-ttu-id="d1217-309">Use [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) e [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) para substituir caracteres em operações de decodificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-309">Use [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) to replace characters in decoding operations.</span></span>

* <span data-ttu-id="d1217-310">Use [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) e [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) para lançar um [EncoderFallbackException](xref:System.Text.EncoderFallbackException) quando um caractere não puder ser codificado.</span><span class="sxs-lookup"><span data-stu-id="d1217-310">Use [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) and [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) to throw an [EncoderFallbackException](xref:System.Text.EncoderFallbackException) when a character cannot be encoded.</span></span>

* <span data-ttu-id="d1217-311">Use [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) e [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) para lançar um [DecoderFallbackException](xref:System.Text.DecoderFallbackException) quando um caractere não puder ser decodificado.</span><span class="sxs-lookup"><span data-stu-id="d1217-311">Use [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) to throw a [DecoderFallbackException](xref:System.Text.DecoderFallbackException) when a character cannot be decoded.</span></span>

<span data-ttu-id="d1217-312">Além disso, você pode implementar uma solução personalizada que usa o fallback de melhor ajuste, fallback de substituição ou fallback de exceção seguindo estas etapas:</span><span class="sxs-lookup"><span data-stu-id="d1217-312">In addition, you can implement a custom solution that uses best-fit fallback, replacement fallback, or exception fallback, by following these steps:</span></span> 

1. <span data-ttu-id="d1217-313">Derive uma classe de [EncoderFallback](xref:System.Text.EncoderFallback) para operações de codificação e de [DecoderFallback](xref:System.Text.DecoderFallback) para operações de decodificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-313">Derive a class from [EncoderFallback](xref:System.Text.EncoderFallback) for encoding operations, and from [DecoderFallback](xref:System.Text.DecoderFallback) for decoding operations.</span></span>

2. <span data-ttu-id="d1217-314">Derive uma classe de [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) para operações de codificação e de [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) para operações de decodificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-314">Derive a class from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) for encoding operations, and from [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) for decoding operations.</span></span>

3. <span data-ttu-id="d1217-315">Para o fallback de exceção, se as classes [EncoderFallbackException](xref:System.Text.EncoderFallbackException) e [DecoderFallbackException](xref:System.Text.DecoderFallbackException) predefinidas não atenderem às suas necessidades, derive uma classe de um objeto de exceção como [Exception](xref:System.Exception) ou [ArgumentException](xref:System.ArgumentException).</span><span class="sxs-lookup"><span data-stu-id="d1217-315">For exception fallback, if the predefined [EncoderFallbackException](xref:System.Text.EncoderFallbackException) and [DecoderFallbackException](xref:System.Text.DecoderFallbackException) classes do not meet your needs, derive a class from an exception object such as [Exception](xref:System.Exception) or [ArgumentException](xref:System.ArgumentException).</span></span>

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a><span data-ttu-id="d1217-316">Derivando de EncoderFallback ou DecoderFallback</span><span class="sxs-lookup"><span data-stu-id="d1217-316">Deriving from EncoderFallback or DecoderFallback</span></span>

<span data-ttu-id="d1217-317">Para implementar uma solução de fallback personalizada, você deverá criar uma classe herdada de [EncoderFallback](xref:System.Text.EncoderFallback) para operações de codificação e de [DecoderFallback](xref:System.Text.DecoderFallback) para operações de decodificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-317">To implement a custom fallback solution, you must create a class that inherits from [EncoderFallback](xref:System.Text.EncoderFallback) for encoding operations, and from [DecoderFallback](xref:System.Text.DecoderFallback) for decoding operations.</span></span> <span data-ttu-id="d1217-318">As instâncias dessas classes são passadas para o método [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) e funcionam como intermediário entre a classe de codificação e a implementação do fallback.</span><span class="sxs-lookup"><span data-stu-id="d1217-318">Instances of these classes are passed to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method and serve as the intermediary between the encoding class and the fallback implementation.</span></span>

<span data-ttu-id="d1217-319">Quando você cria uma solução de fallback personalizada para um codificador ou um decodificador, você deve implementar os seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="d1217-319">When you create a custom fallback solution for an encoder or decoder, you must implement the following members:</span></span>

* <span data-ttu-id="d1217-320">A propriedade [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) ou [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount), que retorna o número máximo possível de caracteres que o fallback de melhor ajuste, de substituição ou de exceção pode retornar para substituir um único caractere.</span><span class="sxs-lookup"><span data-stu-id="d1217-320">The [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) or [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount) property, which returns the maximum possible number of characters that the best-fit, replacement, or exception fallback can return to replace a single character.</span></span> <span data-ttu-id="d1217-321">Para um fallback de exceção personalizado, seu valor é zero.</span><span class="sxs-lookup"><span data-stu-id="d1217-321">For a custom exception fallback, its value is zero.</span></span> 

* <span data-ttu-id="d1217-322">O método [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) ou [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer), que retorna sua implementação [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) ou [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) personalizada.</span><span class="sxs-lookup"><span data-stu-id="d1217-322">The [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) or [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) method, which returns your custom [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) or [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) implementation.</span></span> <span data-ttu-id="d1217-323">O método é chamado pelo codificador quando ele encontra o primeiro caractere que ele não consegue codificar com êxito ou pelo decodificador quando ele encontra o primeiro byte que ele não consegue decodificar com êxito.</span><span class="sxs-lookup"><span data-stu-id="d1217-323">The method is called by the encoder when it encounters the first character that it is unable to successfully encode, or by the decoder when it encounters the first byte that it is unable to successfully decode.</span></span>

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a><span data-ttu-id="d1217-324">Derivando de EncoderFallbackBuffer ou DecoderFallbackBuffer</span><span class="sxs-lookup"><span data-stu-id="d1217-324">Deriving from EncoderFallbackBuffer or DecoderFallbackBuffer</span></span>

<span data-ttu-id="d1217-325">Para implementar uma solução de fallback personalizada, você também deverá criar uma classe herdada de [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) para operações de codificação e de [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) para operações de decodificação.</span><span class="sxs-lookup"><span data-stu-id="d1217-325">To implement a custom fallback solution, you must also create a class that inherits from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) for encoding operations, and from [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) for decoding operations.</span></span> <span data-ttu-id="d1217-326">As instâncias dessas classes são retornadas pelo método `CreateFallbackBuffer` das classes [EncoderFallback](xref:System.Text.EncoderFallback) e [DecoderFallback](xref:System.Text.DecoderFallback).</span><span class="sxs-lookup"><span data-stu-id="d1217-326">Instances of these classes are returned by the `CreateFallbackBuffer` method of the [EncoderFallback](xref:System.Text.EncoderFallback) and [DecoderFallback](xref:System.Text.DecoderFallback) classes.</span></span> <span data-ttu-id="d1217-327">O método [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) é chamado pelo codificador quando ele encontra o primeiro caractere que ele não consegue codificar e o método [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) é chamado pelo decodificador quando ele encontra um ou mais bytes que ele não consegue decodificar.</span><span class="sxs-lookup"><span data-stu-id="d1217-327">The [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) method is called by the encoder when it encounters the first character that it is not able to encode, and the [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) method is called by the decoder when it encounters one or more bytes that it is not able to decode.</span></span> <span data-ttu-id="d1217-328">As classes [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) e [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) fornecem a implementação de fallback.</span><span class="sxs-lookup"><span data-stu-id="d1217-328">The [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) classes provide the fallback implementation.</span></span> <span data-ttu-id="d1217-329">Cada instância representa um buffer que contém os caracteres de fallback que substituirão o caractere que não pode ser codificado ou a sequência de bytes que não pode ser decodificada.</span><span class="sxs-lookup"><span data-stu-id="d1217-329">Each instance represents a buffer that contains the fallback characters that will replace the character that cannot be encoded or the byte sequence that cannot be decoded.</span></span>

<span data-ttu-id="d1217-330">Quando você cria uma solução de fallback personalizada para um codificador ou um decodificador, você deve implementar os seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="d1217-330">When you create a custom fallback solution for an encoder or decoder, you must implement the following members:</span></span>

* <span data-ttu-id="d1217-331">O método [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) ou [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)).</span><span class="sxs-lookup"><span data-stu-id="d1217-331">The [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) or [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) method.</span></span> <span data-ttu-id="d1217-332">[EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) é chamado pelo codificador para fornecer ao buffer de fallback informações sobre o caractere que ele não consegue codificar.</span><span class="sxs-lookup"><span data-stu-id="d1217-332">[EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) is called by the encoder to provide the fallback buffer with information about the character that it cannot encode.</span></span> <span data-ttu-id="d1217-333">Como o caractere a ser codificado pode ser um par alternativo, esse método está sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="d1217-333">Because the character to be encoded may be a surrogate pair, this method is overloaded.</span></span> <span data-ttu-id="d1217-334">Uma sobrecarga é passada para o caractere a ser codificado e para o seu índice na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-334">One overload is passed the character to be encoded and its index in the string.</span></span> <span data-ttu-id="d1217-335">A segunda sobrecarga é passada para os substitutos altos e baixos juntamente com seu índice na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d1217-335">The second overload is passed the high and low surrogate along with its index in the string.</span></span> <span data-ttu-id="d1217-336">O método [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) é chamado pelo decodificador para fornecer ao buffer de fallback informações sobre os bytes que ele não consegue decodificar.</span><span class="sxs-lookup"><span data-stu-id="d1217-336">The [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) method is called by the decoder to provide the fallback buffer with information about the bytes that it cannot decode.</span></span> <span data-ttu-id="d1217-337">Esse método recebe uma matriz de bytes que ele não consegue decodificar, juntamente com o índice do primeiro byte.</span><span class="sxs-lookup"><span data-stu-id="d1217-337">This method is passed an array of bytes that it cannot decode, along with the index of the first byte.</span></span> <span data-ttu-id="d1217-338">O método de fallback deverá retornar `true` se o buffer de fallback conseguir fornecer caracteres de melhor ajuste ou de substituição; caso contrário, ele deverá retornar `false`.</span><span class="sxs-lookup"><span data-stu-id="d1217-338">The fallback method should return `true` if the fallback buffer can supply a best-fit or replacement character or characters; otherwise, it should return `false`.</span></span> <span data-ttu-id="d1217-339">Para um fallback de exceção, o método de fallback deve lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d1217-339">For an exception fallback, the fallback method should throw an exception.</span></span>

* <span data-ttu-id="d1217-340">O método [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) ou [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar), chamado repetidamente pelo codificador ou decodificador para obter o próximo caractere do buffer de fallback.</span><span class="sxs-lookup"><span data-stu-id="d1217-340">The [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) or [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar) method, which is called repeatedly by the encoder or decoder to get the next character from the fallback buffer.</span></span> <span data-ttu-id="d1217-341">Quando todos os caracteres de fallback tiverem sido retornados, o método deverá retornar U+0000.</span><span class="sxs-lookup"><span data-stu-id="d1217-341">When all fallback characters have been returned, the method should return U+0000.</span></span> 

* <span data-ttu-id="d1217-342">A propriedade [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) ou [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining), que retorna o número de caracteres restantes no buffer de fallback.</span><span class="sxs-lookup"><span data-stu-id="d1217-342">The [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) or [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining) property, which returns the number of characters remaining in the fallback buffer.</span></span>

* <span data-ttu-id="d1217-343">O método [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) ou [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious), que move a posição atual no buffer de fallback para o caractere anterior.</span><span class="sxs-lookup"><span data-stu-id="d1217-343">The [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) or [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious) method, which moves the current position in the fallback buffer to the previous character.</span></span>

* <span data-ttu-id="d1217-344">O método [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) ou [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset), que reinicializa o buffer de fallback.</span><span class="sxs-lookup"><span data-stu-id="d1217-344">The [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) or [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset) method, which reinitializes the fallback buffer.</span></span>

<span data-ttu-id="d1217-345">Se a implementação de fallback for um fallback de melhor ajuste ou de substituição, as classes derivadas de [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) e [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) também mantêm dois campos de instância privados: o número exato de caracteres no buffer e o índice do próximo caractere no buffer a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="d1217-345">If the fallback implementation is a best-fit fallback or a replacement fallback, the classes derived from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) and [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) also maintain two private instance fields: the exact number of characters in the buffer; and the index of the next character in the buffer to return.</span></span>

### <a name="an-encoderfallback-example"></a><span data-ttu-id="d1217-346">Um exemplo de EncoderFallback</span><span class="sxs-lookup"><span data-stu-id="d1217-346">An EncoderFallback example</span></span>

<span data-ttu-id="d1217-347">Um exemplo anterior usava o fallback de substituição para substituir caracteres Unicode que não correspondiam aos caracteres ASCII por um asterisco (\*).</span><span class="sxs-lookup"><span data-stu-id="d1217-347">An earlier example used replacement fallback to replace Unicode characters that did not correspond to ASCII characters with an asterisk (\*).</span></span> <span data-ttu-id="d1217-348">O exemplo a seguir usa uma implementação de fallback de melhor ajuste personalizada em vez de fornecer um melhor mapeamento de caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="d1217-348">The following example uses a custom best-fit fallback implementation instead to provide a better mapping of non-ASCII characters.</span></span>

<span data-ttu-id="d1217-349">O código a seguir define uma classe chamada `CustomMapper` derivada de [EncoderFallback](xref:System.Text.EncoderFallback) para lidar com o mapeamento de melhor ajuste de caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="d1217-349">The following code defines a class named `CustomMapper` that is derived from [EncoderFallback](xref:System.Text.EncoderFallback) to handle the best-fit mapping of non-ASCII characters.</span></span> <span data-ttu-id="d1217-350">Seu método `CreateFallbackBuffer` retorna um objeto `CustomMapperFallbackBuffer`, que fornece a implementação do [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer).</span><span class="sxs-lookup"><span data-stu-id="d1217-350">Its `CreateFallbackBuffer` method returns a `CustomMapperFallbackBuffer` object, which provides the [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) implementation.</span></span> <span data-ttu-id="d1217-351">A classe `CustomMapper` usa um objeto [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) para armazenar os mapeamentos de caracteres Unicode sem suporte (o valor da chave) e seus caracteres de 8 bits correspondentes (armazenados em dois bytes consecutivos em um inteiro de 64 bits).</span><span class="sxs-lookup"><span data-stu-id="d1217-351">The `CustomMapper` class uses a [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) object to store the mappings of unsupported Unicode characters (the key value) and their corresponding 8-bit characters (which are stored in two consecutive bytes in a 64-bit integer).</span></span> <span data-ttu-id="d1217-352">Para disponibilizar esse mapeamento ao buffer de fallback, a instância `CustomMapper` é passada como um parâmetro para o construtor de classe `CustomMapperFallbackBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d1217-352">To make this mapping available to the fallback buffer, the `CustomMapper` instance is passed as a parameter to the `CustomMapperFallbackBuffer` class constructor.</span></span> <span data-ttu-id="d1217-353">Como o mapeamento mais longo é a cadeia de caracteres "INF" para o caractere Unicode U+221E, a propriedade `MaxCharCount` retorna 3.</span><span class="sxs-lookup"><span data-stu-id="d1217-353">Because the longest mapping is the string "INF" for the Unicode character U+221E, the `MaxCharCount` property returns 3.</span></span> 

```csharp
public class CustomMapper : EncoderFallback
{
   public string DefaultString;
   internal Dictionary<ushort, ulong> mapping;

   public CustomMapper() : this("*")
   {   
   }

   public CustomMapper(string defaultString)
   {
      this.DefaultString = defaultString;

      // Create table of mappings
      mapping = new Dictionary<ushort, ulong>();
      mapping.Add(0x24C8, 0x53);
      mapping.Add(0x2075, 0x35);
      mapping.Add(0x221E, 0x49004E0046);
   }

   public override EncoderFallbackBuffer CreateFallbackBuffer()
   {
      return new CustomMapperFallbackBuffer(this);
   }

   public override int MaxCharCount
   {
      get { return 3; }
   } 
}
```

```vb
Public Class CustomMapper : Inherits EncoderFallback
   Public DefaultString As String
   Friend mapping As Dictionary(Of UShort, ULong)

   Public Sub New()
      Me.New("?")
   End Sub

   Public Sub New(ByVal defaultString As String)
      Me.DefaultString = defaultString

      ' Create table of mappings
      mapping = New Dictionary(Of UShort, ULong)
      mapping.Add(&H24C8, &H53)
      mapping.Add(&H2075, &H35)
      mapping.Add(&H221E, &H49004E0046)
   End Sub

   Public Overrides Function CreateFallbackBuffer() As System.Text.EncoderFallbackBuffer
      Return New CustomMapperFallbackBuffer(Me)
   End Function

   Public Overrides ReadOnly Property MaxCharCount As Integer
      Get
         Return 3
      End Get
   End Property
End Class
```

<span data-ttu-id="d1217-354">O código a seguir define a classe `CustomMapperFallbackBuffer`, derivada de [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer).</span><span class="sxs-lookup"><span data-stu-id="d1217-354">The following code defines the `CustomMapperFallbackBuffer` class, which is derived from [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer).</span></span> <span data-ttu-id="d1217-355">O dicionário que contém mapeamentos de melhor ajuste e definido na instância `CustomMapper` está disponível no seu construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="d1217-355">The dictionary that contains best-fit mappings and that is defined in the `CustomMapper` instance is available from its class constructor.</span></span> <span data-ttu-id="d1217-356">Seu método `Fallback` retornará `true` se qualquer um dos caracteres Unicode que o codificador ASCII não conseguir codificar forem definidos no dicionário de mapeamento; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="d1217-356">Its `Fallback` method returns `true` if any of the Unicode characters that the ASCII encoder cannot encode are defined in the mapping dictionary; otherwise, it returns `false`.</span></span> <span data-ttu-id="d1217-357">Para cada fallback, a variável `count` privada indica o número de caracteres que continuam sendo retornados e a variável `index` privada indica a posição no buffer de cadeia de caracteres, `charsToReturn`, do próximo caractere a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="d1217-357">For each fallback, the private `count` variable indicates the number of characters that remain to be returned, and the private `index` variable indicates the position in the string buffer, `charsToReturn`, of the next character to return.</span></span> 

```csharp
public class CustomMapperFallbackBuffer : EncoderFallbackBuffer
{
   int count = -1;                   // Number of characters to return
   int index = -1;                   // Index of character to return
   CustomMapper fb; 
   string charsToReturn; 

   public CustomMapperFallbackBuffer(CustomMapper fallback)
   {
      this.fb = fallback;
   }

   public override bool Fallback(char charUnknownHigh, char charUnknownLow, int index)
   {
      // Do not try to map surrogates to ASCII.
      return false;
   }

   public override bool Fallback(char charUnknown, int index)
   {
      // Return false if there are already characters to map.
      if (count >= 1) return false;

      // Determine number of characters to return.
      charsToReturn = String.Empty;

      ushort key = Convert.ToUInt16(charUnknown);
      if (fb.mapping.ContainsKey(key)) {
         byte[] bytes = BitConverter.GetBytes(fb.mapping[key]);
         int ctr = 0;
         foreach (var byt in bytes) {
            if (byt > 0) {
               ctr++;
               charsToReturn += (char) byt;
            }
         }
         count = ctr;
      }
      else {
         // Return default.
         charsToReturn = fb.DefaultString;
         count = 1;
      }
      this.index = charsToReturn.Length - 1;

      return true;
   }

   public override char GetNextChar()
   {
      // We'll return a character if possible, so subtract from the count of chars to return.
      count--;
      // If count is less than zero, we've returned all characters.
      if (count < 0) 
         return '\u0000';

      this.index--;
      return charsToReturn[this.index + 1];
   }

   public override bool MovePrevious()
   {
      // Original: if count >= -1 and pos >= 0
      if (count >= -1) {
         count++;
         return true;
      }
      else {
         return false;
      }
   }

   public override int Remaining 
   {
      get { return count < 0 ? 0 : count; }
   }

   public override void Reset()
   {
      count = -1;
      index = -1;
   }
}
```

```vb
Public Class CustomMapperFallbackBuffer : Inherits EncoderFallbackBuffer

   Dim count As Integer = -1        ' Number of characters to return
   Dim index As Integer = -1        ' Index of character to return
   Dim fb As CustomMapper
   Dim charsToReturn As String

   Public Sub New(ByVal fallback As CustomMapper)
      MyBase.New()
      Me.fb = fallback
   End Sub

   Public Overloads Overrides Function Fallback(ByVal charUnknownHigh As Char, ByVal charUnknownLow As Char, ByVal index As Integer) As Boolean
      ' Do not try to map surrogates to ASCII.
      Return False
   End Function

   Public Overloads Overrides Function Fallback(ByVal charUnknown As Char, ByVal index As Integer) As Boolean
      ' Return false if there are already characters to map.
      If count >= 1 Then Return False

      ' Determine number of characters to return.
      charsToReturn = String.Empty

      Dim key As UShort = Convert.ToUInt16(charUnknown)
      If fb.mapping.ContainsKey(key) Then
         Dim bytes() As Byte = BitConverter.GetBytes(fb.mapping.Item(key))
         Dim ctr As Integer
         For Each byt In bytes
            If byt > 0 Then
               ctr += 1
               charsToReturn += Chr(byt)
            End If
         Next
         count = ctr
      Else
         ' Return default.
         charsToReturn = fb.DefaultString
         count = 1
      End If
      Me.index = charsToReturn.Length - 1

      Return True
   End Function

   Public Overrides Function GetNextChar() As Char
      ' We'll return a character if possible, so subtract from the count of chars to return.
      count -= 1
      ' If count is less than zero, we've returned all characters.
      If count < 0 Then Return ChrW(0)

      Me.index -= 1
      Return charsToReturn(Me.index + 1)
   End Function

   Public Overrides Function MovePrevious() As Boolean
      ' Original: if count >= -1 and pos >= 0
      If count >= -1 Then
         count += 1
         Return True
      Else
         Return False
      End If
   End Function

   Public Overrides ReadOnly Property Remaining As Integer
      Get
         Return If(count < 0, 0, count)
      End Get
   End Property

   Public Overrides Sub Reset()
      count = -1
      index = -1
   End Sub
End Class
```

<span data-ttu-id="d1217-358">O código a seguir cria uma instância do objeto `CustomMapper` e passa uma instância dele para o método [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)).</span><span class="sxs-lookup"><span data-stu-id="d1217-358">The following code then instantiates the `CustomMapper` object and passes an instance of it to the [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) method.</span></span> <span data-ttu-id="d1217-359">A saída indica que a implementação de fallback de melhor ajuste lida com êxito com os três caracteres não ASCII na cadeia de caracteres original.</span><span class="sxs-lookup"><span data-stu-id="d1217-359">The output indicates that the best-fit fallback implementation successfully handles the three non-ASCII characters in the original string.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;

class Program
{
   static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", new CustomMapper(), new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      for (int ctr = 0; ctr <= str1.Length - 1; ctr++) {
         Console.Write("{0} ", Convert.ToUInt16(str1[ctr]).ToString("X4"));
         if (ctr == str1.Length - 1) 
            Console.WriteLine();
      }
      Console.WriteLine();

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);

      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      }
   }
}
```

```vb
Imports System.Text
Imports System.Collections.Generic

Module Module1

   Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", New CustomMapper(), New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&H24C8), ChrW(&H2075), ChrW(&H221E))
      Console.WriteLine(str1)
      For ctr As Integer = 0 To str1.Length - 1
         Console.Write("{0} ", Convert.ToUInt16(str1(ctr)).ToString("X4"))
         If ctr = str1.Length - 1 Then Console.WriteLine()
      Next
      Console.WriteLine()

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="d1217-360">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1217-360">See also</span></span>

[<span data-ttu-id="d1217-361">System.Text.Encoder</span><span class="sxs-lookup"><span data-stu-id="d1217-361">System.Text.Encoder</span></span>](xref:System.Text.Encoder)

[<span data-ttu-id="d1217-362">System.Text.EncoderFallback</span><span class="sxs-lookup"><span data-stu-id="d1217-362">System.Text.EncoderFallback</span></span>](xref:System.Text.EncoderFallback)

[<span data-ttu-id="d1217-363">System.Text.Decoder</span><span class="sxs-lookup"><span data-stu-id="d1217-363">System.Text.Decoder</span></span>](xref:System.Text.Decoder)

[<span data-ttu-id="d1217-364">System.Text.DecoderFallback</span><span class="sxs-lookup"><span data-stu-id="d1217-364">System.Text.DecoderFallback</span></span>](xref:System.Text.DecoderFallback)

[<span data-ttu-id="d1217-365">System.Text.Encoding</span><span class="sxs-lookup"><span data-stu-id="d1217-365">System.Text.Encoding</span></span>](xref:System.Text.Encoding)






---
title: "char (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c6601a58804d6ecfcbedbc19da09560884e54e7f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="char-c-reference"></a><span data-ttu-id="b14fa-102">char (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b14fa-102">char (C# Reference)</span></span>
<span data-ttu-id="b14fa-103">A palavra-chave `char` é usada para declarar uma instância da estrutura <xref:System.Char?displayProperty=fullName> que o .NET Framework usa para representar um caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="b14fa-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=fullName> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="b14fa-104">O valor de um objeto `Char` é um valor numérico de 16 bits (ordinal).</span><span class="sxs-lookup"><span data-stu-id="b14fa-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>  
  
 <span data-ttu-id="b14fa-105">Os caracteres Unicode são usados para representar a maioria dos idiomas escritos em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="b14fa-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>  
  
|<span data-ttu-id="b14fa-106">Tipo</span><span class="sxs-lookup"><span data-stu-id="b14fa-106">Type</span></span>|<span data-ttu-id="b14fa-107">Intervalo</span><span class="sxs-lookup"><span data-stu-id="b14fa-107">Range</span></span>|<span data-ttu-id="b14fa-108">Tamanho</span><span class="sxs-lookup"><span data-stu-id="b14fa-108">Size</span></span>|<span data-ttu-id="b14fa-109">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b14fa-109">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`char`|<span data-ttu-id="b14fa-110">U+0000 a U+FFFF</span><span class="sxs-lookup"><span data-stu-id="b14fa-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="b14fa-111">Caractere Unicode de 16 bits</span><span class="sxs-lookup"><span data-stu-id="b14fa-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="b14fa-112">Literais</span><span class="sxs-lookup"><span data-stu-id="b14fa-112">Literals</span></span>  
 <span data-ttu-id="b14fa-113">As constantes de tipo `char` podem ser escritas como literais de caracteres, sequência de escape hexadecimal ou como representação Unicode.</span><span class="sxs-lookup"><span data-stu-id="b14fa-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="b14fa-114">Você também pode converter os códigos de caracteres integrais.</span><span class="sxs-lookup"><span data-stu-id="b14fa-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="b14fa-115">No exemplo a seguir, quatro variáveis `char` são inicializadas com o mesmo caractere `X`:</span><span class="sxs-lookup"><span data-stu-id="b14fa-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>  
  
 <span data-ttu-id="b14fa-116">[!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b14fa-116">[!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="b14fa-117">Conversões</span><span class="sxs-lookup"><span data-stu-id="b14fa-117">Conversions</span></span>  
 <span data-ttu-id="b14fa-118">Um `char` pode ser implicitamente convertido em [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="b14fa-118">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="b14fa-119">No entanto, não há conversões implícitas de outros tipos para o tipo `char`.</span><span class="sxs-lookup"><span data-stu-id="b14fa-119">However, there are no implicit conversions from other types to the `char` type.</span></span>  
  
 <span data-ttu-id="b14fa-120">O tipo <xref:System.Char?displayProperty=fullName> fornece vários métodos estáticos para trabalhar com valores `char`.</span><span class="sxs-lookup"><span data-stu-id="b14fa-120">The <xref:System.Char?displayProperty=fullName> type provides several static methods for working with `char` values.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b14fa-121">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b14fa-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b14fa-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b14fa-122">See Also</span></span>  
 <span data-ttu-id="b14fa-123"><xref:System.Char></span><span class="sxs-lookup"><span data-stu-id="b14fa-123"><xref:System.Char></span></span>   
 <span data-ttu-id="b14fa-124">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b14fa-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b14fa-125">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b14fa-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b14fa-126">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b14fa-126">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b14fa-127">[Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="b14fa-127">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="b14fa-128">[Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="b14fa-128">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="b14fa-129">[Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="b14fa-129">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 <span data-ttu-id="b14fa-130">[Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="b14fa-130">[Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span></span>  
 <span data-ttu-id="b14fa-131">[Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="b14fa-131">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="b14fa-132">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="b14fa-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)


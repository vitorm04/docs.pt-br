---
title: char (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 67efc4b9600d7d722ebbef83819e143506a93c26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219213"
---
# <a name="char-c-reference"></a><span data-ttu-id="34d88-102">char (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="34d88-102">char (C# Reference)</span></span>
<span data-ttu-id="34d88-103">A palavra-chave `char` é usada para declarar uma instância da estrutura <xref:System.Char?displayProperty=nameWithType> que o .NET Framework usa para representar um caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="34d88-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="34d88-104">O valor de um objeto `Char` é um valor numérico de 16 bits (ordinal).</span><span class="sxs-lookup"><span data-stu-id="34d88-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>  
  
 <span data-ttu-id="34d88-105">Os caracteres Unicode são usados para representar a maioria dos idiomas escritos em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="34d88-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>  
  
|<span data-ttu-id="34d88-106">Tipo</span><span class="sxs-lookup"><span data-stu-id="34d88-106">Type</span></span>|<span data-ttu-id="34d88-107">Intervalo</span><span class="sxs-lookup"><span data-stu-id="34d88-107">Range</span></span>|<span data-ttu-id="34d88-108">Tamanho</span><span class="sxs-lookup"><span data-stu-id="34d88-108">Size</span></span>|<span data-ttu-id="34d88-109">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="34d88-109">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`char`|<span data-ttu-id="34d88-110">U+0000 a U+FFFF</span><span class="sxs-lookup"><span data-stu-id="34d88-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="34d88-111">Caractere Unicode de 16 bits</span><span class="sxs-lookup"><span data-stu-id="34d88-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="34d88-112">Literais</span><span class="sxs-lookup"><span data-stu-id="34d88-112">Literals</span></span>  
 <span data-ttu-id="34d88-113">As constantes de tipo `char` podem ser escritas como literais de caracteres, sequência de escape hexadecimal ou como representação Unicode.</span><span class="sxs-lookup"><span data-stu-id="34d88-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="34d88-114">Você também pode converter os códigos de caracteres integrais.</span><span class="sxs-lookup"><span data-stu-id="34d88-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="34d88-115">No exemplo a seguir, quatro variáveis `char` são inicializadas com o mesmo caractere `X`:</span><span class="sxs-lookup"><span data-stu-id="34d88-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a><span data-ttu-id="34d88-116">Conversões</span><span class="sxs-lookup"><span data-stu-id="34d88-116">Conversions</span></span>  
 <span data-ttu-id="34d88-117">Um `char` pode ser implicitamente convertido em [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="34d88-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="34d88-118">No entanto, não há conversões implícitas de outros tipos para o tipo `char`.</span><span class="sxs-lookup"><span data-stu-id="34d88-118">However, there are no implicit conversions from other types to the `char` type.</span></span>  
  
 <span data-ttu-id="34d88-119">O tipo <xref:System.Char?displayProperty=nameWithType> fornece vários métodos estáticos para trabalhar com valores `char`.</span><span class="sxs-lookup"><span data-stu-id="34d88-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="34d88-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="34d88-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34d88-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34d88-121">See Also</span></span>  
 <xref:System.Char>  
 [<span data-ttu-id="34d88-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="34d88-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="34d88-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="34d88-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="34d88-124">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="34d88-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="34d88-125">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="34d88-125">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="34d88-126">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="34d88-126">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="34d88-127">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="34d88-127">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="34d88-128">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="34d88-128">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="34d88-129">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="34d88-129">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="34d88-130">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="34d88-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

---
title: Como preencher um número com zeros à esquerda
description: Aprenda a preencher um número com zeros à esquerda. Adicione zeros à esquerda a inteiros ou valores numéricos a um comprimento total específico ou a um número específico de zeros à esquerda.
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET]
- formatting [.NET], numbers
- number formatting [.NET]
- numbers [.NET], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
ms.openlocfilehash: 7c3ee376fde34663ee0599c0b1ae654871a71206
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888450"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="08d84-104">Como preencher um número com zeros à esquerda</span><span class="sxs-lookup"><span data-stu-id="08d84-104">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="08d84-105">É possível adicionar zeros à esquerda de um inteiro usando a [cadeia de caracteres de formato numérico padrão](standard-numeric-format-strings.md) “D” com um especificador de precisão.</span><span class="sxs-lookup"><span data-stu-id="08d84-105">You can add leading zeros to an integer by using the "D" [standard numeric format string](standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="08d84-106">Você pode adicionar zeros à esquerda de inteiros e pontos flutuantes usando uma [cadeia de caracteres de formato numérico personalizado](custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="08d84-106">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](custom-numeric-format-strings.md).</span></span> <span data-ttu-id="08d84-107">Este artigo mostra como usar os dois métodos para preencher um número com zeros à esquerda.</span><span class="sxs-lookup"><span data-stu-id="08d84-107">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="08d84-108">Para acrescentar um número inteiro com zeros à esquerda com um comprimento específico</span><span class="sxs-lookup"><span data-stu-id="08d84-108">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="08d84-109">Determine o número mínimo de dígitos que o valor inteiro deve exibir.</span><span class="sxs-lookup"><span data-stu-id="08d84-109">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="08d84-110">Inclua os dígitos à esquerda nesse número.</span><span class="sxs-lookup"><span data-stu-id="08d84-110">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="08d84-111">Determine se quer exibir o inteiro como valor decimal ou hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="08d84-111">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="08d84-112">Para exibir o inteiro como um valor decimal, chame seu método `ToString(String)` e passe a cadeia de caracteres "D *n* " como o valor do parâmetro `format`, em que *n* representa o tamanho mínimo da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="08d84-112">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D *n* " as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="08d84-113">Para exibir o número inteiro como hexadecimal, chame seu método `ToString(String)` e informe a cadeia de caracteres “X *n* ” como valor do parâmetro format, em que *n* representa o comprimento mínimo da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="08d84-113">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X *n* " as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="08d84-114">Você também pode usar a cadeia de caracteres de formato em uma cadeia de caracteres interpolada em [C#](../../csharp/language-reference/tokens/interpolated.md) e em [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) ou você pode chamar um método, como <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, que usa a [formatação de composição](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="08d84-114">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](composite-formatting.md).</span></span>

<span data-ttu-id="08d84-115">O exemplo a seguir formata diversos valores inteiros com zeros à esquerda para que o comprimento total do número formatado tenha pelo menos oito caracteres.</span><span class="sxs-lookup"><span data-stu-id="08d84-115">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="08d84-116">Para acrescentar um número inteiro com uma determinada quantidade de zeros à esquerda</span><span class="sxs-lookup"><span data-stu-id="08d84-116">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="08d84-117">Determine quantos zeros à esquerda o valor inteiro deve exibir.</span><span class="sxs-lookup"><span data-stu-id="08d84-117">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="08d84-118">Determine se quer exibir o inteiro como valor decimal ou hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="08d84-118">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="08d84-119">A formatação como um valor decimal requer que você use o especificador de formato padrão "D".</span><span class="sxs-lookup"><span data-stu-id="08d84-119">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="08d84-120">A formatação como um valor hexadecimal requer que você use o especificador de formato padrão "X".</span><span class="sxs-lookup"><span data-stu-id="08d84-120">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="08d84-121">Determine o comprimento da cadeia de caracteres numérica não acrescentada. Para isso, chame o método `ToString("D").Length` ou `ToString("X").Length` do valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="08d84-121">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="08d84-122">Adicione quantos dígitos zero à esquerda quer incluir na cadeia de caracteres formatada com comprimento da cadeia de caracteres numérica não acrescentada.</span><span class="sxs-lookup"><span data-stu-id="08d84-122">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="08d84-123">A adição do número de zeros à esquerda define o comprimento total da cadeia de caracteres preenchida.</span><span class="sxs-lookup"><span data-stu-id="08d84-123">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="08d84-124">Chame o método `ToString(String)` do valor inteiro e informe a cadeia de caracteres “D *n* ” para cadeias de caracteres decimais e “X *n* ” para cadeias de caracteres hexadecimais, em que *n* representa o comprimento total da cadeia de caracteres acrescentada.</span><span class="sxs-lookup"><span data-stu-id="08d84-124">Call the integer value's `ToString(String)` method, and pass the string "D *n* " for decimal strings and "X *n* " for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="08d84-125">Você também pode usar uma cadeia de caracteres de formato “D *n* ” ou “X *n* ” em um método com suporte para formatação de composição.</span><span class="sxs-lookup"><span data-stu-id="08d84-125">You can also use the "D *n* " or "X *n* " format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="08d84-126">O exemplo a seguir acrescenta um valor inteiro com cinco dígitos zero à esquerda.</span><span class="sxs-lookup"><span data-stu-id="08d84-126">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="08d84-127">Para acrescentar um valor numérico com zeros à esquerda com comprimento específico</span><span class="sxs-lookup"><span data-stu-id="08d84-127">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="08d84-128">Determine quantos dígitos a representação da cadeia de caracteres de números deve ter à esquerda dos decimais.</span><span class="sxs-lookup"><span data-stu-id="08d84-128">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="08d84-129">Inclua os dígitos zero à esquerda no número total de dígitos.</span><span class="sxs-lookup"><span data-stu-id="08d84-129">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="08d84-130">Defina uma cadeia de caracteres de formato numérico personalizado que usa o espaço reservado para zero “0” para representar a quantidade mínima de dígitos zero.</span><span class="sxs-lookup"><span data-stu-id="08d84-130">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="08d84-131">Chame o método `ToString(String)` do número e apresente-o à cadeia de caracteres de formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="08d84-131">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="08d84-132">Você também pode usar uma cadeia de caracteres de formato personalizado com interpolação de cadeia de caracteres ou um método com suporte para formatação de composição.</span><span class="sxs-lookup"><span data-stu-id="08d84-132">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="08d84-133">O exemplo a seguir formata diversos valores numéricos com zeros à esquerda.</span><span class="sxs-lookup"><span data-stu-id="08d84-133">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="08d84-134">Como resultado, o comprimento total do número formatado é pelo menos oito dígitos à esquerda do separador decimal.</span><span class="sxs-lookup"><span data-stu-id="08d84-134">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="08d84-135">Para acrescentar um valor numérico com uma determinada quantidade de zeros à esquerda</span><span class="sxs-lookup"><span data-stu-id="08d84-135">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="08d84-136">Determine quantos zeros à esquerda o valor numérico deve ter.</span><span class="sxs-lookup"><span data-stu-id="08d84-136">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="08d84-137">Determine a quantidade de dígitos à esquerda do decimal na cadeia de caracteres numéricos não preenchida:</span><span class="sxs-lookup"><span data-stu-id="08d84-137">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="08d84-138">Determine se a representação da cadeia de caracteres de um número inclui um símbolo de ponto decimal.</span><span class="sxs-lookup"><span data-stu-id="08d84-138">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="08d84-139">Caso o símbolo esteja presente, determine a quantidade de caracteres à esquerda do ponto decimal.</span><span class="sxs-lookup"><span data-stu-id="08d84-139">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="08d84-140">-ou-</span><span class="sxs-lookup"><span data-stu-id="08d84-140">-or-</span></span>

         <span data-ttu-id="08d84-141">Caso o símbolo de decimal não esteja presente, determine o comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="08d84-141">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="08d84-142">Crie uma cadeia de caracteres de formato personalizado que use:</span><span class="sxs-lookup"><span data-stu-id="08d84-142">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="08d84-143">O espaço reservado para zero “0” para cada um dos zeros à esquerda que aparecem na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="08d84-143">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="08d84-144">O espaço reservado para zero ou o espaço reservado de dígito “#” para representar cada dígito na cadeia de caracteres padrão.</span><span class="sxs-lookup"><span data-stu-id="08d84-144">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="08d84-145">Forneça a cadeia de caracteres de formato personalizado como parâmetro para o método `ToString(String)` do número ou para um método que use a formatação composta.</span><span class="sxs-lookup"><span data-stu-id="08d84-145">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="08d84-146">O exemplo a seguir acrescenta dois valores <xref:System.Double> com cinco dígitos zero à esquerda.</span><span class="sxs-lookup"><span data-stu-id="08d84-146">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="08d84-147">Veja também</span><span class="sxs-lookup"><span data-stu-id="08d84-147">See also</span></span>

- [<span data-ttu-id="08d84-148">Cadeias de caracteres de formato numérico personalizado</span><span class="sxs-lookup"><span data-stu-id="08d84-148">Custom Numeric Format Strings</span></span>](custom-numeric-format-strings.md)
- [<span data-ttu-id="08d84-149">Cadeias de Caracteres de Formato Numérico Padrão</span><span class="sxs-lookup"><span data-stu-id="08d84-149">Standard Numeric Format Strings</span></span>](standard-numeric-format-strings.md)
- [<span data-ttu-id="08d84-150">Formatação composta</span><span class="sxs-lookup"><span data-stu-id="08d84-150">Composite Formatting</span></span>](composite-formatting.md)

---
title: "Como preencher um número com zeros à esquerda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6266807a01e8119ae1410a1ba09cab55c788b4d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="4c3a4-102">Como preencher um número com zeros à esquerda</span><span class="sxs-lookup"><span data-stu-id="4c3a4-102">How to: Pad a Number with Leading Zeros</span></span>
<span data-ttu-id="4c3a4-103">É possível adicionar zeros à esquerda de um inteiro usando a [cadeia de caracteres de formato numérico padrão](../../../docs/standard/base-types/standard-numeric-format-strings.md) “D” com um especificador de precisão.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="4c3a4-104">Você pode adicionar zeros à esquerda de inteiros e pontos flutuantes usando uma [cadeia de caracteres de formato numérico personalizado](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="4c3a4-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="4c3a4-105">Este tópico mostra como usar os dois métodos para acrescentar um número com zeros à esquerda.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-105">This topic shows how to use both methods to pad a number with leading zeros.</span></span>  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="4c3a4-106">Para acrescentar um número inteiro com zeros à esquerda com um comprimento específico</span><span class="sxs-lookup"><span data-stu-id="4c3a4-106">To pad an integer with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="4c3a4-107">Determine o número mínimo de dígitos que o valor inteiro deve exibir.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="4c3a4-108">Inclua os dígitos à esquerda nesse número.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-108">Include any leading digits in this number.</span></span>  
  
2.  <span data-ttu-id="4c3a4-109">Determine se quer exibir o inteiro como valor decimal ou hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    -   <span data-ttu-id="4c3a4-110">Para exibir o número inteiro como um valor decimal, chame seu `ToString(String)` método e passe a cadeia de caracteres "D*n*" como o valor da `format` parâmetro, onde  *n*  representa o comprimento mínimo da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    -   <span data-ttu-id="4c3a4-111">Para exibir o número inteiro como um valor hexadecimal, chame seu `ToString(String)` método e passe a cadeia de caracteres "X*n*" como o valor da `format` parâmetro, onde  *n*  representa o comprimento mínimo da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
     <span data-ttu-id="4c3a4-112">Você também pode usar a cadeia de caracteres de formato em um método, como <xref:System.String.Format%2A> ou <xref:System.Console.WriteLine%2A>, que usa [formatação composta](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="4c3a4-112">You can also use the format string in a method, such as <xref:System.String.Format%2A> or <xref:System.Console.WriteLine%2A>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="4c3a4-113">O exemplo a seguir formata diversos valores inteiros com zeros à esquerda para que o comprimento total do número formatado tenha pelo menos oito caracteres.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="4c3a4-114">Para acrescentar um número inteiro com uma determinada quantidade de zeros à esquerda</span><span class="sxs-lookup"><span data-stu-id="4c3a4-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="4c3a4-115">Determine quantos zeros à esquerda o valor inteiro deve exibir.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
2.  <span data-ttu-id="4c3a4-116">Determine se quer exibir o inteiro como valor decimal ou hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span> <span data-ttu-id="4c3a4-117">A formatação como valor decimal requer o uso de um especificador de formato padrão “D”; já a formatação como valor hexadecimal exige que você use o especificador de formato padrão “X”.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-117">Formatting it as a decimal value requires that you use the "D" standard format specifier; formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>  
  
3.  <span data-ttu-id="4c3a4-118">Determine o comprimento da cadeia de caracteres numérica não acrescentada. Para isso, chame o método `ToString("D").Length` ou `ToString("X").Length` do valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-118">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>  
  
4.  <span data-ttu-id="4c3a4-119">Adicione quantos dígitos zero à esquerda quer incluir na cadeia de caracteres formatada com comprimento da cadeia de caracteres numérica não acrescentada.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-119">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="4c3a4-120">Isso define o comprimento total da cadeia de caracteres acrescentada.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-120">This defines the total length of the padded string.</span></span>  
  
5.  <span data-ttu-id="4c3a4-121">Chamar o valor de inteiro `ToString(String)` método e passe a cadeia de caracteres "D*n*" para cadeias de caracteres decimais e "X*n*" para cadeias de caracteres hexadecimais, onde  *n*  representa o comprimento total da cadeia de caracteres preenchido.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-121">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="4c3a4-122">Você também pode usar o "D*n*" ou "X*n*" formato de cadeia de caracteres em um método que dá suporte à formatação composta.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-122">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="4c3a4-123">O exemplo a seguir acrescenta um valor inteiro com cinco dígitos zero à esquerda.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-123">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="4c3a4-124">Para acrescentar um valor numérico com zeros à esquerda com comprimento específico</span><span class="sxs-lookup"><span data-stu-id="4c3a4-124">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="4c3a4-125">Determine quantos dígitos a representação da cadeia de caracteres de números deve ter à esquerda dos decimais.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-125">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="4c3a4-126">Inclua os dígitos zero à esquerda no número total de dígitos.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-126">Include any leading zeros in this total number of digits.</span></span>  
  
2.  <span data-ttu-id="4c3a4-127">Defina uma cadeia de caracteres de formato numérico personalizado que usa o espaço reservado com valor zero (“0”) para representar a quantidade mínima de dígitos zero.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-127">Define a custom numeric format string that uses the zero placeholder ("0") to represent the minimum number of zeros.</span></span>  
  
3.  <span data-ttu-id="4c3a4-128">Chame o método `ToString(String)` do número e apresente-o à cadeia de caracteres de formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-128">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="4c3a4-129">Você também pode usar uma cadeia de caracteres de formato personalizado com um método compatível com formatação de composição.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-129">You can also use the custom format string with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="4c3a4-130">O exemplo a seguir formata diversos valores numéricos com zeros à esquerda para que o comprimento total do número formatado tenha pelo menos oito caracteres à esquerda do decimal.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-130">The following example formats several numeric values with leading zeros so that the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="4c3a4-131">Para acrescentar um valor numérico com uma determinada quantidade de zeros à esquerda</span><span class="sxs-lookup"><span data-stu-id="4c3a4-131">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="4c3a4-132">Determine quantos zeros à esquerda o valor numérico deve ter.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-132">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
2.  <span data-ttu-id="4c3a4-133">Determine a quantidade de dígitos à esquerda do decimal na cadeia de caracteres numéricos não acrescentada.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-133">Determine the number of digits to the left of the decimal in the unpadded numeric string.</span></span> <span data-ttu-id="4c3a4-134">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="4c3a4-134">To do this:</span></span>  
  
    1.  <span data-ttu-id="4c3a4-135">Determine se a representação da cadeia de caracteres de um número inclui um símbolo de ponto decimal.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-135">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    2.  <span data-ttu-id="4c3a4-136">Caso o símbolo esteja presente, determine a quantidade de caracteres à esquerda do ponto decimal.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-136">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="4c3a4-137">- ou -</span><span class="sxs-lookup"><span data-stu-id="4c3a4-137">-or-</span></span>  
  
         <span data-ttu-id="4c3a4-138">Caso o símbolo não esteja presente, determine o comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-138">If it does not include a decimal point symbol, determine the string's length.</span></span>  
  
3.  <span data-ttu-id="4c3a4-139">Crie uma cadeia de caracteres de formato personalizado que use o espaço reservado zero ("0") para que cada um dos dígitos zero à esquerda apareça na cadeia de caracteres e que use o espaço reservado zero ou de dígito ("#") para representar cada dígito na cadeia de caracteres padrão.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-139">Create a custom format string that uses the zero placeholder ("0") for each of the leading zeros to appear in the string, and that uses either the zero placeholder or the digit placeholder ("#") to represent each digit in the default string.</span></span>  
  
4.  <span data-ttu-id="4c3a4-140">Forneça a cadeia de caracteres de formato personalizado como parâmetro para o método `ToString(String)` do número ou para um método que use a formatação composta.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-140">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="4c3a4-141">O exemplo a seguir acrescenta dois valores <xref:System.Double> com cinco dígitos zero à esquerda.</span><span class="sxs-lookup"><span data-stu-id="4c3a4-141">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4c3a4-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c3a4-142">See Also</span></span>  
 [<span data-ttu-id="4c3a4-143">Cadeias de caracteres de formato numérico personalizado</span><span class="sxs-lookup"><span data-stu-id="4c3a4-143">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [<span data-ttu-id="4c3a4-144">Cadeias de Caracteres de Formato Numérico Padrão</span><span class="sxs-lookup"><span data-stu-id="4c3a4-144">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="4c3a4-145">Formatação de composição</span><span class="sxs-lookup"><span data-stu-id="4c3a4-145">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)

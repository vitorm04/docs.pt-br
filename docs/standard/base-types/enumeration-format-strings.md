---
title: Cadeias de caracteres de formato de enumeração – .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
ms.openlocfilehash: 316c042b05e505b3e3e857ea41ae808a2a0282f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126417"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="96144-102">Cadeias de caracteres de formato de enumeração</span><span class="sxs-lookup"><span data-stu-id="96144-102">Enumeration format strings</span></span>

<span data-ttu-id="96144-103">Você pode usar o método <xref:System.Enum.ToString%2A?displayProperty=nameWithType> para criar um novo objeto de cadeia de caracteres que representa o valor numérico, hexadecimal ou de cadeia de caracteres de um membro da enumeração.</span><span class="sxs-lookup"><span data-stu-id="96144-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="96144-104">Esse método usa uma das cadeias de caracteres de formatação de enumeração para especificar o valor que você deseja que seja retornado.</span><span class="sxs-lookup"><span data-stu-id="96144-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="96144-105">As seções a seguir listam as cadeias de caracteres de formatação de enumeração e os valores que elas retornam.</span><span class="sxs-lookup"><span data-stu-id="96144-105">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="96144-106">Esses especificadores de formato não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="96144-106">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="96144-107">"G" ou "g"</span><span class="sxs-lookup"><span data-stu-id="96144-107">G or g</span></span>

<span data-ttu-id="96144-108">Exibem a entrada de enumeração como um valor de cadeia de caracteres. Caso contrário, é exibido o valor inteiro da instância atual.</span><span class="sxs-lookup"><span data-stu-id="96144-108">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="96144-109">Se a enumeração for definida com o atributo **Flags** definido, os valores da cadeia de caracteres de cada entrada válida serão concatenados, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="96144-109">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="96144-110">Se o atributo **Flags** não estiver definido, um valor inválido será exibido como uma entrada numérica.</span><span class="sxs-lookup"><span data-stu-id="96144-110">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="96144-111">O exemplo a seguir ilustra o especificador de formato G.</span><span class="sxs-lookup"><span data-stu-id="96144-111">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="96144-112">F ou f</span><span class="sxs-lookup"><span data-stu-id="96144-112">F or f</span></span>

<span data-ttu-id="96144-113">Exibem a entrada de enumeração como um valor de cadeia de caracteres, se possível.</span><span class="sxs-lookup"><span data-stu-id="96144-113">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="96144-114">Se o valor puder ser exibido totalmente como uma soma das entradas na enumeração (mesmo que o atributo **Flags** não esteja presente), os valores da cadeia de caracteres de cada entrada válida serão concatenados, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="96144-114">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="96144-115">Se não puder ser determinado completamente pelas entradas de enumeração, o valor será formatado como valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="96144-115">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="96144-116">O exemplo a seguir ilustra o especificador de formato F.</span><span class="sxs-lookup"><span data-stu-id="96144-116">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="96144-117">D ou d</span><span class="sxs-lookup"><span data-stu-id="96144-117">D or d</span></span>

<span data-ttu-id="96144-118">Exibem a entrada de enumeração como um valor inteiro na representação mais curta possível.</span><span class="sxs-lookup"><span data-stu-id="96144-118">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="96144-119">O exemplo a seguir ilustra o especificador de formato D.</span><span class="sxs-lookup"><span data-stu-id="96144-119">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="96144-120">"X" ou "x"</span><span class="sxs-lookup"><span data-stu-id="96144-120">X or x</span></span>

<span data-ttu-id="96144-121">Exibe a entrada de enumeração como um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="96144-121">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="96144-122">O valor é representado com zeros à esquerda conforme o necessário, para garantir que a cadeia de caracteres resultante tenha dois caracteres para cada byte no tipo de enumeração [tipo numérico subjacente](xref:System.Enum.GetUnderlyingType%2A).</span><span class="sxs-lookup"><span data-stu-id="96144-122">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="96144-123">O exemplo a seguir ilustra o especificador de formato X.</span><span class="sxs-lookup"><span data-stu-id="96144-123">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="96144-124">No exemplo, o tipo subjacente de <xref:System.ConsoleColor> e <xref:System.IO.FileAttributes> é <xref:System.Int32>, ou um inteiro de 32 bits (ou 4 bytes), que produz uma cadeia de caracteres resultante de oito caracteres.</span><span class="sxs-lookup"><span data-stu-id="96144-124">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]      
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="96144-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96144-125">Example</span></span>

<span data-ttu-id="96144-126">O exemplo a seguir define uma enumeração chamada `Colors`, que consiste em três entradas: `Red`, `Blue` e `Green`.</span><span class="sxs-lookup"><span data-stu-id="96144-126">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="96144-127">Após a enumeração ser definida, uma instância pode ser declarada da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="96144-127">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="96144-128">O método `Color.ToString(System.String)` pode, então, ser usado para exibir o valor da enumeração de diferentes maneiras, dependendo do especificador de formato passado para ele.</span><span class="sxs-lookup"><span data-stu-id="96144-128">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="96144-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96144-129">See also</span></span>

- [<span data-ttu-id="96144-130">Formatando Tipos</span><span class="sxs-lookup"><span data-stu-id="96144-130">Formatting Types</span></span>](formatting-types.md)

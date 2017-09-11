---
title: "Conversões entre cadeias de caracteres e outros tipos (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data type conversion, string
- conversions, type
- string conversion
- conversions, data type
- type conversion, string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 34eb32cb6e640d681db6853aaa164d84acca7e4f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="b4619-102">Conversões entre cadeias de caracteres e outros tipos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4619-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="b4619-103">Você pode converter um numérico, `Boolean`, ou valor de data/hora um `String`.</span><span class="sxs-lookup"><span data-stu-id="b4619-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="b4619-104">Você também pode converter na direção inversa — de um valor de cadeia de caracteres para numérico, `Boolean`, ou `Date` — desde que o conteúdo da cadeia de caracteres pode ser interpretado como um valor válido de tipo de dados de destino.</span><span class="sxs-lookup"><span data-stu-id="b4619-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="b4619-105">Em caso negativo, ocorre um erro de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b4619-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="b4619-106">Conversões de estreitamento são as conversões para todas essas atribuições, em qualquer direção.</span><span class="sxs-lookup"><span data-stu-id="b4619-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="b4619-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span><span class="sxs-lookup"><span data-stu-id="b4619-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="b4619-108">O <xref:Microsoft.VisualBasic.Strings.Format%2A>e <xref:Microsoft.VisualBasic.Conversion.Val%2A>funções fornecem controle adicional sobre conversões entre cadeias de caracteres e números.</xref:Microsoft.VisualBasic.Conversion.Val%2A> </xref:Microsoft.VisualBasic.Strings.Format%2A></span><span class="sxs-lookup"><span data-stu-id="b4619-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="b4619-109">Se você tiver definido uma classe ou estrutura, você pode definir operadores de conversão de tipo entre `String` e o tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="b4619-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="b4619-110">Para obter mais informações, consulte [como: definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b4619-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="b4619-111">Conversão de números em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="b4619-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="b4619-112">Você pode usar o `Format` função para converter um número em uma cadeia de caracteres formatada, que pode incluir não apenas os dígitos apropriados, mas também a formatação de símbolos, como um símbolo de moeda (como `$`), milhares separadores ou *símbolos de agrupamento de dígitos* (como `,`) e um separador decimal (como `.`).</span><span class="sxs-lookup"><span data-stu-id="b4619-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="b4619-113">`Format`utiliza automaticamente os símbolos corretos de acordo com o **opções regionais** as configurações especificadas no Windows **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="b4619-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="b4619-114">Observe que a concatenação (`&`) operador pode converter um número em uma cadeia de caracteres implicitamente, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4619-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="b4619-115">Conversão de cadeias de caracteres em números</span><span class="sxs-lookup"><span data-stu-id="b4619-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="b4619-116">Você pode usar o `Val` função para converter explicitamente os dígitos em uma cadeia de caracteres para um número.</span><span class="sxs-lookup"><span data-stu-id="b4619-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="b4619-117">`Val`lê a cadeia de caracteres até encontrar um caractere que não seja um dígito, espaço, tabulação, alimentação de linha ou período.</span><span class="sxs-lookup"><span data-stu-id="b4619-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="b4619-118">As sequências de "< / S" e "< / H" alterar a base do sistema de número e terminar a verificação.</span><span class="sxs-lookup"><span data-stu-id="b4619-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="b4619-119">Até parar a leitura, `Val` converte todos os caracteres apropriados para um valor numérico.</span><span class="sxs-lookup"><span data-stu-id="b4619-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="b4619-120">Por exemplo, a instrução a seguir retorna o valor `141.825`.</span><span class="sxs-lookup"><span data-stu-id="b4619-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="b4619-121">Quando [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converte uma cadeia de caracteres para um valor numérico, ele usa o **opções regionais** as configurações especificadas no Windows **painel de controle** interpretar milhares separador, o separador decimal e o símbolo de moeda.</span><span class="sxs-lookup"><span data-stu-id="b4619-121">When [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="b4619-122">Isso significa que uma conversão pode terá êxito em uma configuração, mas não em outra.</span><span class="sxs-lookup"><span data-stu-id="b4619-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="b4619-123">Por exemplo, `"$14.20"` é aceitável na localidade inglês (Estados Unidos), mas não em qualquer idioma francês.</span><span class="sxs-lookup"><span data-stu-id="b4619-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4619-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4619-124">See Also</span></span>  
 <span data-ttu-id="b4619-125">[Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="b4619-125">[Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="b4619-126"> [Conversões entre](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="b4619-126"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="b4619-127"> [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="b4619-127"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="b4619-128"> [Como: converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span><span class="sxs-lookup"><span data-stu-id="b4619-128"> [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span></span>  
<span data-ttu-id="b4619-129"> [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="b4619-129"> [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span></span>  
<span data-ttu-id="b4619-130"> [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="b4619-130"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="b4619-131"> [Funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="b4619-131"> [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="b4619-132"> [Introdução a aplicativos internacionais com base no .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)</span><span class="sxs-lookup"><span data-stu-id="b4619-132"> [Introduction to International Applications Based on the .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)</span></span>

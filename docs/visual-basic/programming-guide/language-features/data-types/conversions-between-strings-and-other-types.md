---
title: Conversões entre cadeias de caracteres e outros tipos
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 823931f7d6beb8218e8b99d4a8d45716b7214304
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077144"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="a9fb3-102">Conversões entre cadeias de caracteres e outros tipos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9fb3-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>

<span data-ttu-id="a9fb3-103">Você pode converter um valor numérico, `Boolean` ou de data/hora em um `String` .</span><span class="sxs-lookup"><span data-stu-id="a9fb3-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="a9fb3-104">Você também pode converter na direção inversa — de um valor de cadeia de caracteres para Numeric, `Boolean` ou `Date` – desde que o conteúdo da cadeia de caracteres possa ser interpretado como um valor válido do tipo de dados de destino.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="a9fb3-105">Se não puderem, ocorrerá um erro em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="a9fb3-106">As conversões para todas essas atribuições, em qualquer direção, são conversões redutoras.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="a9fb3-107">Você deve usar as palavras-chave de conversão de tipo ( `CBool` , `CByte` , `CDate` ,,,, `CDbl` `CDec` `CInt` `CLng` , `CSByte` , `CShort` ,,,,, `CSng` `CStr` `CUInt` `CULng` `CUShort` e `CType` ).</span><span class="sxs-lookup"><span data-stu-id="a9fb3-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="a9fb3-108">As <xref:Microsoft.VisualBasic.Strings.Format%2A> <xref:Microsoft.VisualBasic.Conversion.Val%2A> funções e oferecem controle adicional sobre conversões entre cadeias de caracteres e números.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="a9fb3-109">Se você tiver definido uma classe ou estrutura, poderá definir operadores de conversão de tipo entre `String` e o tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="a9fb3-110">Para obter mais informações, consulte [como: definir um operador de conversão](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a9fb3-110">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="a9fb3-111">Conversão de números em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="a9fb3-111">Conversion of Numbers to Strings</span></span>  

 <span data-ttu-id="a9fb3-112">Você pode usar a `Format` função para converter um número em uma cadeia de caracteres formatada, que pode incluir não apenas os dígitos apropriados, mas também os símbolos de formatação, como um símbolo de moeda (como `$` ), separadores de milhares ou *símbolos de agrupamento de dígitos* (como `,` ) e um separador decimal (como `.` ).</span><span class="sxs-lookup"><span data-stu-id="a9fb3-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="a9fb3-113">`Format` o usa automaticamente os símbolos apropriados de acordo com as configurações de **Opções regionais** especificadas no **painel de controle**do Windows.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="a9fb3-114">Observe que o operador concatenation ( `&` ) pode converter um número em uma cadeia de caracteres implicitamente, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="a9fb3-115">Conversão de cadeias de caracteres em números</span><span class="sxs-lookup"><span data-stu-id="a9fb3-115">Conversion of Strings to Numbers</span></span>  

 <span data-ttu-id="a9fb3-116">Você pode usar a `Val` função para converter explicitamente os dígitos em uma cadeia de caracteres em um número.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="a9fb3-117">`Val` lê a cadeia de caracteres até encontrar um caractere que não seja um dígito, espaço, tabulação, alimentação de linha ou ponto.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="a9fb3-118">As sequências "&O" e "&H" alteram a base do sistema numérico e encerram a verificação.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="a9fb3-119">Até que a leitura seja interrompida, `Val` o converte todos os caracteres apropriados em um valor numérico.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="a9fb3-120">Por exemplo, a instrução a seguir retorna o valor `141.825` .</span><span class="sxs-lookup"><span data-stu-id="a9fb3-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="a9fb3-121">Quando Visual Basic converte uma cadeia de caracteres em um valor numérico, ele usa as configurações de **Opções regionais** especificadas no **painel de controle** do Windows para interpretar o separador de milhar, o separador decimal e o símbolo de moeda.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-121">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="a9fb3-122">Isso significa que uma conversão pode ter sucesso em uma configuração, mas não em outra.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="a9fb3-123">Por exemplo, `"$14.20"` é aceitável na localidade inglês (Estados Unidos), mas não em qualquer localidade em francês.</span><span class="sxs-lookup"><span data-stu-id="a9fb3-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9fb3-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="a9fb3-124">See also</span></span>

- [<span data-ttu-id="a9fb3-125">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9fb3-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="a9fb3-126">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="a9fb3-126">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="a9fb3-127">Conversões implícitas e explícitas</span><span class="sxs-lookup"><span data-stu-id="a9fb3-127">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="a9fb3-128">Como converter um objeto em outro tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9fb3-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="a9fb3-129">Conversões de matriz</span><span class="sxs-lookup"><span data-stu-id="a9fb3-129">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="a9fb3-130">Data Types</span><span class="sxs-lookup"><span data-stu-id="a9fb3-130">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="a9fb3-131">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="a9fb3-131">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a9fb3-132">Desenvolver aplicativos localizados e globalizados</span><span class="sxs-lookup"><span data-stu-id="a9fb3-132">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)

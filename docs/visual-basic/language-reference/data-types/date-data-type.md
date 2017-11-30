---
title: Tipo de dados Data (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190b40888dc4a42075b7b6b27bdb1bd403a7efb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="51930-102">Tipo de dados Data (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51930-102">Date Data Type (Visual Basic)</span></span>
<span data-ttu-id="51930-103">Contém os valores de (8 bytes) do IEEE de 64 bits que representam datas desde 1 de janeiro do ano de 0001 até 31 de dezembro do ano 9999 e tempos de 12:00:00 AM (meia-noite) por meio de 11:59:59.9999999 PM.</span><span class="sxs-lookup"><span data-stu-id="51930-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="51930-104">Cada incremento representa 100 nanossegundos de tempo decorrido desde o início de 1º de janeiro do ano 1 no calendário gregoriano.</span><span class="sxs-lookup"><span data-stu-id="51930-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="51930-105">O valor máximo representa 100 nanossegundos antes do início do dia 1º de janeiro do ano 10000.</span><span class="sxs-lookup"><span data-stu-id="51930-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51930-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="51930-106">Remarks</span></span>  
 <span data-ttu-id="51930-107">Use o `Date` tipo de dados para conter valores de data, hora valores ou valores de data e hora.</span><span class="sxs-lookup"><span data-stu-id="51930-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>  
  
 <span data-ttu-id="51930-108">O valor padrão de `Date` é 0:00:00 (meia-noite) em 1º de janeiro de 0001.</span><span class="sxs-lookup"><span data-stu-id="51930-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>  
  
 <span data-ttu-id="51930-109">Você pode obter a data e hora atuais do <xref:Microsoft.VisualBasic.DateAndTime> classe.</span><span class="sxs-lookup"><span data-stu-id="51930-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="51930-110">Requisitos de formato</span><span class="sxs-lookup"><span data-stu-id="51930-110">Format Requirements</span></span>  
 <span data-ttu-id="51930-111">Você deve colocar um `Date` literal entre sinais de número (`# #`).</span><span class="sxs-lookup"><span data-stu-id="51930-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="51930-112">Você deve especificar o valor de data no formato dd/aaaa, por exemplo `#5/31/1993#`, ou AAAA-MM-dd, por exemplo `#1993-5-31#`.</span><span class="sxs-lookup"><span data-stu-id="51930-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="51930-113">Ao especificar o ano pela primeira vez, você pode usar barras.</span><span class="sxs-lookup"><span data-stu-id="51930-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="51930-114">Esse requisito é independente da sua localidade e data do computador e configurações de formato de hora.</span><span class="sxs-lookup"><span data-stu-id="51930-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>  
  
 <span data-ttu-id="51930-115">A razão para essa restrição é que o significado do código nunca deve alterar dependendo da localidade na qual o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="51930-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="51930-116">Suponha que você codificar uma `Date` literal de `#3/4/1998#` e pretende significa 4 de março de 1998.</span><span class="sxs-lookup"><span data-stu-id="51930-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="51930-117">Em uma localidade que utilize dd/mm/aaaa, 4/3/1998 compila como você deseja.</span><span class="sxs-lookup"><span data-stu-id="51930-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="51930-118">Mas suponha que você implantar seu aplicativo em vários países.</span><span class="sxs-lookup"><span data-stu-id="51930-118">But suppose you deploy your application in many countries.</span></span> <span data-ttu-id="51930-119">Em uma localidade que utilize dd/mm/aaaa, a literal embutido seria compilados para 3 de abril de 1998.</span><span class="sxs-lookup"><span data-stu-id="51930-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="51930-120">Em uma localidade que utilize dd/mm/aaaa, literal seria inválido (abril de 1998, 0003) e causa um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="51930-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>  
  
## <a name="workarounds"></a><span data-ttu-id="51930-121">Soluções alternativas</span><span class="sxs-lookup"><span data-stu-id="51930-121">Workarounds</span></span>  
 <span data-ttu-id="51930-122">Para converter um `Date` literal para o formato de sua localidade, ou para um formato personalizado, forneça o literal para o <xref:Microsoft.VisualBasic.Strings.Format%2A> função, especificando um formato de data predefinidos ou definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="51930-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="51930-123">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="51930-123">The following example demonstrates this.</span></span>  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 <span data-ttu-id="51930-124">Como alternativa, você pode usar um dos construtores sobrecarregados do <xref:System.DateTime> estrutura para montar um valor de data e hora.</span><span class="sxs-lookup"><span data-stu-id="51930-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="51930-125">O exemplo a seguir cria um valor para representar a 31 de maio de 1993 em 12:14 à tarde.</span><span class="sxs-lookup"><span data-stu-id="51930-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a><span data-ttu-id="51930-126">Formato de hora</span><span class="sxs-lookup"><span data-stu-id="51930-126">Hour Format</span></span>  
 <span data-ttu-id="51930-127">Você pode especificar o valor de hora no formato de 12 horas ou 24 horas, por exemplo `#1:15:30 PM#` ou `#13:15:30#`.</span><span class="sxs-lookup"><span data-stu-id="51930-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="51930-128">No entanto, se você não especificar os minutos ou segundos, você deve especificar AM ou PM.</span><span class="sxs-lookup"><span data-stu-id="51930-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>  
  
## <a name="date-and-time-defaults"></a><span data-ttu-id="51930-129">Data e hora padrão</span><span class="sxs-lookup"><span data-stu-id="51930-129">Date and Time Defaults</span></span>  
 <span data-ttu-id="51930-130">Se você não incluir uma data em uma literal de data/hora, o Visual Basic define a parte de data do valor 1 de janeiro, 0001.</span><span class="sxs-lookup"><span data-stu-id="51930-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="51930-131">Se você não incluir uma vez em um literal de data/hora, o Visual Basic define a parte de hora do valor para o início do dia, ou seja, meia-noite (0: 00:00).</span><span class="sxs-lookup"><span data-stu-id="51930-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="51930-132">Conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="51930-132">Type Conversions</span></span>  
 <span data-ttu-id="51930-133">Se você converter um `Date` o valor para o `String` tipo, Visual Basic renderiza a data de acordo com o formato de data abreviada especificado pela localidade do tempo de execução e ele renderiza o tempo de acordo com o formato de hora (12 horas ou 24 horas) especificado pelo localidade do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="51930-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="51930-134">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="51930-134">Programming Tips</span></span>  
  
-   <span data-ttu-id="51930-135">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="51930-135">**Interop Considerations.**</span></span> <span data-ttu-id="51930-136">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, tenha em mente que tipos em outros ambientes de data/hora não são compatíveis com o Visual Basic `Date` tipo.</span><span class="sxs-lookup"><span data-stu-id="51930-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="51930-137">Se você estiver passando um argumento de data/hora para um componente, declare-o como `Double` em vez de `Date` no seu novo Visual Basic code e usar os métodos de conversão <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> e <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51930-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="51930-138">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="51930-138">**Type Characters.**</span></span> <span data-ttu-id="51930-139">`Date`não tem o caractere de tipo literal ou caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="51930-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="51930-140">No entanto, o compilador trata literais entre sinais numéricos (`# #`) como `Date`.</span><span class="sxs-lookup"><span data-stu-id="51930-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>  
  
-   <span data-ttu-id="51930-141">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="51930-141">**Framework Type.**</span></span> <span data-ttu-id="51930-142">O tipo correspondente no .NET Framework é a estrutura <xref:System.DateTime?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51930-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51930-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51930-143">Example</span></span>  
 <span data-ttu-id="51930-144">Uma variável ou constante do `Date` tipo de dados contém a data e a hora.</span><span class="sxs-lookup"><span data-stu-id="51930-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="51930-145">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="51930-145">The following example illustrates this.</span></span>  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a><span data-ttu-id="51930-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51930-146">See Also</span></span>  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [<span data-ttu-id="51930-147">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="51930-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="51930-148">Cadeias de caracteres de formato de data e hora padrão</span><span class="sxs-lookup"><span data-stu-id="51930-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [<span data-ttu-id="51930-149">Cadeias de caracteres de formato de data e hora personalizado</span><span class="sxs-lookup"><span data-stu-id="51930-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [<span data-ttu-id="51930-150">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="51930-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="51930-151">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="51930-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="51930-152">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="51930-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

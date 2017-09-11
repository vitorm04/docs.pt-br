---
title: "Como converter uma cadeia de caracteres em um DateTime (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: 21
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
ms.openlocfilehash: 15ef1ec4debf242cdabc42f26add890bd4b61507
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a><span data-ttu-id="6212d-102">Como converter uma cadeia de caracteres em um DateTime (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="6212d-102">How to: Convert a String to a DateTime (C# Programming Guide)</span></span>
<span data-ttu-id="6212d-103">É comum que programas permitam que os usuários insiram datas como valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6212d-103">It is common for programs to enable users to enter dates as string values.</span></span> <span data-ttu-id="6212d-104">Para converter uma data com base em cadeia de caracteres em um objeto <xref:System.DateTime?displayProperty=fullName>, você pode usar o método <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> ou o método estático <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6212d-104">To convert a string-based date to a <xref:System.DateTime?displayProperty=fullName> object, you can use the <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> method or the <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> static method, as shown in the following example.</span></span>  
  
 <span data-ttu-id="6212d-105">**Cultura**.</span><span class="sxs-lookup"><span data-stu-id="6212d-105">**Culture**.</span></span>  <span data-ttu-id="6212d-106">Diferentes culturas do mundo escrevem cadeias de caracteres de data de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="6212d-106">Different cultures in the world write date strings in different ways.</span></span>  <span data-ttu-id="6212d-107">Por exemplo, nos EUA 01/20/2008 é de 20 de janeiro de 2008.</span><span class="sxs-lookup"><span data-stu-id="6212d-107">For example, in the US 01/20/2008 is January 20th, 2008.</span></span>  <span data-ttu-id="6212d-108">Na França, isso gerará uma InvalidFormatException.</span><span class="sxs-lookup"><span data-stu-id="6212d-108">In France this will throw an InvalidFormatException.</span></span> <span data-ttu-id="6212d-109">Isso acontece porque a França lê datas-horas como dia/mês/ano e, nos EUA, é mês/dia/ano.</span><span class="sxs-lookup"><span data-stu-id="6212d-109">This is because France reads date-times as Day/Month/Year, and in the US it is Month/Day/Year.</span></span>  
  
 <span data-ttu-id="6212d-110">Consequentemente, uma cadeia de caracteres como 20/01/2008 será analisada como 20 de janeiro de 2008 na França e, então, gerará uma InvalidFormatException nos EUA.</span><span class="sxs-lookup"><span data-stu-id="6212d-110">Consequently, a string like 20/01/2008 will parse to January 20th, 2008 in France, and then throw an InvalidFormatException in the US.</span></span>  
  
 <span data-ttu-id="6212d-111">Para determinar suas configurações de cultura atuais, você pode usar System.Globalization.CultureInfo.CurrentCulture.</span><span class="sxs-lookup"><span data-stu-id="6212d-111">To determine your current culture settings, you can use System.Globalization.CultureInfo.CurrentCulture.</span></span>  
  
 <span data-ttu-id="6212d-112">Consulte abaixo um exemplo simples de conversão de uma cadeia de caracteres para dateTime.</span><span class="sxs-lookup"><span data-stu-id="6212d-112">See the example below for a simple example of converting a string to dateTime.</span></span>  
  
 <span data-ttu-id="6212d-113">Para obter mais exemplos de cadeias de caracteres de data, consulte <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="6212d-113">For more examples of date strings, see <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>.</span></span>  
  
```csharp  
string dateTime = "01/08/2008 14:50:50.42";  
            DateTime dt = Convert.ToDateTime(dateTime);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond);  
            // Specify exactly how to interpret the string.  
            IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true);  
  
            // Alternate choice: If the string has been input by an end user, you might    
            // want to format it according to the current culture:   
            // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture;  
            DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond  
/* Output (assuming first culture is en-US and second is fr-FR):  
    Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Press any key to continue . . .  
 */  
```  
  
## <a name="example"></a><span data-ttu-id="6212d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6212d-114">Example</span></span>  
 <span data-ttu-id="6212d-115">[!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6212d-115">[!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6212d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6212d-116">See Also</span></span>  
 [<span data-ttu-id="6212d-117">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="6212d-117">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)


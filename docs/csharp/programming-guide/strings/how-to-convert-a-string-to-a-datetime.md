---
title: "Como converter uma cadeia de caracteres em um DateTime (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b459f245f0090fff16918bceb12a0082f6944331
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a>Como converter uma cadeia de caracteres em um DateTime (Guia de Programação em C#)
É comum que programas permitam que os usuários insiram datas como valores de cadeia de caracteres. Para converter uma data com base em cadeia de caracteres em um objeto <xref:System.DateTime?displayProperty=nameWithType>, você pode usar o método <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType> ou o método estático <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType>, conforme mostrado no exemplo a seguir.  
  
 **Cultura**.  Diferentes culturas do mundo escrevem cadeias de caracteres de data de maneiras diferentes.  Por exemplo, nos EUA 01/20/2008 é de 20 de janeiro de 2008.  Na França, isso gerará uma InvalidFormatException. Isso acontece porque a França lê datas-horas como dia/mês/ano e, nos EUA, é mês/dia/ano.  
  
 Consequentemente, uma cadeia de caracteres como 20/01/2008 será analisada como 20 de janeiro de 2008 na França e, então, gerará uma InvalidFormatException nos EUA.  
  
 Para determinar suas configurações de cultura atuais, você pode usar System.Globalization.CultureInfo.CurrentCulture.  
  
 Consulte abaixo um exemplo simples de conversão de uma cadeia de caracteres para dateTime.  
  
 Para obter mais exemplos de cadeias de caracteres de data, consulte <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType>.  
  
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
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)

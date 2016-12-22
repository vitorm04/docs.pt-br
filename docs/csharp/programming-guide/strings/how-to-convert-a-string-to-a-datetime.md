---
title: "Como converter uma cadeia de caracteres em um DateTime (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "cadeias de caracteres [c#], convertendo para DateTIme"
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como converter uma cadeia de caracteres em um DateTime (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

É comum para programas permitir aos usuários inserir datas como valores de cadeia de caracteres. Para converter uma data com base em cadeia de caracteres para um <xref:System.DateTime?displayProperty=fullName> do objeto, você pode usar o <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> método ou o <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> método estático, como mostrado no exemplo a seguir.  
  
 **Cultura**.  Diferentes culturas do mundo escrever cadeias de caracteres de data de maneiras diferentes.  Por exemplo, nos EUA 20\/01\/2008 é de 20 de janeiro de 2008.  França, isso gerará um InvalidFormatException. Isso ocorre porque França lê tempos de data como mês\/dia\/ano e nos Estados Unidos é dia\/mês\/ano.  
  
 Conseqüentemente, uma cadeia de caracteres como 20\/01\/2008 analisará para 20 de janeiro de 2008 na França e depois levantam uma InvalidFormatException nos EUA.  
  
 Para determinar as configurações de cultura atual, você pode usar System.Globalization.CultureInfo.CurrentCulture.  
  
 Consulte o exemplo abaixo para obter um exemplo simple de conversão de uma cadeia de caracteres para dateTime.  
  
 Para obter mais exemplos de cadeias de caracteres de data, consulte <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>.  
  
```c#  
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
  
## Exemplo  
 [!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]  
  
## Consulte também  
 [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md)
---
title: "Tabela de formata&#231;&#227;o de resultados num&#233;ricos (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "formatação [C#]"
  - "formatação numérica [C#]"
  - "Método String.Format"
  - "Método Console.Write"
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tabela de formata&#231;&#227;o de resultados num&#233;ricos (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode formatar resultados numéricos usando o método de <xref:System.String.Format%2A?displayProperty=fullName> , ou o método de <xref:System.Console.Write%2A?displayProperty=fullName> ou de <xref:System.Console.WriteLine%2A?displayProperty=fullName> , que chama `String.Format`.  O formato é especificado usando cadeias de caracteres de formato.  A tabela a seguir contém as cadeias de caracteres suporte de formato padrão.  A cadeia de caracteres de formato tem a seguinte forma: `Axx`, onde `A` é o especificador de formato e `xx` é o especificador de precisão.  O especificador de formato controla o tipo de formatação aplicada ao valor numérico, e o especificador de precisão controla o número de dígitos significativos ou de casas decimais de saída formatados.  O valor do especificador de precisão varia de 0 a 99.  
  
 Para obter mais informações sobre cadeias de caracteres padrão e personalizados de formatação, consulte [Formatando tipos](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md).  Para mais informações sobre o método `String.Format`, consulte <xref:System.String.Format%2A?displayProperty=fullName>.  
  
|Formatar o especificador|Descrição|Exemplos|Saída|  
|------------------------------|---------------|--------------|-----------|  
|C ou c|Moeda|Console.Write \(“{0: C}”, 2,5\);<br /><br /> Console.Write \(“{0: C}”, \-2,5\);|$2.50<br /><br /> \($2.50\)|  
|D ou d|Decimal|Console.Write \(“{0: D5}”, 25\);|00025|  
|E ou e|Científica|Console.Write \(“{0: E}”, 250000\);|2.500000E\+005|  
|F ou f|Ponto fixo|Console.Write \(“{0: F2}”, 25\);<br /><br /> Console.Write \(“{0: F0}”, 25\);|25.00<br /><br /> 25|  
|G ou g|Geral|Console.Write \(“{0: G}”, 2,5\);|2.5|  
|N ou n|Número|Console.Write \(“{0: Em}”, 2500000\);|2,500,000.00|  
|X ou x|Hexadecimal|Console.Write \(“{0: X}”, 250\);<br /><br /> Console.Write \(“{0: X}”, 0xffff\);|FÁ<br /><br /> FFFF|  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Cadeias de caracteres de formato numérico padrão](../Topic/Standard%20Numeric%20Format%20Strings.md)   
 [Tabelas de referência de tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md)
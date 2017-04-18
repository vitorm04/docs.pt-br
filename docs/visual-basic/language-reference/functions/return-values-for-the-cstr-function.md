---
title: "Valores de retorno para a função CStr (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- times, CStr Function return values
- type conversion
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type, converting
- dates [Visual Basic]
- String data type, converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: da48623ee58fdc312a7bddaeb0aa62b2c8c1324a
ms.lasthandoff: 03/13/2017

---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Retornar valores para a função CStr (Visual Basic)
A tabela a seguir descreve os valores de retorno para `CStr` para tipos de dados diferentes de `expression`.  
  
|Se `expression` é do tipo|`CStr`Retorna|  
|-----------------------------|--------------------|  
|[Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Uma cadeia de caracteres contendo "True" ou "False".|  
|[Tipo de Dados de Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|Uma cadeia de caracteres que contém um `Date` valor (data e hora) no formato de data curto do seu sistema.|  
|[Tipos de Dados Numéricos](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Uma cadeia de caracteres que representa o número.|  
  
## <a name="cstr-and-date"></a>Data e CStr  
 O `Date` tipo sempre contém informações de data e hora. Para fins de conversão de tipos, Visual Basic considera 1/1/0001 (1 de janeiro do ano 1) como sendo um *valor neutro* para a data e 00:00:00 (meia-noite) como sendo um valor neutro para a hora. `CStr`não inclui valores neutros na cadeia de caracteres resultante. Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas. No entanto, as informações de data ainda estão presentes no original `Date` valor e pode ser recuperada com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
  
> [!NOTE]
>  O `CStr` função executa suas conversões baseada nas configurações de cultura atual do aplicativo. Para obter a representação de cadeia de caracteres de um número em uma cultura específica, use o número `ToString(IFormatProvider)` método. Por exemplo, use <xref:System.Double.ToString%2A?displayProperty=fullName>ao converter um valor do tipo `Double` para um `String`.</xref:System.Double.ToString%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A></xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Tipo de Dados de Data](../../../visual-basic/language-reference/data-types/date-data-type.md)

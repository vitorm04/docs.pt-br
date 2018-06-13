---
title: Retornar valores para a função CStr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 5312734633eea12aacd7e61afba616d31e06cd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598518"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Retornar valores para a função CStr (Visual Basic)
A tabela a seguir descreve os valores de retorno para `CStr` para diferentes tipos de dados de `expression`.  
  
|Se `expression` é do tipo|Retornos de `CStr`|  
|-----------------------------|--------------------|  
|[Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Uma cadeia de caracteres contendo "True" ou "False".|  
|[Tipo de Dados de Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|Uma cadeia de caracteres que contém um `Date` valor (data e hora) no formato de data curto de seu sistema.|  
|[Tipos de Dados Numéricos](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Uma cadeia de caracteres que representa o número.|  
  
## <a name="cstr-and-date"></a>Data e CStr  
 O `Date` tipo sempre contém informações de data e hora. Para fins de conversão de tipo, Visual Basic considera 1/1/0001 (1 de janeiro do ano 1) como um *valor neutro* para a data e 00:00:00 (meia-noite) deve ser um valor neutro para a hora. `CStr` não inclui valores neutros na cadeia de caracteres resultante. Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado é "9:30:00 AM"; as informações de data são suprimidas. No entanto, as informações de data ainda estão presentes no original `Date` valor e pode ser recuperada com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  O `CStr` função executa a conversão, com base nas configurações de cultura atual do aplicativo. Para obter a representação de cadeia de caracteres de um número em uma cultura específica, use o número `ToString(IFormatProvider)` método. Por exemplo, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> ao converter um valor do tipo `Double` para um `String`.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Tipo de Dados de Data](../../../visual-basic/language-reference/data-types/date-data-type.md)

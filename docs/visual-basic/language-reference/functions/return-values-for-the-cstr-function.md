---
title: Retornar valores para a função CStr
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
ms.openlocfilehash: 4a40777c7290ec6d8c0d032f2edca5d889e20f04
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349998"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Retornar valores para a função CStr (Visual Basic)
A tabela a seguir descreve os valores de retorno para `CStr` para diferentes tipos de dados de `expression`.  
  
|Se `expression` tipo for|Retornos de `CStr`|  
|-----------------------------|--------------------|  
|[Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Uma cadeia de caracteres que contém "true" ou "false".|  
|[Tipo de Dados de Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|Uma cadeia de caracteres que contém um valor de `Date` (data e hora) no formato de data abreviada do seu sistema.|  
|[Tipos de Dados Numéricos](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Uma cadeia de caracteres que representa o número.|  
  
## <a name="cstr-and-date"></a>CStr e Date  
 O tipo de `Date` sempre contém informações de data e hora. Para fins de conversão de tipo, Visual Basic considera 1/1/0001 (1º de Janeiro do ano 1) como um *valor neutro* para a data e 00:00:00 (meia-noite) para ser um valor neutro para o tempo. `CStr` não inclui valores neutros na cadeia de caracteres resultante. Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas. No entanto, as informações de data ainda estão presentes no valor de `Date` original e podem ser recuperadas com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
> A função `CStr` executa sua conversão com base nas configurações de cultura atuais para o aplicativo. Para obter a representação de cadeia de caracteres de um número em uma cultura específica, use o método `ToString(IFormatProvider)` do número. Por exemplo, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> ao converter um valor do tipo `Double` para um `String`.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Tipo de Dados de Data](../../../visual-basic/language-reference/data-types/date-data-type.md)

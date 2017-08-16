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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2d0a5fc7327ecd6339b5021e1b4cb87cc54bd2bc
ms.lasthandoff: 03/13/2017

---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Conversões entre cadeias de caracteres e outros tipos (Visual Basic)
Você pode converter um numérico, `Boolean`, ou valor de data/hora um `String`. Você também pode converter na direção inversa — de um valor de cadeia de caracteres para numérico, `Boolean`, ou `Date` — desde que o conteúdo da cadeia de caracteres pode ser interpretado como um valor válido de tipo de dados de destino. Em caso negativo, ocorre um erro de tempo de execução.  
  
 Conversões de estreitamento são as conversões para todas essas atribuições, em qualquer direção. You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`). O <xref:Microsoft.VisualBasic.Strings.Format%2A>e <xref:Microsoft.VisualBasic.Conversion.Val%2A>funções fornecem controle adicional sobre conversões entre cadeias de caracteres e números.</xref:Microsoft.VisualBasic.Conversion.Val%2A> </xref:Microsoft.VisualBasic.Strings.Format%2A>  
  
 Se você tiver definido uma classe ou estrutura, você pode definir operadores de conversão de tipo entre `String` e o tipo de sua classe ou estrutura. Para obter mais informações, consulte [como: definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Conversão de números em cadeias de caracteres  
 Você pode usar o `Format` função para converter um número em uma cadeia de caracteres formatada, que pode incluir não apenas os dígitos apropriados, mas também a formatação de símbolos, como um símbolo de moeda (como `$`), milhares separadores ou *símbolos de agrupamento de dígitos* (como `,`) e um separador decimal (como `.`). `Format`utiliza automaticamente os símbolos corretos de acordo com o **opções regionais** as configurações especificadas no Windows **painel de controle**.  
  
 Observe que a concatenação (`&`) operador pode converter um número em uma cadeia de caracteres implicitamente, como mostra o exemplo a seguir.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Conversão de cadeias de caracteres em números  
 Você pode usar o `Val` função para converter explicitamente os dígitos em uma cadeia de caracteres para um número. `Val`lê a cadeia de caracteres até encontrar um caractere que não seja um dígito, espaço, tabulação, alimentação de linha ou período. As sequências de "< / S" e "< / H" alterar a base do sistema de número e terminar a verificação. Até parar a leitura, `Val` converte todos os caracteres apropriados para um valor numérico. Por exemplo, a instrução a seguir retorna o valor `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Quando [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converte uma cadeia de caracteres para um valor numérico, ele usa o **opções regionais** as configurações especificadas no Windows **painel de controle** interpretar milhares separador, o separador decimal e o símbolo de moeda. Isso significa que uma conversão pode terá êxito em uma configuração, mas não em outra. Por exemplo, `"$14.20"` é aceitável na localidade inglês (Estados Unidos), mas não em qualquer idioma francês.  
  
## <a name="see-also"></a>Consulte também  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões entre](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Como: converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Introdução a aplicativos internacionais com base no .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)

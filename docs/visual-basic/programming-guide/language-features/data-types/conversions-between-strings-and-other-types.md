---
title: Conversões entre cadeias de caracteres e outros tipos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 38acd9056f9517e6d8b62691cdeb1a2960bec800
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42998704"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Conversões entre cadeias de caracteres e outros tipos (Visual Basic)
Você pode converter um numérico `Boolean`, ou valor de data/hora um `String`. Você também pode converter na direção inversa — de um valor de cadeia de caracteres para numérico, `Boolean`, ou `Date` — desde que o conteúdo da cadeia de caracteres pode ser interpretado como um valor válido do tipo de dados de destino. Em caso negativo, ocorrerá um erro de tempo de execução.  
  
 As conversões para todas as essas atribuições, em qualquer direção, são conversões de estreitamento. Você deve usar as palavras-chave de conversão de tipo (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, e `CType`). O <xref:Microsoft.VisualBasic.Strings.Format%2A> e <xref:Microsoft.VisualBasic.Conversion.Val%2A> funções oferecem controle adicional sobre as conversões entre cadeias de caracteres e números.  
  
 Se você tiver definido uma classe ou estrutura, você pode definir operadores de conversão de tipo entre `String` e o tipo de sua classe ou estrutura. Para obter mais informações, consulte [como: definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Conversão de números em cadeias de caracteres  
 Você pode usar o `Format` função para converter um número em uma cadeia de caracteres formatada, que pode incluir não apenas os dígitos apropriados, mas também a formatação de símbolos, como um símbolo de moeda (como `$`), milhares separadores ou *agrupamento de dígitos símbolos* (como `,`) e um separador decimal (como `.`). `Format` usa automaticamente os símbolos apropriados de acordo com o **opções regionais** as configurações especificadas no Windows **painel de controle**.  
  
 Observe que a concatenação (`&`) operador pode converter um número em uma cadeia de caracteres implicitamente, como mostra o exemplo a seguir.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Conversão de cadeias de caracteres em números  
 Você pode usar o `Val` função para converter explicitamente os dígitos em uma cadeia de caracteres em um número. `Val` lê a cadeia de caracteres até encontrar um caractere que não seja um dígito, espaço, tabulação, alimentação de linha ou período. As sequências de "& S" e "& H" alterar a base do sistema de número e terminar o processo de verificação. Até que ele interrompe a leitura, `Val` converte todos os caracteres apropriados para um valor numérico. Por exemplo, a instrução a seguir retorna o valor `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Quando o Visual Basic converte uma cadeia de caracteres para um valor numérico, ele usa o **opções regionais** as configurações especificadas no Windows **painel de controle** interpretar milhares separador, o separador decimal, e símbolo de moeda. Isso significa que uma conversão pode ter êxito em uma configuração, mas não em outro. Por exemplo, `"$14.20"` é aceitável na localidade inglês (Estados Unidos), mas não em qualquer localidade francês.  
  
## <a name="see-also"></a>Consulte também  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Como: converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)  
 [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Introdução a aplicativos internacionais com base no .NET Framework](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)

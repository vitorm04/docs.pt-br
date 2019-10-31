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
ms.openlocfilehash: 06dabbb5d5dfbfb545f01afb157fd532ca0551df
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197339"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Conversões entre cadeias de caracteres e outros tipos (Visual Basic)
Você pode converter um valor numérico, `Boolean` ou de data/hora em um `String`. Você também pode converter na direção inversa — de um valor de cadeia de caracteres para Numeric, `Boolean` ou `Date` – desde que o conteúdo da cadeia de caracteres possa ser interpretado como um valor válido do tipo de dados de destino. Se não puderem, ocorrerá um erro em tempo de execução.  
  
 As conversões para todas essas atribuições, em qualquer direção, são conversões redutoras. Você deve usar as palavras-chave de conversão de tipo (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, 0, 1, 2 , 3 e 4). As funções <xref:Microsoft.VisualBasic.Strings.Format%2A> e <xref:Microsoft.VisualBasic.Conversion.Val%2A> fornecem controle adicional sobre conversões entre cadeias de caracteres e números.  
  
 Se você tiver definido uma classe ou estrutura, poderá definir operadores de conversão de tipo entre `String` e o tipo de sua classe ou estrutura. Para obter mais informações, consulte [como: definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Conversão de números em cadeias de caracteres  
 Você pode usar a função `Format` para converter um número em uma cadeia de caracteres formatada, que pode incluir não apenas os dígitos apropriados, mas também os símbolos de formatação, como um símbolo de moeda (como `$`), milhares de separadores ou *símbolos de agrupamento de dígitos* (como @no __t_3) e um separador decimal (como `.`). `Format` usa automaticamente os símbolos apropriados de acordo com as configurações de **Opções regionais** especificadas no **painel de controle**do Windows.  
  
 Observe que o operador concatenação (`&`) pode converter um número em uma cadeia de caracteres implicitamente, como mostra o exemplo a seguir.  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Conversão de cadeias de caracteres em números  
 Você pode usar a função `Val` para converter explicitamente os dígitos em uma cadeia de caracteres em um número. `Val` lê a cadeia de caracteres até encontrar um caractere diferente de dígito, espaço, tabulação, alimentação de linha ou ponto. As sequências "& O" e "& H" alteram a base do sistema numérico e encerram a verificação. Até que a leitura seja interrompida, `Val` converte todos os caracteres apropriados em um valor numérico. Por exemplo, a instrução a seguir retorna o valor `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Quando Visual Basic converte uma cadeia de caracteres em um valor numérico, ele usa as configurações de **Opções regionais** especificadas no **painel de controle** do Windows para interpretar o separador de milhar, o separador decimal e o símbolo de moeda. Isso significa que uma conversão pode ter sucesso em uma configuração, mas não em outra. Por exemplo, `"$14.20"` é aceitável na localidade inglês (Estados Unidos), mas não em qualquer localidade em francês.  
  
## <a name="see-also"></a>Consulte também

- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Como converter um objeto em outro tipo em Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Desenvolver aplicativos globalizados e localizados](/visualstudio/ide/globalizing-and-localizing-applications)

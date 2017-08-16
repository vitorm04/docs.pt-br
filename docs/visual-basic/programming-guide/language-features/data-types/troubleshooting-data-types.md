---
title: Solucionando problemas de tipos de dados (Visual Basic) | Documentos do Microsoft
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
- Char data type, converting
- Decimal data type, conversions
- data types [Visual Basic], troubleshooting
- literals, default types
- type characters, literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types
- floating-point numbers, precision
- Boolean data type, converting
- literal types
- literal type characters
- floating-point numbers, imprecision
- String data type, converting
- floating-point numbers, comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: 29
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
ms.openlocfilehash: cfb8fc77d3e0d85ef795a94fc95ab61a8f68ff39
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-data-types-visual-basic"></a>Solucionando problemas de tipos de dados (Visual Basic)
Esta página lista alguns problemas comuns que podem ocorrer ao executar operações em tipos de dados intrínseco.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>Expressões de ponto flutuante não comparados como iguais  
 Quando você trabalha com números de ponto flutuante ([único tipo de dados](../../../../visual-basic/language-reference/data-types/single-data-type.md) e [tipo de dados Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)), lembre-se de que eles são armazenados como frações binárias. Isso significa que eles não podem manter uma representação exata de qualquer quantidade que não seja uma fração binária (do formulário k / (2 ^ n) onde k e n são números inteiros). Por exemplo, 0,5 (= 1/2) e 0.3125 (= 5/16) podem ser mantidos como valores precisos, enquanto 0.2 (= 1/5) e 0,3 (= 3/10) podem ser apenas aproximações.  
  
 Devido a essa imprecisão, você não pode depender resultados exatos quando opera com valores de ponto flutuante. Em particular, dois valores que são, teoricamente, iguais podem ter representações ligeiramente diferentes.  
  
| Para comparar as quantidades de ponto flutuantes | 
|---| 
|1.  Calcular o valor absoluto de seu diferença usando o <xref:System.Math.Abs%2A>método o <xref:System.Math>classe o <xref:System>namespace.</xref:System> </xref:System.Math> </xref:System.Math.Abs%2A><br />2.  Determine uma diferença máxima aceitável, de modo que você pode considerar as duas quantidades como iguais para fins práticos se da diferença não for maior.<br />3.  Compare o valor absoluto da diferença com a diferença aceitável.|  
  
 O exemplo a seguir demonstra comparações correta e incorreta entre dois `Double` valores.  
  
 [!code-vb[VbVbalrDataTypes n º&10;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 O exemplo anterior usa o <xref:System.Double.ToString%2A>método o <xref:System.Double>estrutura para que ele possa especificar melhor precisão que o `CStr` palavra-chave usa.</xref:System.Double> </xref:System.Double.ToString%2A> O padrão é 15 dígitos, mas o formato "G17" estende a até 17 dígitos.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Operador Mod não retorna resultados precisos  
 Devido à imprecisão de armazenamento de ponto flutuante, o [operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md) poderá retornar um resultado inesperado quando pelo menos um dos operandos for ponto flutuante.  
  
 O [tipo de dados Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) não usa representação de ponto flutuante. Muitos números que são inexatos em `Single` e `Double` são exatos em `Decimal` (por exemplo 0.2 e 0,3). Embora a aritmética seja mais lenta em `Decimal` que em ponto flutuante, talvez valha a redução de desempenho para obter melhor precisão.  
  
|Para localizar o resto inteiro de quantidades de ponto flutuantes|  
|---|  
|1.  Declare as variáveis como `Decimal`.<br />2.  Use o caractere de tipo literal `D` para forçar literais a `Decimal`, caso os valores sejam muito grandes para o `Long` tipo de dados.|  
  
 O exemplo a seguir demonstra a imprecisão potencial de operandos de ponto flutuantes.  
  
 [!code-vb[VbVbalrDataTypes n º&11;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 O exemplo anterior usa o <xref:System.Double.ToString%2A>método o <xref:System.Double>estrutura para que ele possa especificar melhor precisão que o `CStr` palavra-chave usa.</xref:System.Double> </xref:System.Double.ToString%2A> O padrão é 15 dígitos, mas o formato "G17" estende a até 17 dígitos.  
  
 Porque `zeroPointTwo` é `Double`, seu valor 0,2 é uma fração binária infinitamente de repetição com um valor armazenado de 0.20000000000000001. A divisão 2.0 por essa quantidade produz 9.9999999999999995 com resto 0.19999999999999991.  
  
 Em uma expressão para `decimalRemainder`, o caractere de tipo literal `D` força ambos os operandos para `Decimal`, e 0.2 tem uma representação exata. Portanto, o `Mod` operador produz o resto 0.0 esperado.  
  
 Observe que não é suficiente declarar `decimalRemainder` como `Decimal`. Você também deve forçar os literais para `Decimal`, ou eles usam `Double` por padrão e `decimalRemainder` recebe o mesmo valor como `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>Tipo booleano não converte para tipo numérico com precisão  
 [Tipo de dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) valores não são armazenados como números, e não são os valores armazenados sejam equivalentes a números. Para compatibilidade com versões anteriores, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece palavras-chave de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`, e assim por diante) para converter entre `Boolean` e tipos numéricos. No entanto, outras linguagens, às vezes, executam essas conversões diferente, como o [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] métodos.  
  
 Você nunca deve escrever código que dependa de valores numéricos equivalentes para `True` e `False`. Sempre que possível, você deve restringir o uso de `Boolean` variáveis para os valores lógicos para que elas são criadas. Se você deve combinar `Boolean` e valores numéricos, certifique-se de que você entende o método de conversão que você selecionar.  
  
### <a name="conversion-in-visual-basic"></a>Conversão em Visual Basic  
 Quando você usa o `CType` ou `CBool` palavras-chave de conversão para converter tipos de dados numéricos para `Boolean`, 0 se torna `False` e todos os outros valores tornam-se `True`. Quando você converte `Boolean` valores para tipos numéricos usando as palavras-chave de conversão, `False` se torna 0 e `True` torna-se -1.  
  
### <a name="conversion-in-the-framework"></a>Conversão no Framework  
 O <xref:System.Convert.ToInt32%2A>método o <xref:System.Convert>classe o <xref:System>namespace converte `True` para +&1;.</xref:System> </xref:System.Convert> </xref:System.Convert.ToInt32%2A>  
  
 Se você deve converter um `Boolean` o valor para um tipo de dados numérico, tome cuidado sobre que método de conversão usar.  
  
## <a name="character-literal-generates-compiler-error"></a>Caractere Literal gera erro do compilador  
 Na ausência de qualquer caracteres de tipo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pressupõe padrão de tipos de dados literais. O tipo de padrão de um caractere literal — entre aspas (`" "`) — é `String`.  
  
 O `String` tipo de dados não amplia para o [tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md). Isso significa que, se você quiser atribuir um literal para uma `Char` variável, você deve fazer uma conversão de restrição ou forçar o literal para o `Char` tipo.  

|Para criar um caractere literal para atribuir a uma variável ou constante|
|---|  
|1.  Declarar a variável ou constante como `Char`.<br />2.  Coloque o valor de caractere entre aspas (`" "`).<br />3.  Siga as aspas duplas de fechamento do caracter de tipo literal `C` para forçar o literal para `Char`. Isso é necessário se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `On`, e é desejável em qualquer caso.|  
  
 O exemplo a seguir demonstra atribuições bem e malsucedidas sucedidas de um literal para um `Char` variável.  
  
 [!code-vb[VbVbalrDataTypes&#12;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 Sempre há um risco usando conversões de redução, pois elas podem falhar em tempo de execução. Por exemplo, uma conversão de `String` para `Char` pode falhar se o `String` valor contiver mais de um caractere. Portanto, é melhor programação para usar o `C` caractere de tipo.  
  
## <a name="string-conversion-fails-at-run-time"></a>Falha na conversão de cadeia de caracteres em tempo de execução  
 O [tipo de dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md) participa de poucas conversões ampliadoras. `String`amplia somente a mesmo e `Object`e apenas `Char` e `Char()` (uma `Char` matriz) amplia para `String`. Isso ocorre porque `String` variáveis e constantes podem conter valores que outros tipos de dados não podem conter.  
  
 Quando a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `On`, o compilador proíbe todas as conversões de estreitamento implícitas. Isso inclui aquelas envolvendo `String`. Seu código pode ainda usar palavras-chave de conversão como `CStr` e [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md), quais direta a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] a tentar a conversão.  
  
> [!NOTE]
>  O erro de conversão de estreitamento será suprimido para conversões de elementos em um `For Each…Next` coleção para a variável de controle de loop. Para obter mais informações e exemplos, consulte a seção "Conversões de estreitamento" [para cada uma... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Restringir a proteção de conversão  
 A desvantagem de conversões de estreitamento é que eles podem falhar em tempo de execução. Por exemplo, se um `String` variável contiver algo diferente de "True" ou "False", ele não pode ser convertido em `Boolean`. Se ele contiver caracteres de pontuação, a conversão em qualquer tipo numérico falhará. A menos que você saiba que o `String` variável sempre contém valores que o tipo de destino pode aceitar, você não deve tentar uma conversão.  
  
 Se você deve converter de `String` para outro tipo de dados, o procedimento mais seguro é cercar a tentativa de conversão de [Try... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Isso lhe permite lidar com uma falha de tempo de execução.  
  
### <a name="character-arrays"></a>Matrizes de caracteres  
 Um único `Char` e uma matriz de `Char` elementos ampliam para `String`. No entanto, `String` não se estendem ao `Char()`. Para converter um `String` valor para um `Char` matriz, você pode usar o <xref:System.String.ToCharArray%2A>método de <xref:System.String?displayProperty=fullName>classe.</xref:System.String?displayProperty=fullName> </xref:System.String.ToCharArray%2A>  
  
### <a name="meaningless-values"></a>Valores sem sentido  
 Em geral, `String` valores não são significativos em outros tipos de dados e a conversão é perigosa e altamente artificial. Sempre que possível, você deve restringir o uso de `String` variáveis de sequências de caracteres para que elas são criadas. Você nunca deve escrever código que se baseie em valores equivalentes em outros tipos.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Uso Eficiente de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

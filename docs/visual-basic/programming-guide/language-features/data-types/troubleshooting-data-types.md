---
title: Solucionando problemas de tipos de dados (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: 5b2cb0d5270b7e14c3462aeaf54942f939511fd7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933228"
---
# <a name="troubleshooting-data-types-visual-basic"></a>Solucionando problemas de tipos de dados (Visual Basic)
Esta página lista alguns problemas comuns que podem ocorrer quando você executa operações em tipos de dados intrínsecos.  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>As expressões de ponto flutuante não são comparadas como iguais  
 Quando você trabalha com números de ponto flutuante ([tipo de dados único](../../../../visual-basic/language-reference/data-types/single-data-type.md) e [tipo de dados duplo](../../../../visual-basic/language-reference/data-types/double-data-type.md)), lembre-se de que eles são armazenados como frações binárias. Isso significa que eles não podem manter uma representação exata de qualquer quantidade que não seja uma fração binária (do formulário k/(2 ^ n) em que k e n são inteiros). Por exemplo, 0,5 (= 1/2) e 0,3125 (= 5/16) podem ser mantidos como valores precisos, enquanto 0,2 (= 1/5) e 0,3 (= 3/10) podem ser apenas aproximações.  
  
 Devido a essa imprecisão, você não pode contar com resultados exatos ao operar em valores de ponto flutuante. Em particular, dois valores que são teoricamente iguais podem ter representações ligeiramente diferentes.  
  
| Para comparar as quantidades de ponto flutuante | 
|---| 
|1.  Calcule o valor absoluto de sua diferença usando o <xref:System.Math.Abs%2A> método <xref:System.Math> da classe no <xref:System> namespace.<br />2.  Determine uma diferença máxima aceitável, de modo que você pode considerar que as duas quantidades sejam iguais para fins práticos se a diferença não for maior.<br />3.  Compare o valor absoluto da diferença com a diferença aceitável.|  
  
 O exemplo a seguir demonstra a comparação correta e correta de `Double` dois valores.  
  
 [!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]  
  
 O exemplo anterior usa o <xref:System.Double.ToString%2A> método <xref:System.Double> da estrutura para que ele possa especificar uma precisão melhor do que `CStr` a palavra-chave usa. O padrão é 15 dígitos, mas o formato "G17" o estende para 17 dígitos.  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>O operador Mod não retorna um resultado preciso  
 Devido à imprecisão do armazenamento de ponto flutuante, o [operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md) pode retornar um resultado inesperado quando pelo menos um dos operandos for de ponto flutuante.  
  
 O [tipo de dados decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) não usa representação de ponto flutuante. Muitos números que são inexatos `Single` em `Double` e são exatos `Decimal` (por exemplo, 0,2 e 0,3). Embora a aritmética seja mais lenta `Decimal` no que no ponto flutuante, pode valer a pena diminuir o desempenho para obter uma precisão melhor.  
  
|Para localizar o restante do inteiro de quantidades de ponto flutuante|  
|---|  
|1.  Declare variáveis como `Decimal`.<br />2.  Use o caractere `D` de tipo literal para forçar literais `Decimal`, caso seus valores sejam muito grandes para o tipo `Long` de dados.|  
  
 O exemplo a seguir demonstra a possível imprecisão de operandos de ponto flutuante.  
  
 [!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]  
  
 O exemplo anterior usa o <xref:System.Double.ToString%2A> método <xref:System.Double> da estrutura para que ele possa especificar uma precisão melhor do que `CStr` a palavra-chave usa. O padrão é 15 dígitos, mas o formato "G17" o estende para 17 dígitos.  
  
 Como `zeroPointTwo` é`Double`, seu valor de 0,2 é uma fração binária infinitamente repetida com um valor armazenado de 0.20000000000000001. A divisão 2,0 por essa quantidade produz 9.9999999999999995 com um restante de 0.19999999999999991.  
  
 Na expressão para `decimalRemainder`, o caractere `D` de tipo literal `Decimal`força ambos os operandos e 0,2 tem uma representação precisa. Portanto, `Mod` o operador produz o restante esperado de 0,0.  
  
 Observe que não é suficiente declarar `decimalRemainder` como. `Decimal` Você também deve forçar os literais para `Decimal`, ou eles usam `Double` por padrão e `decimalRemainder` recebem o mesmo valor impreciso como `doubleRemainder`.  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>O tipo booliano não converte em tipo numérico com precisão  
 Os valores de [tipo de dados booliano](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) não são armazenados como números e os valores armazenados não devem ser equivalentes aos números. Para compatibilidade com versões anteriores, Visual Basic fornece palavras-chave de conversão[(função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) `CBool`, `CInt`, etc.) para converter entre `Boolean` tipos numéricos e. No entanto, outras linguagens às vezes executam essas conversões de forma diferente, assim como os métodos de .NET Framework.  
  
 Você nunca deve escrever código que dependa de valores numéricos equivalentes `False`para `True` e. Sempre que possível, você deve restringir o `Boolean` uso de variáveis para os valores lógicos para os quais elas foram projetadas. Se você precisar misturar `Boolean` e valores numéricos, certifique-se de entender o método de conversão que você selecionar.  
  
### <a name="conversion-in-visual-basic"></a>Conversão em Visual Basic  
 Quando você usa as `CType` palavras `CBool` -chave de conversão ou para converter tipos de dados `Boolean`numéricos em `False` , 0 se torna e `True`todos os outros valores se tornam. Quando você converte `Boolean` valores em tipos numéricos usando as palavras-chave de conversão `False` , torna- `True` se 0 e torna-se-1.  
  
### <a name="conversion-in-the-framework"></a>Conversão na estrutura  
 O <xref:System.Convert.ToInt32%2A> método <xref:System> `True` da classe no namespace é convertido em + 1. <xref:System.Convert>  
  
 Se você precisar converter um `Boolean` valor em um tipo de dados numérico, tenha cuidado com o método de conversão usado.  
  
## <a name="character-literal-generates-compiler-error"></a>O literal de caractere gera erro de compilador  
 Na ausência de qualquer caractere de tipo, Visual Basic pressupõe tipos de dados padrão para literais. O tipo padrão para um literal de caractere — entre aspas (`" "`) — é. `String`  
  
 O `String` tipo de dados não amplia para o [tipo de dados char](../../../../visual-basic/language-reference/data-types/char-data-type.md). Isso significa que, se você quiser atribuir um literal a uma `Char` variável, deverá fazer uma conversão de restrição ou forçar o literal para o `Char` tipo.  

|Para criar um literal char para atribuir a uma variável ou constante|
|---|  
|1.  Declare a variável ou constante como `Char`.<br />2.  Coloque o valor do caractere entre aspas (`" "`).<br />3.  Siga as aspas duplas de fechamento com o caractere `C` de tipo literal para forçar o `Char`literal. Isso será necessário se a opção de verificação de tipo ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) for `On`e for desejável em qualquer caso.|  
  
 O exemplo a seguir demonstra as atribuições malsucedidas e bem sucedidas de `Char` um literal para uma variável.  
  
 [!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]  
  
 Sempre há um risco no uso de conversões redutoras, pois elas podem falhar em tempo de execução. Por exemplo, uma conversão de `String` para `Char` pode falhar se o `String` valor contiver mais de um caractere. Portanto, é melhor programar para usar o `C` caractere de tipo.  
  
## <a name="string-conversion-fails-at-run-time"></a>A conversão da cadeia de caracteres falha em tempo de execução  
 O [tipo de dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md) participa de poucas conversões ampliadas. `String`amplia apenas para si mesmo e `Object`, e apenas `Char` e `Char()` (uma `Char` matriz) amplia para `String`. Isso ocorre porque `String` as variáveis e constantes podem conter valores que outros tipos de dados não podem conter.  
  
 Quando o tipo verificando switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) `On`é, o compilador não permite todas as conversões de estreitamento implícitas. Isso inclui os que `String`envolvem. Seu código ainda pode usar palavras-chave de conversão como `CStr` , e a [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md), que direcionam a .NET Framework para tentar a conversão.  
  
> [!NOTE]
> O erro de conversão de restrição é suprimido para conversões dos elementos em uma `For Each…Next` coleção para a variável de controle de loop. Para obter mais informações e exemplos, consulte a seção "conversões redutoras" em [para cada... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="narrowing-conversion-protection"></a>Restringir a proteção de conversão  
 A desvantagem de conversões redutoras é que elas podem falhar em tempo de execução. Por exemplo, se uma `String` variável contiver algo diferente de "true" ou "false", ela não poderá ser `Boolean`convertida em. Se ele contiver caracteres de pontuação, a conversão para qualquer tipo numérico falhará. A menos que você saiba `String` que a variável sempre mantém os valores que o tipo de destino pode aceitar, você não deve tentar uma conversão.  
  
 Se você precisar converter de `String` para outro tipo de dados, o procedimento mais seguro é colocar a conversão tentada no [bloco try... Capturar... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Isso permite que você lide com uma falha de tempo de execução.  
  
### <a name="character-arrays"></a>Matrizes de caracteres  
 Um único `Char` e uma matriz de `Char` elementos são ampliados `String`para. No entanto, `String` o não `Char()`amplia para. Para converter um `String` valor em uma `Char` matriz, você pode <xref:System.String?displayProperty=nameWithType> usar o <xref:System.String.ToCharArray%2A> método da classe.  
  
### <a name="meaningless-values"></a>Valores sem significado  
 Em geral, `String` os valores não são significativos em outros tipos de dados, e a conversão é altamente artificial e perigosa. Sempre que possível, você deve restringir o `String` uso de variáveis para as sequências de caracteres para as quais elas foram projetadas. Você nunca deve escrever código que dependa de valores equivalentes em outros tipos.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Uso Eficiente de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

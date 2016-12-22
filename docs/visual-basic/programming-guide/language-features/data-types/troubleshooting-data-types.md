---
title: "Solucionando problemas de tipos de dados (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipo de dados Booliano, convertendo"
  - "tipo de dados Char, convertendo"
  - "tipos de dados [Visual Basic], solucionando problemas"
  - "tipo de dados Decimal, conversões"
  - "números de ponto flutuante"
  - "números de ponto flutuante, comparação"
  - "números de ponto flutuante, imprecisão"
  - "números de ponto flutuante, precisão"
  - "caracteres de tipo literal"
  - "tipos literais"
  - "literais, tipos padrão"
  - "Operador Mod [Visual Basic], em operações de ponto flutuante"
  - "tipo de dados String, convertendo"
  - "solucionando problemas de tipos de dados"
  - "solucionando problemas do Visual Basic, tipos de dados"
  - "caracteres de tipo, literal"
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: 29
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Solucionando problemas de tipos de dados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Essa página lista alguns problemas comuns que podem ocorrer quando você realiza operações com tipos de dado intrínsecos.  
  
## Não Comparar Expressões em Ponto Flutuante \(Floating\-Point\) como Igual  
 Quando você trabalha com números de ponto flutuante \([Tipo de dados único](../../../../visual-basic/language-reference/data-types/single-data-type.md) e [Tipo de dados double](../../../../visual-basic/language-reference/data-types/double-data-type.md)\), lembre\-se que eles são armazenados como frações binárias.  Isso significa que eles não podem manter uma representação exata de qualquer quantidade que não seja uma fração binária \(do formulário k \/ \(2 ^ n\) em que k e n são números inteiros\).  Por exemplo, 0,5 \(\= 1\/2\) e 0.3125 \(\= 5\/16\) podem ser mantidos como valores precisos, enquanto 0.2 \(\= 1\/5\) e 0,3 \(\= 3\/10\) podem ser apenas aproximações.  
  
 Devido a essa imprecisão, você não pode depender de resultados exatos quando opera com valores de ponto flutuante.  Em particular, dois valores que são, teoricamente, iguais podem ter representações ligeiramente diferentes.  
  
||  
|-|  
|Para comparar as quantidades de ponto flutuante|  
|1.  Calcule a valor absoluto de seu diferença usando o método <xref:System.Math.Abs%2A> da classe <xref:System.Math> no namespace <xref:System>.<br />2.  Determine uma diferença máxima aceitável, de forma que você pode considerar as duas quantidades como iguais para fins práticos se a diferença não for maior.<br />3.  Compare o valor absoluto da diferença com a diferença aceitável.|  
  
 O exemplo a seguir demonstra  comparações correta e incorreta entre dois valores `Double`.  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 O exemplo anterior usa o método <xref:System.Double.ToString%2A> da  estrutura <xref:System.Double> para que ele possa especificar uma precisão melhor do que aquela que a palavra\-chave `CStr` usa.  O padrão é 15 dígitos, mas o formato "G17" estende a até 17 dígitos.  
  
## Operador Mod Não Retorna Resultados Precisos  
 Devido à imprecisão de armazenamento de ponto flutuante, o [Operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md) pode retornar um resultado inesperado quando pelo menos um dos operandos for ponto flutuante.  
  
 [Tipo de dados decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) não usa representação de ponto flutuante.  Muitos números que são inexatos em `Single` e `Double` são exatos em `Decimal` \(por exemplo 0.2 e 0,3\).  Embora a aritmética seja mais lenta em `Decimal` do que em ponto flutuante, talvez valha a pena a redução de desempenho para obter melhor precisão.  
  
||  
|-|  
|Para localizar o resto inteiro de quantidades de ponto flutuante|  
|1.  Declare as variáveis como `Decimal`.<br />2.  Use o caractere de tipo literal `D` para forçar literais a `Decimal`, caso os valores sejam muito grandes para o tipo de dado `Long`.|  
  
 O exemplo a seguir demonstra a imprecisão potencial de operandos em ponto flutuante.  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 O exemplo anterior usa o método <xref:System.Double.ToString%2A> da  estrutura <xref:System.Double> para que ele possa especificar uma precisão melhor do que aquela que a palavra\-chave `CStr` usa.  O padrão é 15 dígitos, mas o formato "G17" estende a até 17 dígitos.  
  
 Como `zeroPointTwo` é `Double`,seu valor 0,2 é uma fração binária de repetição infinita com um valor armazenado de 0.20000000000000001.  A divisão 2.0 por essa quantidade produz 9.9999999999999995 com resto 0.19999999999999991.  
  
 Em uma expressão para `decimalRemainder`, o caracter de tipo literal `D` força ambos os operandos para `Decimal`, e 0.2 tem uma representação exata.  Portanto, o operador `Mod` produz o resto 0.0 esperado.  
  
 Observe que é não suficiente declarar `decimalRemainder` como `Decimal`.  Você também deve forçar os literais para que sejam `Decimal`, ou eles usam `Double` por padrão e `decimalRemainder` recebe o mesmo valor `doubleRemainder` impreciso.  
  
## Tipo Booleano Não Cconverte para Tipo Numérico com Precisão  
 Valores [Tipo de dados booliano](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) não são armazenados como números, e não se espera que os valores armazenados sejam equivalentes a números.  Para compatibilidade com versões anteriores, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece conversão de palavras\-chave \([Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md),`CBool`,`CInt`, e assim por diante\) para converter entre `Boolean` e tipos numéricos.  No entanto, outras linguagens, às vezes, executam essas conversões de maneira diferente, como fazem os métodos [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
 Você nunca deve escrever um código que dependa de valores numéricos equivalentes para `True` e `False`.  Sempre que possível, você deve restringir uso de variáveis `Boolean` para os valores lógicos para o quais elas são criadas.  Se você deve combinar `Boolean` e valores numéricos, certifique\-se que você entende o método de conversão que você selecionar.  
  
### Conversão em Visual Basic  
 Quando você usar as palavras\-chave de conversão `CType` ou `CBool` para converter tipos de dados numérico para `Boolean`,0 se torna `False` e todos os outros valores tornam\-se `True`.  Quando você converte valores `Boolean` para tipos numéricos usando as palavras\-chave de conversão, `False` se torna 0 e `True` torna\-se \-1.  
  
### Conversão no Framework  
 O método <xref:System.Convert.ToInt32%2A> da classe <xref:System.Convert> no namespace <xref:System> converte  `True` para \+ 1.  
  
 Se você deve converter um valor `Boolean` para um tipo de dados numérico, tome cuidado sobre que método de conversão usar.  
  
## Caractere Literal Gera Erro do Compilador  
 Na ausência de qualquer caracteres de tipo, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] assume tipo de dados padrão para literais.  O tipo padrão de um caractere literal — entre aspas \(`" "`\) — é `String`.  
  
 O tipo de dados `String` não amplia para o [Tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md).  Isso significa que se você desejar atribuir um literal para uma variável `Char`, você deve fazer uma conversão de restrição ou forçar o literal para o tipo `Char`.  
  
||  
|-|  
|Para criar um literal Char para atribuir a uma variável ou constante|  
|1.  Declare a variável ou constante como `Char`.<br />2.  Coloque o valor de caracteres entre aspas \(`" "`\).<br />3.  Siga as aspas duplas de fechamento do caracter de tipo literal  `C` para forçar o literal para `Char`.  Isso é necessário se a verificação de tipo muda \([Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) é `On`,e em qualquer caso, isto é desejável.|  
  
 O exemplo a seguir demonstra atribuições bem e mal sucedidas de um literal para uma variável `Char`.  
  
 [!CODE [VbVbalrStatements#49](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrStatements#49)]  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/troubleshooting-data-types_4.vb)]  
  
 Há sempre um risco ao usar conversões redutoras, pois elas podem falhar em tempo de execução.  Por exemplo, uma conversão de `String` em `Char` pode falhar se o valor `String` contiver mais de um caractere.  Portanto, ele é uma técnica de programação melhor usar o caracter de tipo `C`.  
  
## Falha na conversão de cadeia de caracteres em tempo de execução  
 O [Tipo de dados da cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md) participa muito poucas conversões de expansão.  `String`amplia\-se somente a mesmo e `Object`e apenas `Char` e `Char()` \(um `Char` array\) aumentarão para `String`.  Isso ocorre porque variáveis e constantes `String` podem conter valores que outros tipos de dados não podem conter.  
  
 Quando o verificação de tipo muda \([Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) é `On`, o compilador proíbe todos as conversões redutoras implícitas.  Isso inclui aquelas envolvendo `String`.  Seu código pode ainda usar conversão de palavras\-chave, como `CStr` e [Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md), que direciona o [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] a tentar a conversão.  
  
> [!NOTE]
>  O erro de conversão narrowing é suprimido para conversões de elementos em um `For Each…Next` coleção para a variável de controle de loop.  Para obter mais informações e exemplos, consulte a seção "Estreitando conversões" [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### Restringir a Proteção de Conversão  
 A desvantagem de conversões redutoras é que eles podem falhar em tempo de execução.  Por exemplo, se uma variável `String` contiver algo diferente de "True" ou "False", ela não pode ser convertido em `Boolean`.  Se ele contiver caracteres de pontuação, a conversão em qualquer tipo numérico falhará.  A menos que você saiba que a variável `String` sempre contém valores que o tipo de destino pode aceitar, você não deve tentar uma conversão.  
  
 Se você deve converter de `String` para outro tipo de dados, o procedimento mais seguro é cercar a tentativa de conversão com [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  Isso permite que você lide com uma falha em tempo de execução.  
  
### Matrizes de Caracteres  
 Um único `Char` e uma matriz de elementos `Char` ampliam para `String`.  No entanto, `String` não amplia para `Char()`.  Para converter um valor `String` em uma matriz `Char`, você pode usar o método <xref:System.String.ToCharArray%2A> da classe <xref:System.String?displayProperty=fullName>.  
  
### Valores Sem Significado  
 Em geral, os valores `String` não são significativos em outros tipos de dados, e a conversão é perigosa e altamente artificial.  Sempre que possível, você deve restringir o uso de variáveis `String` a seqüencia de caracteres para as quais elas são criadas.  Você nunca deve escrever código que se baseie em valores equivalentes em outros tipos.  
  
## Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão do tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Uso eficiente de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
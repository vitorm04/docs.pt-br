---
title: "Operador Like (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Like"
  - "vb.Like"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "símbolo ?, caractere curinga"
  - "operadores de comparação"
  - "dados [Visual Basic], classificando"
  - "dados [Visual Basic], comparações de cadeias de caracteres"
  - "Operador Like [Visual Basic]"
  - "operadores [Visual Basic], correspondência padrão"
  - "correspondência padrão"
  - "semelhante a"
  - "comparação de cadeias de caracteres [Visual Basic], Operador Like"
  - "comparação de cadeias de caracteres [Visual Basic], operadores Like"
  - "comparação de cadeias de caracteres [Visual Basic], classificando dados"
  - "cadeias de caracteres {Visual Basic], comparando"
  - "cadeias de caracteres {Visual Basic], correspondência"
  - "símbolos, curinga"
  - "texto [Visual Basic], comparando"
  - "curingas, Operador Like"
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador Like (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Compara uma sequência de caracteres com um padrão.  
  
## Sintaxe  
  
```  
  
result = string Like pattern  
```  
  
## Partes  
 `result`  
 Obrigatório.  Qualquer variável `Boolean`.  O resultado é um valor `Boolean` indicando se `string` satisfaz ou não `pattern`.  
  
 `string`  
 Obrigatório.  Qualquer expressão `String`.  
  
 `pattern`  
 Obrigatório.  Qualquer expressão `String` de acordo com as convenções de coincidência de padrão descritas em "Comentários".  
  
## Comentários  
 Se o valor `string` satisfizer o padrão contido em `pattern`, `result` `True`.  Se a sequência de caracteres não satisfizer o padrão, `result` será  `False`.  Se ambos `string` e `pattern` forem sequências de caracteres vazias, o resultado será `True`.  
  
## Método de Comparação  
 O comportamento do operador `Like` depende de [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).  O método de comparação de sequência de caracteres padrão para cada arquivo de origem é `Option Compare Binary`.  
  
## Opções Padrão  
 Correspondência de padrões interna fornece uma ferramenta versátil para comparações de sequência de caracteres.  Os recursos de coincidência de padrão permitem que você coincida cada caractere em `string` com um caractere específico, um caractere curinga, uma lista de caracteres ou um intervalo de caracteres.  A tabela a seguir mostra os caracteres permitidos em `pattern` e o que eles correspondem.  
  
|Caracteres em `pattern`|Correspondências em `string`|  
|-----------------------------|----------------------------------|  
|`?`|Qualquer caractere único|  
|`*`|Zero ou mais caracteres|  
|`#`|Qualquer dígito único \(0–9\)|  
|`[` `charlist` `]`|Qualquer caractere único no `charlist`|  
|`[!` `charlist` `]`|Qualquer caractere único que não esteja em `charlist`|  
  
## Listas de Caracteres  
 Um grupo de um ou mais caracteres \(`charlist`\) entre colchetes \(`[ ]`\) pode ser usado para coincidir qualquer caractere único em `string` e pode incluir quase todos os código de caractere, inclusive dígitos.  
  
 Um ponto de exclamação \(`!`\) no início de `charlist` significa que uma coincidência é feita se qualquer caractere, exceto os caracteres em `charlist` for encontrado em `string`.  Quando usado fora de colchetes, o ponto de exclamação corresponde a si mesmo.  
  
## Caracteres Especiais  
 Para coincidir com os caracteres especiais à esquerda do colchete \(`[`\), ponto de interrogação \(`?`\), sinal numérico \(`#`\), e asterisco \(`*`\), coloque\-os entre colchetes.  O colchete direito \(`]`\) não pode ser usado dentro de um grupo para corresponder em si, mas ele pode ser usado fora de um grupo como um caractere individual.  
  
 A sequência de caracteres `[]` é considerada uma sequencia de caracteres de comprimento zero \(`""`\).  No entanto, ele não pode ser parte de uma lista de caracteres entre colchetes.  Se você quiser verificar se uma posição na `string` contém um de um grupo de caracteres ou nenhum caractere, você pode usar `Like` duas vezes.  Para um exemplo, consulte [Como corresponder uma cadeia de caracteres a um padrão](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## Intervalos de Caracteres  
 Usando um hífen \(`–`\) para separar os limites inferior e superior do intervalo, `charlist` pode especificar um intervalo de caracteres.  Por exemplo, `[A–Z]` resulta em uma coincidência, se o caractere correspondente posicionar em `string` contém qualquer caractere dentro do intervalo de `A`–`Z`, e `[!H–L]` resulta em uma coincidência se a posição do caractere correspondente contiver qualquer caractere fora do intervalo `H`–`L`.  
  
 Quando você especifica um intervalo de caracteres, eles devem aparecer em ordem de classificação crescente, ou seja, do menor para o maior.  Assim, `[A–Z]` é um padrão válido, mas `[Z–A]` não é.  
  
### Vários Intervalos de Caracteres  
 Para especificar vários intervalos para a mesma posição de caractere, coloque\-os entre os mesmos colchetes sem delimitadores.  Por exemplo, `[A–CX–Z]` resulta em uma coincidência, se o caractere correspondente posicionar em `string` contém qualquer caractere dentro do intervalo ambos `A`–`C` ou o intervalo de `X`–`Z`.  
  
### Uso do Hífen  
 Um hífen \(`–`\) podem aparecer no início \(após um ponto de exclamação, se houver\) ou no final do `charlist` para corresponder a próprio.  Em qualquer outro local, o hífen identifica um intervalo de caracteres delimitado por caracteres em ambos os lados do hífen.  
  
## Sequência de Agrupamento  
 O significado de um intervalo especificado depende do caractere de ordenação em tempo de execução, conforme determinado pela `Option` `Compare` e da configuração local do sistema na qual o código está sendo executado.  With `Option``Compare``Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.  With `Option``Compare``Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.  O intervalo não coincide com `Ê` ou `ê` porque caracteres acentuados agupam após caracteres não acentuados na ordem de classificação.  
  
## Caracteres Dígrafo  
 Em alguns idiomas, há caracteres alfabéticos que representam dois caracteres distintos.  Por exemplo, vários idiomas usam o caractere `æ` para representar os caracteres `a` e `e` quando aparecem juntos.  O operador `Like` reconhece que o caractere dígrafo único e os dois caracteres individuais são equivalentes.  
  
 Quando um idioma que usa um caractere dígrafo for especificado nas configurações de localidade do sistema, uma ocorrência do caractere dígrafo única em `pattern` ou `string` coincide com a sequência de dois caracteres equivalente na outra sequência de caracteres.  Da mesma forma, um caractere dígrafo em `pattern` entre colchetes \(por si só, em uma lista, ou em um intervalo\) coincide com a sequência de dois caracteres `string`.  
  
## Sobrecarga  
 O operador `Like` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo daquela classe ou estrutura.  Se seu código usa esse operador em tal classe ou estrutura, esteja certo que entende seu comportamento redefinido.  Para obter mais informações, consulte [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Exemplo  
 Este exemplo usa o operador `Like` para comparar sequências de caracteres para vários padrões.  Os resultados entram em uma variável `Boolean` que indica se cada sequência satisfaz o padrão.  
  
 [!CODE [VbVbalrOperators#30](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#30)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [Operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Como corresponder uma cadeia de caracteres a um padrão](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
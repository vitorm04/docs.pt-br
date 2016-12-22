---
title: "Solucionando problemas de procedimentos (Visual Basic) | Microsoft Docs"
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
  - "procedimentos, sobre procedimentos"
  - "procedimentos, solucionando problemas"
  - "solucionando problemas de procedimentos"
  - "solucionando problemas do Visual Basic, procedimentos"
  - "código do Visual Basic, procedimentos"
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Solucionando problemas de procedimentos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esta página lista somente problemas comuns que podem ocorrer quando se trabalha com procedimentos.  
  
## Retornando um tipo arrayde uma função de procedimento  
 Se um procedimento `Function` retornar um tipo de dados array, você não pode usar o nome `Function` para armazenar os valores nos elementos do array.  Se você tentar fazer isso, o compilador interpretará como uma chamada para `Function`.  O exemplo a seguir gera Erros de compilador.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 A declaração `allOnes(i) = 1` gera um erro do compilador porque ela aparenta chamar `allOnes` com um argumento do tipo de dados incorreto \(um singleton `Integer` em vez de um array `Integer`\).  A declaração `Return allOnes()` gera um erro do compilador porque ela aparenta chamar `allOnes` com nenhum argumento.  
  
 **Abordagem correta:** Para modificar os elementos de um array que está para ser retornado, defina um array interno como uma variável local.  O exemplo a seguir compila sem erro.  
  
 [!code-vb[VbVbcnProcedures#66](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## Argumento não sendo modificado pela chamada de procedimento  
 Se você pretende permitir que um procedimento altere um elemento de programação subjacente a um argumento no código de chamada, você deve passá\-lo por referência.  Mas um procedimento pode acessar os elementos de um argumento de tipo de referência mesmo se você passá\-lo por valor.  
  
-   **Variável Subjacente** .  Para permitir que o procedimento substitua o valor do elemento variável subjacente, o procedimento deve declarar o parâmetro [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  Aém disso, o código de chamada não deve colocarc o argumento entre parênteses, porque isso poderia substituir o mecanismo de passagem `ByRef`.  
  
-   **Elementos de Tipo de Referência** Se você declarar um parâmetro [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), o procedimento não pode modificar o elemento variável subjacente.  No entanto, se o argumento for um tipo de referência, o procedimento pode modificar os membros do objeto para o qual ele aponta, mesmo que não seja possível substituir o valor da variável.  Por exemplo, se o argumento for uma variável array, o procedimento não pode atribuir um novo array a ela, mas ele pode alterar um ou mais dos seus elementos.  Os elementos alterados são refletidos na variável array subjacente no código de chamada.  
  
 O exemplo a seguir defeine dois procedimentos que tenham uma variável de matriz e operam em seus elementos.  O procedimento `increase` simplesmente adiciona um para cada elemento.  O procedimento `replace` atribui o parâmetro `a()` uma nova matriz e, em seguida, adiciona um para cada elemento.  No entanto, a reatribuição não afeta a variável array subjacente no código de chamada porque `a()` é declarado como `ByVal`.  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 O exemplo a seguir faz chamadas para `increase` e `replace`.  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 Exibe o primeiro `MsgBox` chamada " após increase\(n\): 11 21, 31, 41".  Como `n` é um tipo de referência, `increase` pode alterar seus membros, mesmo que ele seja passado `ByVal`.  
  
 A segunda `MsgBox` chamada exibe " Após Replace\(n\): 11, 21, 31, 41.  Como `n` é passado `ByVal`,`replace` não pode modificar a variável `n` atribuindo um novo array a ela.  Quando `replace` cria a nova instância de array `k` e a atribui para a variável local `a`,ele perde a referência à `n` passada pelo código de chamada.  Quando ele aumenta os membros do `a`, somente o array ocal `k` é afetado.  
  
 **Abordagem correta:**  Para modificar um elemento variável subjacente, passá\-lo por referência.  O exemplo a seguir mostra a alteração na declaração de `replace` que permite que ele substitua um array com outro no código de chamada.  
  
 [!code-vb[VbVbcnProcedures#64](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## Não é possível definir uma sobrecarga  
 Se você quiser definir uma versão sobrecarregada de um procedimento, você deve usar o mesmo nome mas uma assinatura diferente.  Se o compilador não pode diferenciar sua declaração de uma sobrecarga com a mesma assinatura, ele gera um erro.  
  
 A *assinatura* de um procedimento é determinada pelo nome do procedimento e a lista de parâmetros.  Cada sobrecarga deve ter o mesmo nome de todas as outras sobrecargas, mas deve diferir de todoa elas em pelo menos um dos outros componentes da assinatura.  Para obter mais informações, consulte [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
 Os itens a seguir, mesmo que pertençam à lista de parâmetros, não são componentes da assinatura de um procedimento:  
  
-   Palavras\-chave modificadores de procedimento, como `Public`, `Shared`, e `Static`  
  
-   Nomes de parâmetro  
  
-   Palavras\-chave modificadoras de parâmetros \(como `ByRef` e `Optional`\)  
  
-   O tipo de dado do valor de retorno \(exceto para um operador de conversão\)  
  
 Você não pode sobrecarregar um procedimento, variando apenas um ou mais dos itens anteriores.  
  
 **Abordagem correta:**  Para conseguir definir uma sobrecarga procedimento, você deve variar a assinatura.  Como você deve usar o mesmo nome, você deve variar o número, ordem ou tipos de dados dos parâmetros.  Em um procedimento genérico, você pode variar o número de parâmetros de tipo.  Em um operador de conversão \([Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)\), você pode variar o tipo de retorno.  
  
### Resolução de sobrecarga com argumentos Opcional e ParamArray  
 Se você estiver sobrecarregando um procedimento com um ou mais parâmetros [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md) ou um parâmetro [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , você deve evitar duplicar qualquer uma das  *sobrecargas implícitas*.  Para obter mais informações, consulte: [Considerações sobre procedimentos de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md).  
  
## Chamando uma versão incorreta de um procedimento sobrecarregado  
 Se um procedimento tem várias versões sobrecarregadas, você deve estar familiarizado com todos as suas listas de parâmetros e entender como [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] resolve chamadas entre as sobrecargas.  Caso contrário, você poderia chamar uma sobrecarga diferente daquela pretendida.  
  
 Quando você determinar que sobrecarga  você deseja chamar, tenha cuidado para observar as seguintes regras:  
  
-   Forneça o número correto de argumentos e na ordem correta.  
  
-   Idealmente, seus argumentos devem ter os mesmos tipos de dados que os parâmetros correspondentes.  Em qualquer caso, o tipo de dados de cada argumento deve ampliar ao de seu parâmetro correspondente.  Isso é verdadeiro mesmo com o [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) definido como `Off`.  Se uma sobrecarga exigir qualquer conversão de restrição na sua lista de argumentos, a sobrecarga não está qualificada a ser chamada.  
  
-   Se você fornecer argumentos que exigem conversões de ampliação, faça com que seus tipos sejam o mais próximo possível dos tipos de dados dos parâmetros correspondentes.  Se duas ou mais sobrecargas aceitarem os tipos de dados dos seus argumentos, o compilador resolve a chamada para a sobrecarga que precisa do mínimo de ampliação.  
  
 Você pode reduzir a chance de diferenças de tipo de dado usando a palavra\-chave de conversão [Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) ao preparar seus argumentos.  
  
### Falha de Resolução de Sobrecarga  
 Quando você chamar um procedimento sobrecarregado, o compilador tenta eliminar todas menos uma das sobrecargas.  Se ele for bem\-sucedido, ele resolve a chamada para essa sobrecarga.  Se ele elimina todas as sobrecargas, ou se não é possível reduzir as sobrecargas qualificadas para uma única candidata, ele gera um erro.  
  
 O exemplo a seguir ilustra o processo de resolução de sobrecarga.  
  
 [!code-vb[VbVbcnProcedures#62](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 Na primeira chamada, o compilador elimina o primeiro sobrecarregamento porque o tipo do primeiro argumento \(`Short`\) estreita ao tipo do parâmetro correspondente \(`Byte`\).  Então elimina o terceiro sobrecarregamento porque cada tipo de argumento no segundo sbrecarregamento \(`Short` e `Single`\) alarga ao tipo correspondente no terceiro sobrecarregamento \(`Integer` e `Single`\).  O segundo sobrecarregamento requer menos alargamento, então o compilador usa\-o para a chamada.  
  
 Na segunda chamada, o compilador não pode eliminar qualquer dos sobrecarregamentos na base do estreitamento.  Elimina o terceiro sobrecarregamento pela mesma razão que na primeira chamada, porque pode chamar o segundo sobrecarregamento com menos alargamento de tipos de argumento.  Entretanto, o compilador não pode resolver entre o primeiro e segundo sobrecarregamentos.  Cada um possui tipo definido de parâmetro que alarga para o tipo correspondente no outro \(`Byte` a `Short`, mas `Single` a `Double`\).  O compilador, por isso, gera um erro de resolução de sobrecarregamento.  
  
 **Abordagem correta:**  Para chamar um procedimento sobrecarregado sem ambiguidade, use [Função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para haver correspondência entre os tipos de dados dos argumento e os tipos de dados dos parâmetros.  O exemplo a seguir mostra uma chamada para `z` que força a resolução para a segunda sobrecarga.  
  
 [!code-vb[VbVbcnProcedures#65](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### Resolução de sobrecarga com argumentos Opcional e ParamArray  
 Se duas sobrecargas de um procedimento tenham assinaturas idênticas exceto pelo fato de que o último parâmetro é declarado [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md) em um e [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) no outro, o compilador resolve a chamada para o procedimento de acordo com a correspondência mais próxima.  Para obter mais informações, consulte [Resolução de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md).  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Considerações sobre procedimentos de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Resolução de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
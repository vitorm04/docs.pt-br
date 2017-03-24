---
title: Solucionando problemas de procedimentos (Visual Basic) | Documentos do Microsoft
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
- troubleshooting Visual Basic, procedures
- procedures, troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures, about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: a5445d6da982e4eea5b1047505e4bee3380ed472
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-procedures-visual-basic"></a>Solucionando problemas de procedimentos (Visual Basic)
Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com procedimentos.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Retornando um tipo de matriz de um procedimento Function  
 Se um `Function` procedimento retorna um tipo de dados de matriz, você não pode usar o `Function` nome para armazenar os valores nos elementos da matriz. Se você tentar fazer isso, o compilador interpretará como uma chamada para o `Function`. O exemplo a seguir gera erros de compilador.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 A instrução `allOnes(i) = 1` gera um erro do compilador porque ela aparenta chamar `allOnes` com um argumento do tipo de dados incorreto (um singleton `Integer` em vez de um `Integer` matriz). A instrução `Return allOnes()` gera um erro do compilador porque ela aparenta chamar `allOnes` com nenhum argumento.  
  
 **Abordagem correta:** para ser capaz de modificar os elementos de uma matriz que deve ser retornado, defina um array interno como uma variável local. O exemplo a seguir compila sem erro.  
  
 [!code-vb[VbVbcnProcedures&#66;](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>Argumento não sendo modificado pela chamada de procedimento  
 Se você pretende permitir que um procedimento alterar um elemento de programação subjacente um argumento no código de chamada, você deve passar por referência. Mas um procedimento pode acessar os elementos de um argumento de tipo de referência, mesmo se você passá-lo por valor.  
  
-   **Subjacente a variável**. Para permitir que o procedimento substituir o valor do elemento variável subjacente, o procedimento deve declarar o parâmetro [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Além disso, o código de chamada deve não coloque o argumento entre parênteses, porque isso poderia substituir o `ByRef` mecanismo de passagem.  
  
-   **Fazer referência a elementos do tipo**. Se você declarar um parâmetro [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), o procedimento não pode modificar o elemento variável subjacente. No entanto, se o argumento for um tipo de referência, o procedimento pode modificar os membros do objeto para o qual ele aponta, mesmo que não seja possível substituir o valor da variável. Por exemplo, se o argumento for uma variável de matriz, o procedimento não pode atribuir uma nova matriz a ela, mas ele pode alterar um ou mais dos seus elementos. Os elementos alterados são refletidos na variável array subjacente no código de chamada.  
  
 O exemplo a seguir define dois procedimentos que tenham uma variável de matriz por valor e operam em seus elementos. Procedimento `increase` simplesmente adiciona um para cada elemento. Procedimento `replace` atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento. No entanto, a reatribuição não afeta a variável array subjacente no código de chamada porque `a()` é declarado `ByVal`.  
  
 [!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures&38;](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 O exemplo a seguir faz chamadas para `increase` e `replace`.  
  
 [!code-vb[VbVbcnProcedures&#37;](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 A primeira `MsgBox` chamada exibe "após increase (n): 11, 21, 31, 41". Porque `n` é um tipo de referência, `increase` pode alterar seus membros, mesmo que ele seja passado `ByVal`.  
  
 O segundo `MsgBox` chamada exibe "Após Replace (n): 11, 21, 31, 41". Porque `n` é passado `ByVal`, `replace` não é possível modificar a variável `n` atribuindo uma nova matriz a ela. Quando `replace` cria a nova instância de matriz `k` e o atribui à variável local `a`, ele perde a referência à `n` passado pelo código de chamada. Quando ele aumenta os membros de `a`, somente o array local `k` é afetado.  
  
 **Abordagem correta:** para ser capaz de modificar um elemento variável subjacente, passá-lo por referência. O exemplo a seguir mostra a alteração na declaração de `replace` que permite que ele substitua um array com outro no código de chamada.  
  
 [!code-vb[VbVbcnProcedures&#64;](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a>Não é possível definir uma sobrecarga  
 Se você quiser definir uma versão sobrecarregada de um procedimento, você deve usar o mesmo nome mas uma assinatura diferente. Se o compilador não pode diferenciar sua declaração de uma sobrecarga com a mesma assinatura, ele gera um erro.  
  
 O *assinatura* de um procedimento é determinada pelo nome do procedimento e a lista de parâmetros. Cada sobrecarga deve ter o mesmo nome de todas as outras sobrecargas, mas deve diferir de todas elas em pelo menos um dos outros componentes da assinatura. Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).  
  
 Os itens a seguir, mesmo que pertençam à lista de parâmetros, não são componentes da assinatura do procedimento:  
  
-   Palavras-chave modificadores de procedimento, como `Public`, `Shared`, e`Static`  
  
-   Nomes de parâmetro  
  
-   Palavras-chave modificador de parâmetro, como `ByRef` e`Optional`  
  
-   O tipo de dados do valor de retorno (exceto para um operador de conversão)  
  
 Você não pode sobrecarregar um procedimento, variando apenas um ou mais dos itens anteriores.  
  
 **Abordagem correta:** para poder definir uma sobrecarga procedimento, você deve variar a assinatura. Como você deve usar o mesmo nome, você deve variar o número, ordem ou tipos de dados dos parâmetros. Em um procedimento genérico, você pode variar o número de parâmetros de tipo. Em um operador de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)), você pode variar o tipo de retorno.  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Sobrecarga de resolução com opcional e argumentos ParamArray  
 Se você estiver sobrecarregando um procedimento com um ou mais [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetros ou um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro, você deve evitar duplicar qualquer uma da *sobrecargas implícitas*. Para obter informações, consulte [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>Chamando uma versão incorreta de um procedimento sobrecarregado  
 Se um procedimento tem várias versões sobrecarregadas, você deve estar familiarizado com todas as suas listas de parâmetros e entender como [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] resolve chamadas entre as sobrecargas. Caso contrário, você poderia chamar uma sobrecarga que não seja o pretendido.  
  
 Quando você determinar que sobrecarga você deseja chamar, tenha cuidado para observar as seguintes regras:  
  
-   Forneça o número correto de argumentos e na ordem correta.  
  
-   Idealmente, seus argumentos devem ter os mesmos tipos de dados que os parâmetros correspondentes. Em qualquer caso, o tipo de dados de cada argumento deve ampliar de seu parâmetro correspondente. Isso é verdadeiro mesmo com o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) definida como `Off`. Se uma sobrecarga exigir qualquer conversão de redução da sua lista de argumentos, que sobrecarregam não é elegível para ser chamado.  
  
-   Se você fornecer argumentos que exigem conversões de ampliação, verifique seus tipos de dados mais próximo possível para os tipos de dados do parâmetro correspondente. Se duas ou mais sobrecargas aceitarem seus tipos de dados de argumento, o compilador resolve a chamada para a sobrecarga que chama para a menor quantidade de ampliação.  
  
 Você pode reduzir a chance de diferenças de tipo de dados usando o [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) palavra de-de chave do conversão ao preparar seus argumentos.  
  
### <a name="overload-resolution-failure"></a>Falha na resolução de sobrecarga  
 Quando você chama um procedimento sobrecarregado, o compilador tenta eliminar todas menos uma das sobrecargas. Se for bem-sucedido, ele resolve a chamada para essa sobrecarga. Se ele elimina todas as sobrecargas, ou se não é possível reduzir as sobrecargas qualificadas para uma única candidata, ele gera um erro.  
  
 O exemplo a seguir ilustra o processo de resolução de sobrecarga.  
  
 [!code-vb[VbVbcnProcedures&#62;](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures&#63;](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 Na primeira chamada, o compilador elimina a primeira sobrecarga porque o tipo do primeiro argumento (`Short`) estreita ao tipo do parâmetro correspondente (`Byte`). Então elimina o terceiro sobrecarregamento porque cada tipo de argumento na segunda sobrecarga (`Short` e `Single`) amplia-se para o tipo correspondente no terceiro sobrecarregamento (`Integer` e `Single`). O segundo sobrecarregamento requer menos alargamento, então o compilador usa-o para a chamada.  
  
 Na segunda chamada, o compilador não pode eliminar qualquer uma das sobrecargas com base na restrição. Elimina o terceiro sobrecarregamento pela mesma razão que na primeira chamada, pois ele pode chamar o segundo sobrecarregamento com menos alargamento de tipos de argumento. No entanto, o compilador não pode resolver entre as primeira e o segunda sobrecargas. Cada um tem um tipo definido de parâmetro que amplia para o tipo correspondente no outro (`Byte` para `Short`, mas `Single` para `Double`). Portanto, o compilador gera um erro de resolução de sobrecarga.  
  
 **Abordagem correta:** para poder chamar um procedimento sobrecarregado sem ambiguidade, use [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para corresponder aos tipos de dados de argumento para os tipos de parâmetro. O exemplo a seguir mostra uma chamada para `z` que força a resolução para a segunda sobrecarga.  
  
 [!code-vb[VbVbcnProcedures&#65;](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Sobrecarga de resolução com opcional e argumentos ParamArray  
 Se duas sobrecargas de um procedimento possuem assinaturas idênticas exceto que o último parâmetro é declarado [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) em um e [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) no outro, o compilador resolve uma chamada para o procedimento de acordo com a correspondência mais próxima. Para obter mais informações, consulte [resolução de sobrecarga](./overload-resolution.md).  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Procedimentos de função](./function-procedures.md)   
 [Procedimentos de propriedade](./property-procedures.md)   
 [Procedimentos de operador](./operator-procedures.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md)   
 [Resolução de Sobrecarga](./overload-resolution.md)

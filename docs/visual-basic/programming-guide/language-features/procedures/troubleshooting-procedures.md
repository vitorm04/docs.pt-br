---
title: Solucionando problemas de procedimentos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: 492a7474a38a7e41b7e3b3f59dfa118c30256ea4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791788"
---
# <a name="troubleshooting-procedures-visual-basic"></a>Solucionando problemas de procedimentos (Visual Basic)
Esta página lista alguns problemas comuns que podem ocorrer ao trabalhar com procedimentos.  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Retornando um tipo de matriz de um procedimento Function  
 Se um `Function` procedimento retorna um tipo de dados de matriz, você não pode usar o `Function` nome para armazenar os valores nos elementos da matriz. Se você tentar fazer isso, o compilador interpreta como uma chamada para o `Function`. O exemplo a seguir gera erros de compilador.  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 A instrução `allOnes(i) = 1` gera um erro do compilador porque ele aparece para chamar `allOnes` com um argumento de tipo de dados errado (um singleton `Integer` em vez de um `Integer` matriz). A instrução `Return allOnes()` gera um erro do compilador porque ele aparece para chamar `allOnes` com nenhum argumento.  
  
 **Abordagem correta:** Para ser capaz de modificar os elementos de uma matriz que é retornada, define uma matriz interna como uma variável local. O exemplo a seguir compila sem erro.  
  
 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>Argumento não sendo modificado pela chamada de procedimento  
 Se você pretende permitir que um procedimento alterar um elemento de programação subjacente um argumento no código de chamada, você deve passar por referência. Mas um procedimento pode acessar os elementos de um argumento de tipo de referência, mesmo se você passá-lo por valor.  
  
- **Variável de base**. Para permitir que o procedimento substituir o valor do elemento variável subjacente, o procedimento deve declarar o parâmetro [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Além disso, o código de chamada deve não coloque o argumento entre parênteses, porque isso poderia substituir o `ByRef` mecanismo de passagem.  
  
- **Fazer referência a elementos do tipo**. Se você declarar um parâmetro [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), o procedimento não é possível modificar o elemento variável subjacente. No entanto, se o argumento for um tipo de referência, o procedimento pode modificar os membros do objeto para o qual ele aponta, mesmo que ele não é possível substituir o valor da variável. Por exemplo, se o argumento for uma variável de matriz, o procedimento não é possível atribuir uma nova matriz a ela, mas ele pode alterar um ou mais dos seus elementos. Os elementos alterados são refletidos na variável de matriz subjacente no código de chamada.  
  
 O exemplo a seguir define dois procedimentos que tenham uma variável de matriz por valor e operam em seus elementos. Procedimento `increase` simplesmente adiciona um para cada elemento. Procedimento `replace` atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento. No entanto, a reatribuição não afeta a variável de matriz subjacente no código de chamada porque `a()` é declarado `ByVal`.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 O exemplo a seguir faz chamadas para `increase` e `replace`.  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 A primeira `MsgBox` chamada exibe "após increase (n): 11, 21, 31, 41". Porque `n` é um tipo de referência `increase` podem alterar seus membros, mesmo que ele seja passado `ByVal`.  
  
 O segundo `MsgBox` chamada exibe "Após Replace (n): 11, 21, 31, 41". Porque `n` é passado `ByVal`, `replace` não é possível modificar a variável `n` atribuindo uma nova matriz a ela. Quando `replace` cria a nova instância de matriz `k` e o atribui à variável local `a`, ele perde a referência à `n` passado pelo código de chamada. Quando ele aumenta os membros da `a`, apenas a matriz local `k` é afetado.  
  
 **Abordagem correta:** Para ser capaz de modificar um elemento variável subjacente, passá-lo por referência. O exemplo a seguir mostra a alteração na declaração de `replace` que permite que ele substitua um array com outro no código de chamada.  
  
 [!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]  
  
## <a name="unable-to-define-an-overload"></a>Não é possível definir uma sobrecarga  
 Se você quiser definir uma versão sobrecarregada de um procedimento, você deve usar o mesmo nome mas uma assinatura diferente. Se o compilador não pode diferenciar sua declaração de uma sobrecarga com a mesma assinatura, ele gera um erro.  
  
 O *assinatura* de um procedimento é determinado pelo nome do procedimento e a lista de parâmetros. Cada sobrecarga deve ter o mesmo nome de todas as outras sobrecargas, mas deve ser diferente de todos eles em pelo menos um dos outros componentes da assinatura. Para obter mais informações, consulte [sobrecarga de procedimento](./procedure-overloading.md).  
  
 Os seguintes itens, mesmo que pertençam à lista de parâmetros, não são componentes da assinatura do procedimento:  
  
- Palavras-chave com o modificador de procedimento, como `Public`, `Shared`, e `Static`  
  
- Nomes de parâmetro  
  
- Palavras-chave com o modificador de parâmetro, como `ByRef` e `Optional`  
  
- o tipo de dados do valor de retorno (exceto para um operador de conversão)  
  
 Você não pode sobrecarregar um procedimento, variando apenas um ou mais dos itens anteriores.  
  
 **Abordagem correta:** Para poder definir uma sobrecarga de procedimento, você deve variar a assinatura. Como você deve usar o mesmo nome, você deve variar o número, ordem ou tipos de dados dos parâmetros. Em um procedimento genérico, você pode variar o número de parâmetros de tipo. Em um operador de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)), você pode variar o tipo de retorno.  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Sobrecarga de resolução com opcional e argumentos ParamArray  
 Se você estiver sobrecarregando um procedimento com um ou mais [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetros ou um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro, você deve evitar a duplicação de qualquer um dos *sobrecargas implícitas*. Para obter informações, consulte [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>Chamando uma versão incorreta de um procedimento sobrecarregado  
 Se um procedimento tem várias versões sobrecarregadas, você deve estar familiarizado com todas as suas listas de parâmetros e entender como o Visual Basic resolve chamadas entre as sobrecargas. Caso contrário, você poderia chamar uma sobrecarga que não seja o pretendido.  
  
 Quando você determinou qual sobrecarga você deseja chamar, tenha cuidado para observar as seguintes regras:  
  
- Forneça o número correto de argumentos e na ordem correta.  
  
- O ideal é que seus argumentos devem ter os mesmos tipos de dados como os parâmetros correspondentes. Em qualquer caso, o tipo de dados de cada argumento deve ampliar ao de seu parâmetro correspondente. Isso é verdadeiro mesmo com o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) definido como `Off`. Se uma sobrecarga exigir qualquer conversão de redução da sua lista de argumentos, que sobrecarregam não é elegível para ser chamado.  
  
- Se você fornecer argumentos que exigem conversões de ampliação, faça seus tipos de dados o mais próximo possível para os tipos de dados do parâmetro correspondente. Se duas ou mais sobrecargas aceitam os tipos de dados do argumento, o compilador resolve a chamada para a sobrecarga que chama para a menor quantidade de ampliação.  
  
 Você pode reduzir a chance de incompatibilidade de tipo de dados usando o [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) palavra de-de chave do conversão ao preparar seus argumentos.  
  
### <a name="overload-resolution-failure"></a>Falha na resolução de sobrecarga  
 Quando você chama um procedimento sobrecarregado, o compilador tenta eliminar todos, exceto uma das sobrecargas. Se tiver êxito, ele resolve a chamada para essa sobrecarga. Se ele elimina todas as sobrecargas, ou se ele não é possível reduzir as sobrecargas qualificadas para uma única de candidato, ele gera um erro.  
  
 O exemplo a seguir ilustra o processo de resolução de sobrecarga.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 Na primeira chamada, o compilador elimina a primeira sobrecarga porque o tipo do primeiro argumento (`Short`) restringe-se para o tipo do parâmetro correspondente (`Byte`). Em seguida, ele elimina a terceira sobrecarga porque cada tipo de argumento na segunda sobrecarga (`Short` e `Single`) é ampliado para o tipo correspondente no terceiro sobrecarregamento (`Integer` e `Single`). A segunda sobrecarga requer menos alargamento, portanto, o compilador usa para a chamada.  
  
 Na segunda chamada, o compilador não pode eliminar qualquer uma das sobrecargas com base na restrição. Elimina a terceira sobrecarga pela mesma razão que na primeira chamada, pois ele pode chamar a segunda sobrecarga com menos alargamento dos tipos de argumento. No entanto, o compilador não pode resolver entre as primeiros e segunda sobrecargas. Cada um tem um tipo de parâmetro definidas se expande para o tipo correspondente no outro (`Byte` à `Short`, mas `Single` para `Double`). Portanto, o compilador gera um erro de resolução de sobrecarga.  
  
 **Abordagem correta:** Para poder chamar um procedimento sobrecarregado sem ambiguidade, use [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para corresponder os tipos de dados de argumento para os tipos de parâmetro. O exemplo a seguir mostra uma chamada para `z` que força a resolução para a segunda sobrecarga.  
  
 [!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>Sobrecarga de resolução com opcional e argumentos ParamArray  
 Se duas sobrecargas de um procedimento possuem assinaturas idênticas, exceto pelo fato de que o último parâmetro é declarado [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) em um e [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) no outro, o compilador resolve uma chamada para o procedimento de acordo com a correspondência mais próxima. Para obter mais informações, consulte [resolução de sobrecarga](./overload-resolution.md).  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Procedimentos de Função](./function-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Considerações sobre Procedimentos de Sobrecarga](./considerations-in-overloading-procedures.md)
- [Resolução de Sobrecarga](./overload-resolution.md)

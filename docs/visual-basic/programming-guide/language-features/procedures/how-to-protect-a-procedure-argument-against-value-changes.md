---
title: Como proteger um argumento de procedimento contra alterações de valor
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 75c718c83f36e2f0b2c4cfb5504c2d740eaa3520
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347896"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Como proteger um argumento de procedimento contra alterações de valor (Visual Basic)
Se um procedimento declara um parâmetro como [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), o Visual Basic fornece ao código do procedimento uma referência direta para o elemento de programação subjacente do argumento no código de chamada. Isso permite que o procedimento altere o valor subjacente do argumento no código de chamada. Em alguns casos, o código de chamada talvez queira estar protegido contra essa alteração.  
  
 Você pode proteger um argumento de alteração, declarando o parâmetro correspondente com a palavra-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) no procedimento. Se desejar alterar um argumento fornecido em alguns casos, mas outros não, você pode declará-la `ByRef` e permitir que o código de chamada determine o mecanismo de passagem em cada chamada. Ele faz isso colocando o argumento correspondente entre parênteses para passá-lo por valor, ou não envolvendo em parênteses para passá-lo por referência. Para obter mais informações, consulte [como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra dois procedimentos que têm uma variável de matriz e operam em seus elementos. O procedimento `increase` simplesmente adiciona um para cada elemento. O procedimento `replace` atribui uma nova matriz para o parâmetro `a()` e, em seguida, adiciona um para cada elemento. No entanto, a reatribuição não afeta a variável da array subjacente no código de chamada.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 A primeira chamada de `MsgBox` exibe "após o aumento (n): 11, 21, 31, 41". Como a matriz `n` é um tipo de referência, `increase` pode alterar seus membros, embora o mecanismo de passagem seja `ByVal`.  
  
 A segunda `MsgBox` chamada exibe "Após replace (n): 11, 21, 31, 41". Como `n` é passado `ByVal`, `replace` não pode modificar a `n` variável no código de chamada atribuindo uma nova matriz a ela. Quando `replace` cria a nova instância de matriz `k` e a atribui à variável local `a`, ela perde a referência a `n` passada pelo código de chamada. Quando ele altera os membros de `a`, somente a matriz local `k` é afetada. Portanto, `replace` não incrementa os valores de matriz `n` no código de chamada.  
  
## <a name="compile-the-code"></a>Compilar o código  
 O padrão no Visual Basic é passar argumentos por valor. No entanto, é uma boa prática de programação incluir as palavras-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) em cada parâmetro declarado. Isso torna seu código mais fácil de ler.  
  
## <a name="see-also"></a>Veja também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)
- [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)
- [Diferenças entre argumentos modificáveis e não modificáveis](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Como alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)
- [Como forçar um argumento a ser passado por Valor](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)

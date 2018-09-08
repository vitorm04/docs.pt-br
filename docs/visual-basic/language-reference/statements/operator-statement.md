---
title: Instrução Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: 69dea99cf71bd1e091116e54e244abfca291ffdb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185698"
---
# <a name="operator-statement"></a>Instrução Operator
Declara o símbolo do operador, operandos e código que definem um procedimento de operador em uma classe ou estrutura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a>Partes  
 `attrlist`  
 Opcional. Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `Public`  
 Necessário. Indica que esse procedimento de operador tem [pública](../../../visual-basic/language-reference/modifiers/public.md) acesso.  
  
 `Overloads`  
 Opcional. Ver [sobrecarrega](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Necessário. Indica que esse procedimento de operador é um [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) procedimento.  
  
 `Shadows`  
 Opcional. Ver [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Necessário para um operador de conversão, a menos que você especifique `Narrowing`. Indica que esse procedimento de operador define uma [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversão. Consulte "De ampliação e redução conversões" nesta página de Ajuda.  
  
 `Narrowing`  
 Necessário para um operador de conversão, a menos que você especifique `Widening`. Indica que esse procedimento de operador define uma [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversão. Consulte "De ampliação e redução conversões" nesta página de Ajuda.  
  
 `operatorsymbol`  
 Necessário. O símbolo ou o identificador do operador que define este procedimento de operador.  
  
 `operand1`  
 Necessário. O nome e tipo de operando único de um operador unário (incluindo um operador de conversão) ou o operando esquerdo de um operador binário.  
  
 `operand2`  
 Necessário para os operadores binários. O nome e o tipo do operando à direita de um operador binário.  
  
 `operand1` e `operand2` tem a seguinte sintaxe e partes:  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Parte|Descrição|  
|----------|-----------------|  
|`ByVal`|Opcional, mas o mecanismo de passagem deve ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Necessário. Nome da variável que representa esse operando. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|Opcional, a menos que `Option Strict` é `On`. Tipo de dados desse operando.|  
  
 `type`  
 Opcional, a menos que `Option Strict` é `On`. Retorna o tipo de dados do valor do qual o procedimento de operador.  
  
 `statements`  
 Opcional. Bloco de instruções que executa o procedimento de operador.  
  
 `returnvalue`  
 Necessário. O valor que o procedimento de operador retorna para o código de chamada.  
  
 `End` `Operator`  
 Necessário. Finaliza a definição desse procedimento de operador.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar `Operator` somente em uma classe ou estrutura. Isso significa que o *contexto de declaração* para um operador não pode ser um arquivo de origem, namespace, módulo, interface, procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Todos os operadores devem ser `Public Shared`. Não é possível especificar `ByRef`, `Optional`, ou `ParamArray` para qualquer um dos operandos.  
  
 Você não pode usar o símbolo do operador ou o identificador para manter um valor de retorno. Você deve usar o `Return` instrução e ele devem especificar um valor. Qualquer número de `Return` instruções podem aparecer em qualquer lugar no procedimento.  
  
 Definindo um operador dessa maneira é chamado *sobrecarregamento*, se você usar o `Overloads` palavra-chave. A tabela a seguir lista os operadores que você pode definir.  
  
|Tipo|Operadores|  
|----------|---------------|  
|Unário|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binário|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversão (unário)|`CType`|  
  
 Observe que o `=` operador na lista binária é o operador de comparação, não o operador de atribuição.  
  
 Quando você define `CType`, você deve especificar `Widening` ou `Narrowing`.  
  
## <a name="matched-pairs"></a>Pares correspondentes  
 Você deve definir determinados operadores como pares correspondentes. Se você definir um operador de tal par, você deve definir o outro também. Os pares correspondentes são os seguintes:  
  
-   `=` e `<>`  
  
-   `>` e `<`  
  
-   `>=` e `<=`  
  
-   `IsTrue` e `IsFalse`  
  
## <a name="data-type-restrictions"></a>Restrições de tipo de dados  
 Cada operador que você definir deve envolver a classe ou estrutura na qual você defini-lo. Isso significa que a classe ou estrutura deve aparecer como o tipo de dados das seguintes opções:  
  
-   O operando de um operador unário.  
  
-   Pelo menos um dos operandos de um operador binário.  
  
-   O operando ou tipo de retorno de um operador de conversão.  
  
 Determinados operadores têm dados adicionais que digite as restrições, da seguinte maneira:  
  
-   Se você definir a `IsTrue` e `IsFalse` operadores, eles devem retornar o `Boolean` tipo.  
  
-   Se você definir a `<<` e `>>` operadores, eles devem ambos especificam o `Integer` de tipo para o `operandtype` de `operand2`.  
  
 O tipo de retorno não precisa corresponder ao tipo de qualquer um dos operandos. Por exemplo, um operador de comparação, como `=` ou `<>` pode retornar `Boolean` mesmo se nenhum dos operandos é `Boolean`.  
  
## <a name="logical-and-bitwise-operators"></a>Operadores lógicos e bit a bit  
 O `And`, `Or`, `Not`, e `Xor` operadores podem executar operações de lógicas ou bit a bit no Visual Basic. No entanto, se você definir um destes operadores em uma classe ou estrutura, você pode definir apenas sua operação bit a bit.  
  
 Não é possível definir a `AndAlso` operador diretamente com um `Operator` instrução. No entanto, você pode usar `AndAlso` se você cumpriu as seguintes condições:  
  
-   Você definiu `And` nos mesmos tipos de operando que você deseja usar para `AndAlso`.  
  
-   Sua definição de `And` retorna o mesmo tipo que a classe ou estrutura na qual você o define.  
  
-   Você definiu o `IsFalse` operador na classe ou estrutura na qual você definiu `And`.  
  
 Da mesma forma, você pode usar `OrElse` se você tiver definido `Or` nos operandos mesmos, com o tipo de retorno da classe ou estrutura e você tiver definido `IsTrue` na classe ou estrutura.  
  
## <a name="widening-and-narrowing-conversions"></a>Conversões de Widening e Narrowing  
 Um *conversão de ampliação* sempre terá êxito em tempo de execução, enquanto um *conversão de estreitamento* pode falhar em tempo de execução. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Se você declarar um procedimento de conversão para ser `Widening`, seu código de procedimento não deve gerar falhas. Isso significa que o seguinte:  
  
-   Ele deve sempre retornar um valor válido do tipo `type`.  
  
-   Ele deve tratar todas as possíveis exceções e outras condições de erro.  
  
-   Ele deve tratar retorna qualquer erro de qualquer procedimento que ele chama.  
  
 Se houver a possibilidade que um procedimento de conversão talvez não seja bem-sucedida, ou que ele pode causar uma exceção sem tratamento, você deve declará-la para ser `Narrowing`.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Operator` instrução para definir o contorno de uma estrutura que inclui procedimentos de operador para o `And`, `Or`, `IsFalse`, e `IsTrue` operadores. `And` e `Or` cada usam dois operandos do tipo `abc` e o tipo de retorno `abc`. `IsFalse` e `IsTrue` utilizar um único operando do tipo de cada `abc` e retornar `Boolean`. Essas definições permitem que o código de chamada usar `And`, `AndAlso`, `Or`, e `OrElse` com operandos do tipo `abc`.  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Ampliação](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Procedimentos de Operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Como chamar um procedimento de operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [Como usar uma classe que define operadores](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)

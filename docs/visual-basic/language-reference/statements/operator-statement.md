---
title: "Instru&#231;&#227;o Operator | Microsoft Docs"
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
  - "vb.operator"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Função CType, instrução Operator"
  - "palavra-chave Narrowing, operadores de conversão"
  - "sobrecarga de operador"
  - "procedimentos de Operador"
  - "instrução Operator"
  - "operadores [Visual Basic]"
  - "operadores [Visual Basic], sobrecarga"
  - "operadores sobrecarregados"
  - "procedimentos, operator"
  - "sintaxe, Procedimentos de Operador"
  - "código do Visual Basic, operadores"
  - "palavra-chave Widening, operadores de conversão"
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Operator
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara o símbolo do operador, operandos e código que definem um procedimento de operador em uma classe ou estrutura.  
  
## Sintaxe  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## Partes  
 `attrlist`  
 Opcional.  Veja [Lista de Atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `Public`  
 Obrigatório.  Indica que este procedimento de operador tem [Público](../../../visual-basic/language-reference/modifiers/public.md) acesso.  
  
 `Overloads`  
 Opcional.  Consulte [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Obrigatório.  Indica que este procedimento de operador é um [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) procedimento.  
  
 `Shadows`  
 Opcional.  Consulte [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Necessário para um operador de conversão, a menos que você especifique `Narrowing`.  Indica que este procedimento de operador define uma [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversão.  Consulte "Widening e restringir conversões" nesta página Ajuda.  
  
 `Narrowing`  
 Necessário para um operador de conversão, a menos que você especifique `Widening`.  Indica que este procedimento de operador define uma [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversão.  Consulte "Widening e restringir conversões" nesta página Ajuda.  
  
 `operatorsymbol`  
 Obrigatório.  O símbolo ou o identificador do operador que este procedimento de operador define.  
  
 `operand1`  
 Obrigatório.  O nome e o tipo de operando esquerdo de um operador binário ou de único operando de um operador unário \(incluindo um operador de conversão\).  
  
 `operand2`  
 Obrigatório para operadores binários.  O nome e o tipo do operando à direita de um operador binário.  
  
 `operand1`e `operand2` que a sintaxe e partes a seguir:  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Parte|Descrição|  
|-----------|---------------|  
|`ByVal`|É opcional, mas o mecanismo de passagem deve ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Obrigatório.  Nome da variável que representa esse operando.  Consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|Opcional, a menos que `Option Strict` é `On`.  Tipo de dados deste operando.|  
  
 `type`  
 Opcional, a menos que `Option Strict` é `On`.  Tipo de dados do valor o procedimento de operador retorna.  
  
 `statements`  
 Opcional.  Bloco de instruções que o procedimento de operador é executado.  
  
 `returnvalue`  
 Obrigatório.  O valor que o procedimento de operador retorna para o código de chamada.  
  
 `End` `Operator`  
 Obrigatório.  Finaliza a definição deste procedimento de operador.  
  
## Comentários  
 Você pode usar `Operator` somente em uma classe ou estrutura.  Isso significa que o  *o contexto de declaração* para um operador não pode ser um arquivo de origem, espaço para nome, módulo, interface, procedimento ou bloco.  Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Todos os operadores devem ser `Public Shared`.  Não é possível especificar `ByRef`, `Optional`, ou `ParamArray` para qualquer operador.  
  
 Você não pode usar o símbolo do operador ou o identificador para armazenar um valor de retorno.  Você deve usar o `Return` instrução e ele devem especificar um valor.  Qualquer número de `Return` declarações podem aparecer em qualquer lugar no procedimento.  
  
 A definição de um operador dessa maneira é chamado de  *a sobrecarga de operador*, quer você use ou não o `Overloads` palavra\-chave.  A tabela a seguir lista os operadores que você pode definir.  
  
|Tipo|Operadores|  
|----------|----------------|  
|Unário|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binário|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversão \(Unário\)|`CType`|  
  
 Observe que o operador `=` na lista binária é o operador de comparação, não o operador de atribuição.  
  
 Quando você define `CType`, você deve especificar um `Widening` ou `Narrowing`.  
  
## Pares correspondentes  
 Você deve definir determinados operadores como pares correspondentes.  Se você definir um operador de tal um par, você deve definir o outro também.  Os pares correspondentes são os seguintes:  
  
-   `=` e `<>`  
  
-   `>` e `<`  
  
-   `>=` e `<=`  
  
-   `IsTrue` e `IsFalse`  
  
## Restrições de tipo de dados  
 Cada operador que você define deve envolver a classe ou estrutura na qual você defini\-la.  Isso significa que a classe ou estrutura deve aparecer como o tipo de dados das seguintes opções:  
  
-   O operando de um operador unário.  
  
-   Pelo menos um dos operandos de um operador binário.  
  
-   O operando ou o tipo de retorno de um operador de conversão.  
  
 Determinados operadores têm dados adicionais digite restrições, como segue:  
  
-   Se você definir a `IsTrue` e `IsFalse` operadores, eles devem ambos retornar o `Boolean` tipo.  
  
-   Se você definir a `<<` e `>>` operadores, eles devem especificar o `Integer` tipo para o `operandtype` de `operand2`.  
  
 O tipo de retorno não precisam corresponder ao tipo de qualquer operador.  Por exemplo, um operador de comparação, como `=` ou `<>` pode retornar `Boolean` , mesmo se nenhum operando for `Boolean`.  
  
## Operadores bit a bit e lógicas  
 O `And`, `Or`, `Not`, e `Xor` operadores podem executar operações de lógicas ou bit a bit em Visual Basic.  No entanto, se você definir um desses operadores em uma classe ou estrutura, você pode definir somente sua operação bit a bit.  
  
 Não é possível definir o `AndAlso` operador diretamente com um `Operator` instrução.  Entretanto, você pode usar `AndAlso` se você tiver cumprido as seguintes condições:  
  
-   Você definiu `And` nos mesmos tipos de operando que você deseja usar para `AndAlso`.  
  
-   Sua definição de `And` retorna o mesmo tipo que a classe ou estrutura na qual você o define.  
  
-   Você definiu a `IsFalse` o operador na classe ou estrutura na qual você definiu `And`.  
  
 Da mesma forma, você pode usar `OrElse` se você tiver definido `Or` na mesmos operandos, com o tipo de retorno da classe ou estrutura e você tiver definido `IsTrue` na classe ou estrutura.  
  
## Conversões Ampliadoras e Redutoras  
 A  *widening conversão* sempre é bem\-sucedida em tempo de execução, enquanto um  *Estreitando conversão* pode falhar em tempo de execução.  Para obter mais informações, consulte [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Se você declarar um procedimento de conversão para ser `Widening`, seu código de procedimento não deve gerar quaisquer falhas.  Isso significa o seguinte:  
  
-   Ele sempre deve retornar um valor válido do tipo `type`.  
  
-   Ele deve tratar todas as possíveis exceções e outras condições de erro.  
  
-   Ele deve tratar qualquer retorna erro de qualquer procedimento chama.  
  
 Se houver qualquer possibilidade de que um procedimento de conversão talvez não seja bem\-sucedida, ou que ele pode causar uma exceção não tratada, você deve declarar que ele seja `Narrowing`.  
  
## Exemplo  
 O seguinte exemplo de código usa a `Operator` a instrução para definir o contorno de uma estrutura que inclui procedimentos de operador para o `And`, `Or`, `IsFalse`, e `IsTrue` operadores.  `And`e `Or` cada levar dois operandos do tipo `abc` e tipo de retorno `abc`.  `IsFalse`e `IsTrue` cada ter um único operando do tipo `abc` e retornar `Boolean`.  Essas definições permitem que o código de chamada usar `And`, `AndAlso`, `Or`, e `OrElse` com operandos do tipo `abc`.  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## Consulte também  
 [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Como chamar um procedimento de operador](../Topic/How%20to:%20Call%20an%20Operator%20Procedure%20\(Visual%20Basic\).md)   
 [Como usar uma classe que define operadores](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
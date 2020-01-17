---
title: Subprocedimentos
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 9ca1d302a0bc8e989e0b2dddf8cce68e89211d57
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163807"
---
# <a name="sub-procedures-visual-basic"></a>Sub procedimentos (Visual Basic)

Um procedimento `Sub` é uma série de instruções Visual Basic delimitadas pelas instruções `Sub` e `End Sub`. O procedimento de `Sub` executa uma tarefa e, em seguida, retorna o controle para o código de chamada, mas não retorna um valor para o código de chamada.

Cada vez que o procedimento é chamado, suas instruções são executadas, começando com a primeira instrução executável após a instrução de `Sub` e terminando com a primeira instrução `End Sub`, `Exit Sub`ou `Return` encontrada.

Você pode definir um procedimento `Sub` em módulos, classes e estruturas. Por padrão, é `Public`, o que significa que você pode chamá-lo de qualquer lugar em seu aplicativo que tenha acesso ao módulo, à classe ou à estrutura na qual você o definiu. O *método* Term descreve um `Sub` ou `Function` procedimento que é acessado de fora de sua definição de módulo, classe ou estrutura. Para obter mais informações, consulte [Procedimentos](./index.md).

Um procedimento `Sub` pode receber argumentos, como constantes, variáveis ou expressões, que são passados para ele pelo código de chamada.

## <a name="declaration-syntax"></a>Sintaxe de declaração

A sintaxe para declarar um procedimento `Sub` é a seguinte:

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

O `modifiers` pode especificar o nível de acesso e informações sobre sobrecarga, substituição, compartilhamento e sombreamento. Para obter mais informações, consulte [sub Statement](../../../language-reference/statements/sub-statement.md).

## <a name="parameter-declaration"></a>Declaração de parâmetro

Você declara cada parâmetro de procedimento da mesma forma como declara uma variável, especificando o nome do parâmetro e o tipo de dados. Você também pode especificar o mecanismo de passagem e se o parâmetro é opcional ou uma matriz de parâmetros.

A sintaxe para cada parâmetro na lista de parâmetros é a seguinte:

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

Se o parâmetro for opcional, você também deverá fornecer um valor padrão como parte de sua declaração. A sintaxe para especificar um valor padrão é a seguinte:

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a>Parâmetros como variáveis locais

Quando o controle passa para o procedimento, cada parâmetro é tratado como uma variável local. Isso significa que seu tempo de vida é o mesmo que o do procedimento, e seu escopo é o procedimento completo.

## <a name="calling-syntax"></a>Sintaxe de chamada

Você invoca um procedimento `Sub` explicitamente com uma instrução de chamada autônoma. Você não pode chamá-lo usando seu nome em uma expressão. Você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses. Se nenhum argumento for fornecido, você pode opcionalmente omitir os parênteses. O uso da palavra-chave `Call` é opcional, mas não é recomendado.

A sintaxe de uma chamada para um procedimento `Sub` é a seguinte:

```vb
[Call] SubName[(argumentlist)]
```

Você pode chamar um método `Sub` de fora da classe que o define. Primeiro, você precisa usar a palavra-chave `New` para criar uma instância da classe ou chamar um método que retorne uma instância da classe. Para obter mais informações, consulte [novo operador](../../../language-reference/operators/new-operator.md). Em seguida, você pode usar a seguinte sintaxe para chamar o método `Sub` no objeto de instância:

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a>Ilustração de declaração e chamada

O procedimento a seguir `Sub` informa ao operador do computador qual tarefa o aplicativo está prestes a executar e também exibe um carimbo de data/hora. Em vez de duplicar esse código no início de cada tarefa, o aplicativo simplesmente chama `tellOperator` de vários locais. Cada chamada passa uma cadeia de caracteres no argumento `task` que identifica a tarefa que está sendo iniciada.

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

O exemplo a seguir mostra uma chamada típica para `tellOperator`.

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a>Veja também

- [Procedimentos](./index.md)
- [Procedimentos de Função](./function-procedures.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Procedimentos de Operador](./operator-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Sub](../../../language-reference/statements/sub-statement.md)
- [Como chamar um procedimento que não retorne um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [Como: chamar um manipulador de eventos no Visual Basic](./how-to-call-an-event-handler.md)

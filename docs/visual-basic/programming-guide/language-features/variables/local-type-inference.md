---
title: Inferência de tipo local (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 786466cb0b94a96e629a1f173388ed7d40be7256
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661914"
---
# <a name="local-type-inference-visual-basic"></a>Inferência de tipo local (Visual Basic)
O compilador do Visual Basic usa *inferência* para determinar os tipos de dados de variáveis locais declaradas sem um `As` cláusula. O compilador infere o tipo da variável do tipo da expressão de inicialização. Isso permite que você declare variáveis sem especificar explicitamente um tipo, conforme mostrado no exemplo a seguir. Como resultado das declarações, ambos `num1` e `num2` são fortemente tipadas como inteiros.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  Se você não quiser `num2` no exemplo anterior para ser digitado como um `Integer`, você pode especificar outro tipo, usando uma declaração como `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.  

> [!NOTE]
>  Inferência de tipo pode ser usada somente para as variáveis locais não-estático; ele não pode ser usado para determinar o tipo de funções, propriedades ou campos de classe.
 
 Inferência de tipo local se aplica no nível de procedimento. Ele não pode ser usado para declarar variáveis no nível de módulo (dentro de uma classe, estrutura, módulo ou interface mas não dentro de um procedimento ou bloco). Se `num2` no exemplo anterior, foram um campo de uma classe em vez de uma variável local em um procedimento, a declaração poderia causar um erro com `Option Strict` e deseja classificar `num2` como um `Object` com `Option Strict` off. Da mesma forma, inferência de tipo local não se aplica a variáveis de nível de procedimento declaradas como `Static`.  
  
## <a name="type-inference-vs-late-binding"></a>Vs de inferência de tipo. Associação tardia  
 Código que usa a inferência de tipo é semelhante ao código que dependa da ligação tardia. No entanto, inferência de tipos fortemente a variável em vez de deixá-lo como `Object`. O compilador usa o inicializador da variável para determinar o tipo da variável no tempo de compilação para produzir código early bound. No exemplo anterior, `num2`, como `num1`, é digitado como um `Integer`.  
  
 O comportamento de variáveis de early bound difere das variáveis de associação tardia, para o qual o tipo é conhecido somente em tempo de execução. Saber o tipo no início, permite que o compilador identificar problemas antes da execução, alocar memória com precisão e execute outras otimizações. Associação antecipada também permite que o ambiente de desenvolvimento integrado (IDE) para fornecer o IntelliSense ajuda sobre os membros de um objeto do Visual Basic. Associação antecipada também é preferencial para o desempenho. Isso ocorre porque todos os dados armazenados em uma variável de associação tardia devem ser encapsulados como tipo `Object`, e acesso a membros do tipo em tempo de execução faz com que o programa mais lento.  
  
## <a name="examples"></a>Exemplos  
 Inferência de tipo ocorre quando uma variável local é declarada sem uma `As` cláusula e inicializado. O compilador usa o tipo de valor inicial atribuído como o tipo da variável. Por exemplo, cada uma das seguintes linhas de código declara uma variável do tipo `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 O código a seguir demonstra duas maneiras equivalentes de criar uma matriz de inteiros.  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 É conveniente usar inferência de tipo para determinar o tipo de uma variável de controle de loop. No código a seguir, o compilador infere que `number` é um `Integer` porque `someNumbers2` do exemplo anterior é uma matriz de inteiros.  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 Inferência de tipo local pode ser usada em `Using` instruções para estabelecer o tipo do nome do recurso, como demonstra o exemplo a seguir.  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 O tipo de uma variável também pode ser inferido de valores de retorno de funções, como o exemplo a seguir demonstra. Ambos `pList1` e `pList2` são matrizes de processos porque `Process.GetProcesses` retorna uma matriz de processos.  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` permite que você especifique se a inferência de tipo local é permitida em um arquivo específico. Para habilitar ou bloquear a opção, digite uma das seguintes instruções no início do arquivo.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Se você não especificar um valor para `Option Infer` em seu código, é o padrão do compilador `Option Infer On`. 
  
 Se o valor definido para `Option Infer` em um arquivo entrar em conflito com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.  
  
 Para obter mais informações, consulte [instrução opção inferir](../../../../visual-basic/language-reference/statements/option-infer-statement.md) e [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Consulte também

- [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Associação Antecipada e Tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Instrução For...Next](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

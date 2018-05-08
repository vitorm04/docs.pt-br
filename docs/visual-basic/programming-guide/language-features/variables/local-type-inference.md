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
ms.openlocfilehash: b33b8b2d17c240e380377528d4f5d2f511381a7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="local-type-inference-visual-basic"></a>Inferência de tipo local (Visual Basic)
O compilador do Visual Basic usa *inferência de tipo* para determinar os tipos de dados de variável local declarada sem um `As` cláusula. O compilador infere o tipo da variável do tipo da expressão de inicialização. Isso permite que você declare variáveis sem especificar explicitamente um tipo, conforme mostrado no exemplo a seguir. Como resultado de declarações, ambos `num1` e `num2` são fortemente tipadas como inteiros.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  Se você não quiser `num2` no exemplo anterior para ser digitado como um `Integer`, você pode especificar outro tipo usando uma declaração como `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.  

> [!NOTE]
>  Inferência de tipo pode ser usada somente para as variáveis locais não-estático; ele não pode ser usado para determinar o tipo de funções, propriedades ou campos de classe.
 
 Inferência de tipo local se aplica no nível de procedimento. Ele não pode ser usado para declarar variáveis no nível de módulo (dentro de uma classe, estrutura, módulo ou interface mas não dentro de um procedimento ou bloco). Se `num2` no exemplo anterior foi um campo de uma classe em vez de uma variável local em um procedimento, a declaração causará um erro com `Option Strict` e deseja classificar `num2` como um `Object` com `Option Strict` off. Da mesma forma, inferência de tipo local não se aplica a variáveis de nível de procedimento declaradas como `Static`.  
  
## <a name="type-inference-vs-late-binding"></a>Tipo de inferência vs. Associação tardia  
 Código que usa a inferência de tipo é semelhante a códigos que contem com associação tardia. No entanto, a inferência de tipo tipos altamente variável em vez de deixá-lo como `Object`. O compilador usa o inicializador de variável para determinar o tipo da variável no tempo de compilação para gerar código de associação inicial. No exemplo anterior, `num2`, como `num1`, é digitado como um `Integer`.  
  
 O comportamento de variáveis de early bound difere das variáveis de associação tardia, para o qual o tipo é conhecido apenas em tempo de execução. Saber o tipo de início permite que o compilador identificar problemas antes da execução, alocar memória com precisão e executar outras otimizações. Associação antecipada também permite que o ambiente de desenvolvimento integrado (IDE) para fornecer IntelliSense ajuda sobre os membros de um objeto do Visual Basic. Associação antecipada também é preferencial para o desempenho. Isso ocorre porque todos os dados armazenados em uma variável de associação tardia devem ser encapsulados como tipo `Object`, e acessar os membros do tipo em tempo de execução faz com que o programa mais lento.  
  
## <a name="examples"></a>Exemplos  
 Inferência de tipo ocorre quando uma variável local é declarada sem um `As` cláusula e inicializado. O compilador usa o tipo de valor inicial atribuído como o tipo da variável. Por exemplo, cada uma das linhas de código a seguir declara uma variável do tipo `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 O código a seguir demonstra duas maneiras equivalentes para criar uma matriz de inteiros.  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 É conveniente usar inferência de tipo para determinar o tipo de uma variável de controle de loop. No código a seguir, o compilador infere que `number` é um `Integer` porque `someNumbers2` do exemplo anterior é uma matriz de inteiros.  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 Inferência de tipo local pode ser usada em `Using` instruções para estabelecer o tipo do nome do recurso, como demonstrado no exemplo a seguir.  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 O tipo de uma variável também pode ser inferido de valores de retorno de funções, como demonstrado no exemplo a seguir. Ambos `pList1` e `pList2` são conjuntos de processos porque `Process.GetProcesses` retorna uma matriz de processos.  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a>Opção Infer  
 `Option Infer` permite que você especifique se a inferência de tipo local é permitida em um arquivo específico. Para permitir ou bloquear a opção, digite uma das seguintes instruções no início do arquivo.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Se você não especificar um valor para `Option Infer` em seu código, o padrão do compilador é `Option Infer On`. Para projetos atualizados do [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] ou anterior, o padrão do compilador é `Option Infer Off`.  
  
 Se o valor definido para `Option Infer` em um arquivo entrar em conflito com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.  
  
 Para obter mais informações, consulte [opção Infer instrução](../../../../visual-basic/language-reference/statements/option-infer-statement.md) e [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Associação Antecipada e Tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Instrução For...Next](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

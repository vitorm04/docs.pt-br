---
title: Tipos de valor que permitem valor nulo (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8734114b9d657066a0ef0b2d648f0290c03b1cbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-value-types-visual-basic"></a>Tipos de valor que permitem valor nulo (Visual Basic)
Às vezes, você trabalha com um tipo de valor que não tem um valor definido em determinadas circunstâncias. Por exemplo, um campo em um banco de dados pode ter que distinguir entre ter um valor atribuído que é significativo e não ter um valor atribuído. Tipos de valor podem ser estendidos para levar seus valores normais ou um valor nulo. Tal extensão é chamada de um *tipo anulável*.  
  
 Cada tipo anulável é construído a partir genérica <xref:System.Nullable%601> estrutura. Considere um banco de dados que rastreia atividades relacionadas ao trabalho. O exemplo a seguir constrói um valor nulo `Boolean` e declara uma variável do tipo. Você pode escrever a declaração de três maneiras:  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 A variável `ridesBusToWork` pode conter um valor de `True`, um valor de `False`, ou nenhum valor. O valor inicial padrão não é nenhum valor, que nesse caso pode significar que as informações ainda não foi obtidas para essa pessoa. Por outro lado, `False` pode significar que a informação foi obtida e a pessoa não ir de barramento para trabalhar.  
  
 Você pode declarar variáveis e propriedades com tipos anuláveis, e você pode declarar uma matriz com os elementos de um tipo anulável. Você pode declarar procedimentos com tipos anuláveis como parâmetros, e você pode retornar um tipo anulável de um `Function` procedimento.  
  
 Não é possível construir um tipo anulável em um tipo de referência como uma matriz, uma `String`, ou uma classe. O tipo subjacente deve ser um tipo de valor. Para obter mais informações, consulte [tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
## <a name="using-a-nullable-type-variable"></a>Usando uma variável de tipo anulável  
 Os membros mais importantes de um tipo anulável são suas <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A> propriedades. Para uma variável de um tipo anulável, <xref:System.Nullable%601.HasValue%2A> informa se a variável contém um valor definido. Se <xref:System.Nullable%601.HasValue%2A> é `True`, você pode ler o valor de <xref:System.Nullable%601.Value%2A>. Observe que tanto <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A> são `ReadOnly` propriedades.  
  
### <a name="default-values"></a>Valores padrão  
 Quando você declara uma variável com um tipo anulável, seu <xref:System.Nullable%601.HasValue%2A> propriedade tem um valor padrão de `False`. Isso significa que, por padrão, a variável não tem nenhum valor definido, em vez do valor padrão de seu tipo de valor subjacente. No exemplo a seguir, a variável `numberOfChildren` inicialmente não tem valor definido, mesmo que o valor padrão de `Integer` tipo é 0.  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 Um valor nulo é útil para indicar um valor desconhecido ou indefinido. Se `numberOfChildren` tivesse sido declarado como `Integer`, não haverá nenhum valor que pode indicar que as informações não estão disponíveis no momento.  
  
### <a name="storing-values"></a>Armazenando valores  
 Você pode armazenar um valor em uma variável ou propriedade de um tipo anulável maneira normal. O exemplo a seguir atribui um valor à variável `numberOfChildren` declarada no exemplo anterior.  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 Se uma variável ou propriedade de um tipo anulável contiver um valor definido, você poderá revertê-la para a seu estado inicial de não ter um valor atribuído. Você pode fazer isso definindo a variável ou propriedade `Nothing`, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  Embora você possa atribuir `Nothing` a uma variável de um tipo anulável, você não pode testá-lo para `Nothing` usando o sinal de igual. Comparação que utiliza o sinal de igual, `someVar = Nothing`, sempre é avaliada como `Nothing`. Você pode testar a variável <xref:System.Nullable%601.HasValue%2A> propriedade `False`, ou de teste usando o `Is` ou `IsNot` operador.  
  
### <a name="retrieving-values"></a>Recuperando valores  
 Para recuperar o valor de uma variável de um tipo anulável, primeiro você deve testar seu <xref:System.Nullable%601.HasValue%2A> propriedade para confirmar que ela tem um valor. Se você tentar ler o valor quando <xref:System.Nullable%601.HasValue%2A> é `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] lança um <xref:System.InvalidOperationException> exceção. O exemplo a seguir mostra a maneira recomendada para ler a variável `numberOfChildren` dos exemplos anteriores.  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## <a name="comparing-nullable-types"></a>Comparando tipos anuláveis  
 Quando for anulável `Boolean` variáveis são usadas em expressões booleanas, o resultado poderá ser `True`, `False`, ou `Nothing`. Esta é a tabela verdade para `And` e `Or`. Porque `b1` e `b2` agora tem três valores possíveis, existem nove combinações para avaliar.  
  
|B1|B2|B1 e b2|B1 ou b2|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 Quando o valor de uma variável ou expressão booleana for `Nothing`, não é `true` nem `false`. Considere o exemplo a seguir.  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 Neste exemplo, `b1 And b2` é avaliada como `Nothing`. Como resultado, o `Else` cláusula é executada em cada `If` instrução e a saída é o seguinte:  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso`e `OrElse`, avaliação de curto-circuito que usam deve avaliar os segundos operandos quando o primeiro é avaliado como `Nothing`.  
  
## <a name="propagation"></a>Propagação  
 Se um ou ambos os operandos de aritmética, comparação, shift ou operação de tipo for anulável, o resultado da operação também é anulável. Se ambos os operandos têm valores que não são `Nothing`, a operação é realizada nos valores subjacentes dos operandos, como se nenhum deles fosse um tipo anulável. No exemplo a seguir, variáveis `compare1` e `sum1` são de tipo implícito. Se você posicionar o ponteiro do mouse sobre eles, você verá que o compilador infere tipos anuláveis para os dois.  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 Se um ou ambos os operandos tem um valor de `Nothing`, o resultado será `Nothing`.  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## <a name="using-nullable-types-with-data"></a>Usando tipos anuláveis com dados  
 Um banco de dados é um dos locais mais importantes para usar tipos anuláveis. Nem todos os objetos de banco de dados no momento oferecer suporte a tipos anuláveis, mas os adaptadores de tabelas geradas pelo designer. Consulte "Suporte de TableAdapter para tipos anuláveis" [visão geral de TableAdapter](/visualstudio/data-tools/tableadapter-overview).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [Usando tipos que permitem valor nulo](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Visão geral de TableAdapter](/visualstudio/data-tools/tableadapter-overview)  
 [Operador If](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Operador Is](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [Operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md)

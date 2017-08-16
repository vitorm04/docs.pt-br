---
title: "Relacionamentos de tipo em operações de consulta (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
caps.latest.revision: 34
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a966b69feca7a7021cafbccb7971913ea781c479
ms.lasthandoff: 03/13/2017

---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relacionamentos de tipo em operações de consulta (Visual Basic)
Variáveis usadas em [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] consulta operações são fortemente tipadas e devem ser compatíveis entre si. Tipagem forte é usado na fonte de dados, a consulta em si e a execução da consulta. A ilustração a seguir identifica os termos usados para descrever um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta. Para obter mais informações sobre as partes de uma consulta, consulte [operações básicas de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Consulta de pseudocódigo com elementos realçados.](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
Partes de uma consulta LINQ  
  
 O tipo da variável de intervalo na consulta deve ser compatível com o tipo dos elementos na fonte de dados. O tipo da variável de consulta deve ser compatível com o elemento de sequência definido o `Select` cláusula. Por fim, o tipo dos elementos da sequência também deve ser compatível com o tipo da variável de controle de loop é usado no `For Each` instrução que executa a consulta. Este tipagem forte facilita a identificação de erros de tipo em tempo de compilação.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]conveniente forte digitando implementando inferência de tipo local, também conhecido como *digitação implícita*. Que recurso é usado no exemplo anterior, e você verá que ele é usado em todo o [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] amostras e documentação. No Visual Basic, inferência de tipo local é realizada simplesmente usando um `Dim` instrução sem um `As` cláusula. No exemplo a seguir, `city` é fortemente tipada como uma cadeia de caracteres.  
  
 [!code-vb[VbLINQTypeRels n º&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  Inferência de tipo local funciona somente quando `Option Infer` é definido como `On`. Para obter mais informações, consulte [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 No entanto, mesmo se você usar a inferência de tipo local em uma consulta, as mesmas relações de tipo estão presentes entre as variáveis na fonte de dados, a variável de consulta e o loop de execução de consulta. É útil ter uma compreensão básica dessas relações de tipo quando você estiver escrevendo [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas ou trabalhar com os exemplos e exemplos de código na documentação.  
  
 Talvez seja necessário especificar um tipo explícito para uma variável de intervalo que não coincide com o tipo retornado da fonte de dados. Você pode especificar o tipo da variável de intervalo usando um `As` cláusula. No entanto, isso resulta em um erro se a conversão for um [conversão de redução](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e `Option Strict` é definido como `On`. Portanto, recomendamos que você realize a conversão dos valores recuperados da fonte de dados. Você pode converter os valores da fonte de dados para o tipo de variável de intervalo explícito usando o <xref:System.Linq.Enumerable.Cast%2A>método.</xref:System.Linq.Enumerable.Cast%2A> Você também pode converter os valores selecionados no `Select` cláusula para um tipo explícito é diferente do tipo da variável de intervalo. Esses pontos são ilustrados no código a seguir.  
  
 [!code-vb[VbLINQTypeRels n º&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Consultas que retornam elementos inteiros da fonte de dados  
 A exemplo a seguir mostra um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] operação que retorna uma sequência de elementos selecionados da fonte de dados de consulta. O código-fonte, `names`, contém uma matriz de cadeias de caracteres, e a saída da consulta é uma sequência contendo cadeias de caracteres que começam com a letra M.  
  
 [!code-vb[VbLINQTypeRels n º&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 Isso é equivalente ao código a seguir, mas é muito menor e mais fáceis de escrever. Dependência de inferência de tipo local em consultas é o estilo preferido no Visual Basic.  
  
 [!code-vb[VbLINQTypeRels n º&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 As seguintes relações existem em ambos os exemplos de código anterior, se os tipos são determinados implícita ou explicitamente.  
  
1.  O tipo dos elementos na fonte de dados, `names`, é o tipo da variável de intervalo, `name`, na consulta.  
  
2.  O tipo do objeto selecionado, `name`, determina o tipo de variável de consulta, `mNames`. Aqui `name` é uma cadeia de caracteres, portanto, a variável de consulta é IEnumerable (Of String) no Visual Basic.  
  
3.  A consulta definida no `mNames` é executado no `For Each` loop. O loop itera sobre o resultado da execução da consulta. Porque `mNames`, quando ele é executado, retornará uma sequência de cadeias de caracteres da variável de iteração do loop, `nm`, também é uma cadeia de caracteres.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Consultas que retornam um campo de elementos selecionados  
 A exemplo a seguir mostra um [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] operação que retorna uma sequência contendo apenas uma parte de cada elemento selecionado da fonte de dados de consulta. A consulta usa uma coleção de `Customer` objetos como sua fonte de dados e projeta apenas o `Name` propriedade no resultado. Como o nome do cliente é uma cadeia de caracteres, a consulta produz uma sequência de cadeias de caracteres como saída.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 As relações entre as variáveis são como aqueles no exemplo mais simples.  
  
1.  O tipo dos elementos na fonte de dados, `customers`, é o tipo da variável de intervalo, `cust`, na consulta. Neste exemplo, o que é do tipo `Customer`.  
  
2.  O `Select` instrução retorna a `Name` propriedade de cada `Customer` objeto em vez de todo o objeto. Porque `Name` é uma cadeia de caracteres, a variável de consulta, `custNames`, novamente será IEnumerable (Of String), não do `Customer`.  
  
3.  Porque `custNames` representa uma sequência de cadeias de caracteres, o `For Each` variável de iteração do loop, `custName`, deve ser uma cadeia de caracteres.  
  
 Sem inferência de tipo local, o exemplo anterior seria mais complicado para escrever e entender, como mostra o exemplo a seguir.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="queries-that-require-anonymous-types"></a>Consultas que exigem tipos anônimos  
 O exemplo a seguir mostra uma situação mais complexa. No exemplo anterior, era inconveniente especificar explicitamente os tipos de todas as variáveis. Neste exemplo, é impossível. Em vez de selecionar toda `Customer` elementos de fonte de dados ou um único campo de cada elemento, o `Select` cláusula nesta consulta retorna duas propriedades do original `Customer` objeto: `Name` e `City`. Em resposta ao `Select` cláusula, o compilador define um tipo anônimo que contém essas duas propriedades. O resultado da execução `nameCityQuery` no `For Each` loop é uma coleção de instâncias do novo tipo anônimo. Como o tipo anônimo não tem nenhum nome utilizável, você não pode especificar o tipo de `nameCityQuery` ou `custInfo` explicitamente. Ou seja, com um tipo anônimo, você não tem nenhum nome de tipo para usar no lugar de `String` em `IEnumerable(Of String)`. Para obter mais informações, consulte [tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Embora não seja possível especificar tipos de todas as variáveis no exemplo anterior, as relações permanecem os mesmos.  
  
1.  Novamente, o tipo dos elementos na fonte de dados é o tipo da variável de intervalo na consulta. Neste exemplo, `cust` é uma instância de `Customer`.  
  
2.  Porque o `Select` instrução produz um tipo anônimo, a variável de consulta, `nameCityQuery`, devem ser digitadas implicitamente como um tipo anônimo. Um tipo anônimo não tem nenhum nome pode ser usado e, portanto, não pode ser especificado explicitamente.  
  
3.  O tipo da variável de iteração no `For Each` loop é o tipo anônimo criado na etapa 2. Porque o tipo não tem nenhum nome utilizável, o tipo da variável de iteração de loop deve ser determinado implicitamente.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)

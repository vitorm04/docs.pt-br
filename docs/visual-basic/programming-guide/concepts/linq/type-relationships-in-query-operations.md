---
title: Relacionamentos de tipo em operações de consulta (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: f1084ffcf0b5330185a44eda8721ef2a03413602
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258143"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relacionamentos de tipo em operações de consulta (Visual Basic)
Variáveis usadas em [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] consulta operações são fortemente tipadas e devem ser compatíveis entre si. Tipagem forte é usada na fonte de dados, na própria consulta e na execução da consulta. A ilustração a seguir identifica os termos usados para descrever um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta. Para obter mais informações sobre as partes de uma consulta, consulte [operações básicas de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Consulta de pseudocódigo com elementos realçados. ](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
Partes de uma consulta LINQ  
  
 O tipo da variável de intervalo na consulta deve ser compatível com o tipo dos elementos na fonte de dados. O tipo da variável de consulta deve ser compatível com o elemento de sequência definido no `Select` cláusula. Por fim, o tipo dos elementos da sequência também deve ser compatível com o tipo da variável de controle de loop é usado no `For Each` instrução que executa a consulta. Este tipagem forte facilita a identificação de erros de tipo em tempo de compilação.  
  
 O Visual Basic faz forte digitando conveniente com a implementação de inferência de tipo local, também conhecido como *tipagem implícita*. Que recurso é usado no exemplo anterior, e você verá que ele é usado em todo o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] amostras e documentação. No Visual Basic, inferência de tipo local é realizada simplesmente usando um `Dim` instrução sem uma `As` cláusula. No exemplo a seguir, `city` é fortemente tipada como uma cadeia de caracteres.  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  Inferência de tipo local funciona somente quando `Option Infer` é definido como `On`. Para obter mais informações, consulte [instrução opção inferir](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 No entanto, mesmo se você usar inferência de tipo local em uma consulta, os mesmo relacionamentos de tipo estão presentes entre as variáveis na fonte de dados, a variável de consulta e o loop de execução de consulta. É útil ter uma compreensão básica desses relacionamentos de tipo quando você estiver escrevendo [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consultas ou trabalhar com os exemplos e exemplos de código na documentação.  
  
 Talvez você precise especificar um tipo explícito para uma variável de intervalo que não coincide com o tipo retornado da fonte de dados. Você pode especificar o tipo da variável de intervalo usando um `As` cláusula. No entanto, isso resulta em um erro se a conversão for um [conversão de estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e `Option Strict` é definido como `On`. Portanto, é recomendável que você realize a conversão dos valores recuperados da fonte de dados. Você pode converter os valores da fonte de dados para o tipo de variável de intervalo explícita usando o <xref:System.Linq.Enumerable.Cast%2A> método. Você também pode converter os valores selecionados no `Select` cláusula para um tipo explícito que é diferente do tipo da variável de intervalo. Esses pontos são ilustrados no código a seguir.  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Consultas que retornam elementos inteiros da fonte de dados  
 A exemplo a seguir mostra um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operação que retorna uma sequência de elementos selecionados dos dados de origem de consulta. O código-fonte, `names`, contém uma matriz de cadeias de caracteres, e a saída da consulta é uma sequência que contém cadeias de caracteres que começam com a letra M.  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 Isso é equivalente ao código a seguir, mas é muito menor e mais fáceis de escrever. Dependência de inferência de tipo local nas consultas é o estilo preferencial no Visual Basic.  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 As seguintes relações existem em ambos os exemplos de código anterior, se os tipos são determinados implícita ou explicitamente.  
  
1.  O tipo dos elementos na fonte de dados, `names`, é o tipo da variável de intervalo, `name`, na consulta.  
  
2.  O tipo do objeto selecionado, `name`, determina o tipo da variável de consulta, `mNames`. Aqui `name` é uma cadeia de caracteres, portanto, a variável de consulta é IEnumerable (Of String) no Visual Basic.  
  
3.  A consulta definida na `mNames` é executado no `For Each` loop. O loop itera sobre o resultado da execução da consulta. Porque `mNames`, quando ele é executado, retornará uma sequência de cadeias de caracteres, a variável de iteração do loop, `nm`, também é uma cadeia de caracteres.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Consultas que retornam um campo de elementos selecionados  
 A exemplo a seguir mostra um [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operação que retorna uma sequência que contém apenas uma parte de cada elemento selecionado da fonte de dados de consulta. A consulta usa uma coleção de `Customer` objetos como sua fonte de dados e somente projetos de `Name` propriedade no resultado. Como o nome do cliente é uma cadeia de caracteres, a consulta produz uma sequência de cadeias de caracteres como saída.  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 As relações entre as variáveis são como aqueles no exemplo mais simples.  
  
1.  O tipo dos elementos na fonte de dados, `customers`, é o tipo da variável de intervalo, `cust`, na consulta. Neste exemplo, o que é do tipo `Customer`.  
  
2.  O `Select` instrução retorna o `Name` propriedade de cada `Customer` objeto em vez de todo o objeto. Porque `Name` é uma cadeia de caracteres, a variável de consulta `custNames`, novamente será IEnumerable (Of String), não do `Customer`.  
  
3.  Porque `custNames` representa uma sequência de cadeias de caracteres, o `For Each` variável de iteração do loop, `custName`, deve ser uma cadeia de caracteres.  
  
 Sem inferência de tipo local, o exemplo anterior seria mais complicado de escrever e entender, como mostra o exemplo a seguir.  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a>Consultas que exigem tipos anônimos  
 O exemplo a seguir mostra uma situação mais complexa. No exemplo anterior, era inconveniente especificar os tipos para todas as variáveis explicitamente. Neste exemplo, é impossível. Em vez de selecionar toda `Customer` elementos da fonte de dados, ou um único campo de cada elemento, o `Select` cláusula nessa consulta retornará duas propriedades do original `Customer` objeto: `Name` e `City`. Em resposta ao `Select` cláusula, o compilador define um tipo anônimo que contém essas duas propriedades. O resultado da execução `nameCityQuery` no `For Each` loop é uma coleção de instâncias do novo tipo anônimo. Como o tipo anônimo tem nenhum nome utilizável, é possível especificar o tipo de `nameCityQuery` ou `custInfo` explicitamente. Ou seja, com um tipo anônimo, você não tem nenhum nome de tipo para usar no lugar de `String` em `IEnumerable(Of String)`. Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 Embora não seja possível especificar os tipos para todas as variáveis no exemplo anterior, as relações permanecem os mesmos.  
  
1.  Novamente, o tipo dos elementos na fonte de dados é o tipo da variável de intervalo na consulta. Neste exemplo, `cust` é uma instância de `Customer`.  
  
2.  Porque o `Select` instrução produz um tipo anônimo, a variável de consulta, `nameCityQuery`, deve ser digitada implicitamente como um tipo anônimo. Um tipo anônimo não tem nenhum nome utilizável e, portanto, não pode ser especificado explicitamente.  
  
3.  O tipo de variável de iteração no `For Each` loop é o tipo anônimo criado na etapa 2. Como o tipo não tem nenhum nome utilizável, o tipo da variável de iteração de loop deve ser determinado implicitamente.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/index.md)

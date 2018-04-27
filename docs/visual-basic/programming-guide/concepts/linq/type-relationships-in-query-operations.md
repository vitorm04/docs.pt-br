---
title: Relacionamentos de tipo em operações de consulta (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
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
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e38f51d77869dcca8a81fdcbc70aed32c4146935
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relacionamentos de tipo em operações de consulta (Visual Basic)
Variáveis usadas em [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] consulta operações são fortemente tipadas e devem ser compatíveis entre si. Tipagem forte é usada na fonte de dados, a consulta em si e a execução da consulta. A ilustração a seguir identifica os termos usados para descrever um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consulta. Para obter mais informações sobre as partes de uma consulta, consulte [operações básicas de consulta (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Consulta de pseudocódigo com elementos realçados. ] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
Partes de uma consulta LINQ  
  
 O tipo da variável de intervalo na consulta deve ser compatível com o tipo dos elementos na fonte de dados. O tipo da variável de consulta deve ser compatível com o elemento de sequência definido no `Select` cláusula. Por fim, o tipo dos elementos da sequência também deve ser compatível com o tipo da variável de controle de loop é usado no `For Each` instrução que executa a consulta. Este tipagem forte facilita a identificação de erros de tipo em tempo de compilação.  
  
 Visual Basic conveniente forte digitando implementando inferência de tipo local, também conhecido como *implícita digitando*. Que o recurso é usado no exemplo anterior, e você verá que ele usado em todo o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] amostras e documentação. No Visual Basic, a inferência de tipo local é realizada simplesmente usando um `Dim` instrução sem um `As` cláusula. No exemplo a seguir, `city` é fortemente tipada como uma cadeia de caracteres.  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  Inferência de tipo local só funciona quando `Option Infer` é definido como `On`. Para obter mais informações, consulte [opção Infer instrução](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 No entanto, mesmo se você usar a inferência de tipo local em uma consulta, as mesmas relações de tipo estão presentes entre as variáveis na fonte de dados, a variável de consulta e o loop de execução de consulta. É útil ter um entendimento básico desses relacionamentos de tipo quando você estiver escrevendo [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consultas ou trabalhar com os exemplos e exemplos de código na documentação.  
  
 Talvez seja necessário especificar um tipo explícito para uma variável de intervalo que não coincide com o tipo retornado da fonte de dados. Você pode especificar o tipo da variável de intervalo usando um `As` cláusula. No entanto, isso resulta em um erro se a conversão for um [conversão de estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e `Option Strict` é definido como `On`. Portanto, recomendamos que você realize a conversão dos valores recuperados da fonte de dados. Você pode converter os valores da fonte de dados para o tipo de variável de intervalo explícita usando o <xref:System.Linq.Enumerable.Cast%2A> método. Você também pode converter os valores selecionados no `Select` cláusula para um tipo explícito que é diferente do tipo da variável de intervalo. Esses pontos são ilustrados no código a seguir.  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Consultas que retornam elementos inteiros da fonte de dados  
 A exemplo a seguir mostra um [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operação que retorna uma sequência de elementos selecionados da fonte de dados de consulta. A fonte, `names`, contém uma matriz de cadeias de caracteres, e a saída da consulta é uma sequência que contém cadeias de caracteres que começam com a letra M.  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 Isso é equivalente ao seguinte código, mas é muito menor e mais fáceis de escrever. A dependência de inferência de tipo local em consultas é o estilo preferencial no Visual Basic.  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 As seguintes relações existem em ambos os exemplos de código anterior, se os tipos são determinados implícita ou explicitamente.  
  
1.  O tipo dos elementos na fonte de dados, `names`, é o tipo da variável de intervalo, `name`, na consulta.  
  
2.  O tipo do objeto selecionado, `name`, determina o tipo da variável de consulta, `mNames`. Aqui `name` é uma cadeia de caracteres, portanto, a variável de consulta é IEnumerable (Of String) no Visual Basic.  
  
3.  A consulta definida no `mNames` é executado no `For Each` loop. O loop é iterado sobre o resultado da execução da consulta. Porque `mNames`, quando ele é executado, retornará uma sequência de cadeias de caracteres da variável de iteração do loop, `nm`, também é uma cadeia de caracteres.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Consultas que retornam um campo de elementos selecionados  
 A exemplo a seguir mostra um [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operação que retorna uma sequência que contém apenas uma parte de cada elemento selecionado da fonte de dados de consulta. A consulta usa uma coleção de `Customer` objetos como sua fonte de dados e projetos apenas o `Name` propriedade no resultado. Como o nome do cliente é uma cadeia de caracteres, a consulta produz uma sequência de cadeias de caracteres como saída.  
  
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
  
2.  O `Select` instrução retorna o `Name` propriedade de cada `Customer` objeto em vez do objeto inteiro. Porque `Name` é uma cadeia de caracteres, a variável de consulta, `custNames`, novamente será IEnumerable (Of String), não do `Customer`.  
  
3.  Porque `custNames` representa uma sequência de cadeias de caracteres, o `For Each` variável de iteração do loop, `custName`, deve ser uma cadeia de caracteres.  
  
 Sem inferência de tipo local, o exemplo anterior seria mais complicado escrever e entender, como mostra o exemplo a seguir.  
  
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
 O exemplo a seguir mostra uma situação mais complexa. No exemplo anterior, era inconveniente especificar os tipos de todas as variáveis explicitamente. Neste exemplo, é impossível. Em vez de selecionar todo `Customer` elementos da fonte de dados, ou um único campo de cada elemento, o `Select` cláusula nesta consulta retorna duas propriedades do original `Customer` objeto: `Name` e `City`. Em resposta ao `Select` cláusula, o compilador define um tipo anônimo que contém essas duas propriedades. O resultado da execução `nameCityQuery` no `For Each` loop é uma coleção de instâncias do novo tipo anônimo. Porque o tipo anônimo não tem utilizável nome, você não pode especificar o tipo de `nameCityQuery` ou `custInfo` explicitamente. Ou seja, com um tipo anônimo, você não tem nenhum nome de tipo a ser usado no lugar de `String` em `IEnumerable(Of String)`. Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
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
  
 Embora não seja possível especificar os tipos de todas as variáveis no exemplo anterior, as relações permanecem os mesmos.  
  
1.  Novamente, o tipo dos elementos na fonte de dados é o tipo da variável de intervalo na consulta. Neste exemplo, `cust` é uma instância de `Customer`.  
  
2.  Porque o `Select` instrução produz um tipo anônimo, a variável de consulta, `nameCityQuery`, deve ser digitada implicitamente como um tipo anônimo. Um tipo anônimo não tiver usado um nome e, portanto, não pode ser especificado explicitamente.  
  
3.  O tipo da variável de iteração no `For Each` loop é o tipo anônimo criado na etapa 2. Porque o tipo não tem utilizável nome, o tipo da variável de iteração de loop deve ser determinado implicitamente.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)

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
ms.openlocfilehash: 4851d0a74de38f0fb6b6deee34cf7b3e66eb11b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937489"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>Relacionamentos de tipo em operações de consulta (Visual Basic)
As variáveis usadas [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] em operações de consulta são fortemente tipadas e devem ser compatíveis entre si. A tipagem forte é usada na fonte de dados, na própria consulta e na execução da consulta. A ilustração a seguir identifica os termos usados para [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] descrever uma consulta. Para obter mais informações sobre as partes de uma consulta, consulte [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Captura de tela mostrando uma consulta de pseudocódigo com elementos realçados.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 O tipo da variável de intervalo na consulta deve ser compatível com o tipo dos elementos na fonte de dados. O tipo da variável de consulta deve ser compatível com o elemento Sequence definido na `Select` cláusula. Por fim, o tipo dos elementos de sequência também deve ser compatível com o tipo da variável de controle de loop que é usada `For Each` na instrução que executa a consulta. Essa tipagem forte facilita a identificação de erros de tipo no momento da compilação.  
  
 Visual Basic facilita a digitação de rigidez, implementando a inferência de tipo local, também conhecida como *digitação implícita*. Esse recurso é usado no exemplo anterior e você verá que ele é usado em todos os [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] exemplos e documentação. Em Visual Basic, a inferência de tipo local é realizada simplesmente `Dim` usando uma instrução `As` sem uma cláusula. No exemplo a seguir, `city` é fortemente tipado como uma cadeia de caracteres.  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
> A inferência de tipo local `Option Infer` só funciona quando `On`é definido como. Para obter mais informações, consulte [instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 No entanto, mesmo se você usar a inferência de tipo local em uma consulta, as mesmas relações de tipo estarão presentes entre as variáveis na fonte de dados, a variável de consulta e o loop de execução da consulta. É útil ter um entendimento básico dessas relações de tipo quando você estiver escrevendo [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consultas ou trabalhando com exemplos e códigos de exemplo na documentação.  
  
 Talvez seja necessário especificar um tipo explícito para uma variável de intervalo que não corresponda ao tipo retornado da fonte de dados. Você pode especificar o tipo da variável de intervalo usando uma `As` cláusula. No entanto, isso resultará em um erro se a conversão for uma conversão `Option Strict` de [restrição](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e `On`for definida como. Portanto, recomendamos que você execute a conversão nos valores recuperados da fonte de dados. Você pode converter os valores da fonte de dados para o tipo de variável de intervalo explícito usando <xref:System.Linq.Enumerable.Cast%2A> o método. Você também pode converter os valores selecionados na `Select` cláusula para um tipo explícito que seja diferente do tipo da variável de intervalo. Esses pontos são ilustrados no código a seguir.  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>Consultas que retornam elementos inteiros dos dados de origem  
 O exemplo a seguir mostra [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] uma operação de consulta que retorna uma sequência de elementos selecionados a partir dos dados de origem. A origem, `names`, contém uma matriz de cadeias de caracteres e a saída da consulta é uma sequência que contém cadeias de caracteres que começam com a letra M.  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 Isso é equivalente ao código a seguir, mas é muito mais curto e mais fácil de escrever. A dependência da inferência de tipo local em consultas é o estilo preferencial em Visual Basic.  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 As relações a seguir existem nos dois exemplos de código anteriores, independentemente de os tipos serem determinados implicitamente ou explicitamente.  
  
1. O tipo dos elementos na fonte de dados, `names`, é o tipo da variável de intervalo, `name`, na consulta.  
  
2. O tipo do objeto selecionado, `name`, determina o tipo da variável de consulta,. `mNames` Aqui `name` está uma cadeia de caracteres, portanto, a variável de consulta é IEnumerable (Of String) em Visual Basic.  
  
3. A consulta definida em `mNames` é executada `For Each` no loop. O loop itera sobre o resultado da execução da consulta. Como `mNames`, quando é executado, retornará uma sequência de cadeias de caracteres, a `nm`variável de iteração de loop,, também é uma cadeia de caracteres.  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>Consultas que retornam um campo dos elementos selecionados  
 O exemplo a seguir mostra [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] uma operação de consulta que retorna uma sequência contendo apenas uma parte de cada elemento selecionado na fonte de dados. A consulta usa uma coleção de `Customer` objetos como sua fonte de dados e projeta apenas `Name` a propriedade no resultado. Como o nome do cliente é uma cadeia de caracteres, a consulta produz uma sequência de cadeias de caracteres como saída.  
  
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
  
 As relações entre as variáveis são como as do exemplo mais simples.  
  
1. O tipo dos elementos na fonte de dados, `customers`, é o tipo da variável de intervalo, `cust`, na consulta. Neste exemplo, esse tipo é `Customer`.  
  
2. A `Select` instrução retorna a `Name` propriedade de cada `Customer` objeto em vez de todo o objeto. Como `Name` é uma cadeia de caracteres, a variável `custNames`de consulta,, novamente será IEnumerable (Of String), `Customer`não de.  
  
3. Como `custNames` representa uma sequência de cadeias de `For Each` caracteres, a variável de `custName`iteração do loop,, deve ser uma cadeia de caracteres.  
  
 Sem a inferência de tipo local, o exemplo anterior seria mais complicado de escrever e entender, como mostra o exemplo a seguir.  
  
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
 O exemplo a seguir mostra uma situação mais complexa. No exemplo anterior, era inconveniente especificar tipos para todas as variáveis explicitamente. Neste exemplo, é impossível. Em vez de selecionar `Customer` elementos inteiros da fonte de dados, ou um único campo de cada elemento, `Select` a cláusula nessa consulta retorna duas propriedades do objeto original `Customer` : `Name` e `City`. Em resposta à `Select` cláusula, o compilador define um tipo anônimo que contém essas duas propriedades. O resultado da execução `nameCityQuery` `For Each` no loop é uma coleção de instâncias do novo tipo anônimo. Como o tipo anônimo não tem nome utilizável, você não pode especificar o tipo `nameCityQuery` de `custInfo` ou explicitamente. Ou seja, com um tipo anônimo, você não tem nenhum nome de tipo a ser usado `String` no `IEnumerable(Of String)`lugar do. Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
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
  
 Embora não seja possível especificar tipos para todas as variáveis no exemplo anterior, as relações permanecem as mesmas.  
  
1. O tipo dos elementos na fonte de dados é novamente o tipo da variável de intervalo na consulta. Neste exemplo, `cust` é uma instância do `Customer`.  
  
2. Como a `Select` instrução produz um tipo anônimo, a variável de consulta `nameCityQuery`,, deve ser digitada implicitamente como um tipo anônimo. Um tipo anônimo não tem nome utilizável e, portanto, não pode ser especificado explicitamente.  
  
3. O tipo da variável de iteração no `For Each` loop é o tipo anônimo criado na etapa 2. Como o tipo não tem nenhum nome utilizável, o tipo da variável de iteração de loop deve ser determinado implicitamente.  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)

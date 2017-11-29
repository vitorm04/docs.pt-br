---
title: "Relacionamentos de tipo em operações de consulta LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a088a7f673a9f6aea7a0f50e18746259171bb7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="type-relationships-in-linq-query-operations-c"></a>Relacionamentos de tipo em operações de consulta LINQ (C#)
Para escrever consultas com eficiência, você precisa entender como os tipos de variáveis em uma operação de consulta completa se relacionam entre si. Se compreender esses relacionamentos, você compreenderá com maior facilidade os exemplos de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] e exemplos de código na documentação. Além disso, você compreenderá o que ocorre nos bastidores quando variáveis são tipadas de forma implícita usando `var`.  
  
 Operações de consulta de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] são fortemente tipadas na fonte de dados, na própria consulta e na execução da consulta. O tipo das variáveis na consulta deve ser compatível com o tipo dos elementos na fonte de dados e com o tipo da variável de iteração na instrução `foreach`. Essa tipagem forte garante que erros de tipo sejam capturados em tempo de compilação, quando podem ser corrigidos antes que os usuários os encontrem.  
  
 Para demonstrar essas relações de tipo, a maioria dos exemplos a seguir usam tipagem explícita para todas as variáveis. O último exemplo mostra como os mesmos princípios se aplicam mesmo quando você usa tipagem implícita usando [var](../../../../csharp/language-reference/keywords/var.md).  
  
## <a name="queries-that-do-not-transform-the-source-data"></a>Consultas que não transformam os dados de origem  
 A ilustração a seguir mostra uma operação de consulta de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects que não executa transformações nos dados. A fonte contém uma sequência de cadeias de caracteres e a saída da consulta também é uma sequência de cadeias de caracteres.  
  
 ![Relação dos tipos de dados em uma consulta LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")  
  
1.  O argumento de tipo da fonte de dados determina o tipo da variável de intervalo.  
  
2.  O tipo do objeto selecionado determina o tipo da variável de consulta. Esta é uma cadeia de caracteres `name`. Portanto, a variável de consulta é uma `IEnumerable`\<cadeia de caracteres>.  
  
3.  A variável de consulta é iterada na instrução `foreach`. Como a variável de consulta é uma sequência de cadeias de caracteres, a variável de iteração também é uma cadeia de caracteres.  
  
## <a name="queries-that-transform-the-source-data"></a>Consultas que transformam os dados de origem  
 A ilustração a seguir mostra uma operação de consulta de [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] que executa transformações simples nos dados. A consulta usa uma sequência de objetos `Customer` como entrada e seleciona somente a propriedade `Name` no resultado. Como `Name` é uma cadeia de caracteres, a consulta produz uma sequência de cadeias de caracteres como saída.  
  
 ![Uma consulta que transforma o tipo de dados](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")  
  
1.  O argumento de tipo da fonte de dados determina o tipo da variável de intervalo.  
  
2.  A instrução `select` retorna a propriedade `Name` em vez do objeto `Customer` completo. Como `Name` é uma cadeia de caracteres, o argumento de tipo de `custNameQuery` é `string` e não `Customer`.  
  
3.  Como `custNameQuery` é uma sequência de cadeias de caracteres, a variável de iteração do loop `foreach` também deve ser um `string`.  
  
 A ilustração a seguir mostra uma transformação um pouco mais complexa. A instrução `select` retorna um tipo anônimo que captura apenas dois membros do objeto `Customer` original.  
  
 ![Uma consulta que transforma o tipo de dados](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")  
  
1.  O argumento de tipo da fonte de dados sempre é o tipo da variável de intervalo na consulta.  
  
2.  Como a instrução `select` produz um tipo anônimo, a variável de consulta deve ser tipada implicitamente usando `var`.  
  
3.  Como o tipo da variável de consulta é implícito, a variável de iteração no loop `foreach` também deve ser implícito.  
  
## <a name="letting-the-compiler-infer-type-information"></a>Deixando o compilador inferir informações de tipo  
 Embora você precise entender as relações de tipo em uma operação de consulta, você tem a opção de permitir que o compilador fazer todo o trabalho. A palavra-chave [var](../../../../csharp/language-reference/keywords/var.md) pode ser usada para qualquer variável local em uma operação de consulta. A ilustração a seguir é semelhante ao exemplo número 2 que foi discutido anteriormente. No entanto, o compilador fornece o tipo forte para cada variável na operação de consulta.  
  
 ![Fluxo de tipo com tipagem implícita](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")  
  
 Para obter mais informações sobre `var`, consulte [Variáveis de local digitadas implicitamente](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução a LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

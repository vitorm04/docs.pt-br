---
title: "Relacionamentos de tipo em opera&#231;&#245;es de consulta LINQ (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "fontes de dados [LINQ em C#], relacionamentos de tipos"
  - "transformações de dados [LINQ em C#]"
  - "deduzindo informações de tipo [LINQ em C#]"
  - "LINQ [C#], relacionamentos de tipos"
  - "consultas [LINQ in C#], relacionamentos de tipos"
  - "relacionamentos [LINQ em C#]"
  - "informações de tipo deduzidas [LINQ em C#]"
  - "relacionamentos de tipos [LINQ em C#]"
  - "relacionamentos de variáveis [LINQ em C#]"
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Relacionamentos de tipo em opera&#231;&#245;es de consulta LINQ (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Para escrever consultas com eficiência, você deve entender como os tipos de variáveis em uma operação de consulta completa todos se relacionam entre si. Se você compreender esses relacionamentos serão mais fácil compreender o [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] amostras e exemplos de código na documentação. Além disso, você saberá o que ocorre nos bastidores quando variáveis são de tipo implícito usando `var`.  
  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] operações de consulta são fortemente tipada na fonte de dados, a consulta em si e a execução da consulta. O tipo das variáveis na consulta deve ser compatível com o tipo dos elementos na fonte de dados e o tipo da variável de iteração no `foreach` instrução. Este tipagem forte garante que erros de tipo são capturados em tempo de compilação quando eles podem ser corrigidos antes que os usuários encontrem\-los.  
  
 Para demonstrar essas relações de tipo, a maioria dos exemplos a seguir usa uma digitação explícita para todas as variáveis. O último exemplo mostra como os mesmos princípios se aplicam mesmo quando você usa a digitação implícita usando [var](../../../../csharp/language-reference/keywords/var.md).  
  
## Consultas que não transformam os dados de origem  
 A ilustração a seguir mostra um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para objetos de operação executada sem transformações nos dados de consulta. O código\-fonte contém uma sequência de cadeias de caracteres e a saída da consulta também é uma sequência de cadeias de caracteres.  
  
 ![Relação de tipos de dados em uma consulta LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ\_flow1")  
  
1.  O argumento de tipo da fonte de dados determina o tipo da variável de intervalo.  
  
2.  O tipo do objeto selecionado determina o tipo da variável de consulta. Aqui `name` é uma cadeia de caracteres. Portanto, a variável de consulta é um `IEnumerable`\< string \>.  
  
3.  A variável de consulta é iterada no `foreach` instrução. Como a variável de consulta é uma sequência de cadeias de caracteres, a variável de iteração também é uma cadeia de caracteres.  
  
## Consultas que transformam os dados de origem  
 A ilustração a seguir mostra um [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] operação que executa uma transformação simple nos dados de consulta. A consulta usa uma sequência de `Customer` objetos como entrada e seleciona somente os `Name` propriedade no resultado. Porque `Name` é uma cadeia de caracteres, a produzir consulta uma seqüência de cadeias de caracteres como saída.  
  
 ![Uma consulta que transforma o tipo de dados](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ\_flow2")  
  
1.  O argumento de tipo da fonte de dados determina o tipo da variável de intervalo.  
  
2.  O `select` instrução retorna a `Name` propriedade em vez de concluir `Customer` objeto. Porque `Name` é uma cadeia de caracteres, o argumento de tipo de `custNameQuery` é `string`, e não `Customer`.  
  
3.  Porque `custNameQuery` é uma seqüência de cadeias de caracteres, o `foreach` variável de iteração do loop também deve ser um `string`.  
  
 A ilustração a seguir mostra uma transformação um pouco mais complexa. O `select` instrução retorna um tipo anônimo que captura apenas dois membros do original `Customer` objeto.  
  
 ![Uma consulta que transforma o tipo de dados](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ\_flow3")  
  
1.  O argumento de tipo da fonte de dados sempre é o tipo da variável de intervalo na consulta.  
  
2.  Porque o `select` instrução produz um tipo anônimo, a variável de consulta deve ser digitada implicitamente usando `var`.  
  
3.  Porque o tipo da variável de consulta é implícito, a variável de iteração no `foreach` loop também deve ser implícito.  
  
## Permitir que o compilador inferir informações de tipo  
 Embora você deve compreender as relações de tipo em uma operação de consulta, você tem a opção para permitir que o compilador fazer todo o trabalho para você. A palavra\-chave [var](../../../../csharp/language-reference/keywords/var.md) pode ser usado para qualquer variável local em uma operação de consulta. A ilustração a seguir é semelhante ao exemplo número 2 que foi discutido anteriormente. No entanto, o compilador fornece o tipo forte para cada variável na operação de consulta.  
  
 ![Fluxo de tipos com tipagem implícita](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ\_flow4")  
  
 Para obter mais informações sobre `var`, consulte [Variáveis locais de tipo implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## Consulte também  
 [Introdução a LINQ em C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
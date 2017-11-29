---
title: LINQ to Objects (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bb2a6593b02125478f2221a6822dec447921c4f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
O termo "LINQ to Objects" refere-se ao uso de consultas LINQ com qualquer coleção <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601> diretamente, sem o uso de uma API ou provedor LINQ intermediário como o [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) ou [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). Você pode usar o LINQ para consultar qualquer coleção enumerável ​​como <xref:System.Collections.Generic.List%601>, <xref:System.Array> ou <xref:System.Collections.Generic.Dictionary%602>. A coleção pode ser definida pelo usuário ou pode ser devolvida por uma API do .NET Framework.  
  
 Basicamente, o LINQ to Objects representa uma nova abordagem às coleções. Na forma antiga, você precisava escrever loops `foreach` complexos que especificavam como recuperar dados de uma coleção. Na abordagem da LINQ, você escreve o código declarativo que descreve o que você deseja recuperar.  
  
 Além disso, as consultas LINQ oferecem três principais vantagens sobre os loops `foreach` tradicionais:  
  
1.  Elas são mais concisas e legíveis, especialmente quando você filtra várias condições.  
  
2.  Elas fornecem poderosos recursos de filtragem, ordenação e agrupamento com um mínimo de código do aplicativo.  
  
3.  Elas podem ser movidas para outras fontes de dados com pouca ou nenhuma modificação.  
  
 Em geral, quanto mais complexa a operação que você deseja executar sobre os dados, maior benefício você perceberá usando consultas LINQs em vez de técnicas tradicionais de iteração.  
  
 O objetivo desta seção é demonstrar a abordagem LINQ com alguns exemplos selecionados. Não pretendemos que ela seja detalhada.  
  
## <a name="in-this-section"></a>Nesta seção  
 [LINQ e cadeias de caracteres (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 Explica como a LINQ pode ser usada para consultar e transformar cadeias de caracteres e coleções de cadeias de caracteres. Também inclui links para tópicos que demonstram esses princípios.  
  
 [LINQ e reflexão (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 Contém um link para um exemplo que demonstra como a LINQ usa a reflexão.  
  
 [LINQ e diretórios de arquivos (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Explica como a LINQ pode ser usada para interagir com sistemas de arquivos. Também inclui links para tópicos que demonstram esses conceitos.  
  
 [Como consultar um ArrayList com LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Demonstra como consultar um ArrayList no C#.  
  
 [Como adicionar métodos personalizados para consultas LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Explica como estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando os métodos de extensão à interface <xref:System.Collections.Generic.IEnumerable%601>.  
  
 [LINQ (Consulta Integrada à Linguagem) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 Fornece links para tópicos que explicam a LINQ e fornecem exemplos de código que realizam consultas.

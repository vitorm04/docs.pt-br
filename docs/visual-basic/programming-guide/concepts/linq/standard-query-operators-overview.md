---
title: "Visão geral de operadores de consulta padrão (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: eb28988ef49e0583fb7e9197c4e13c84665074ac
ms.lasthandoff: 03/13/2017

---
# <a name="standard-query-operators-overview-visual-basic"></a>Visão geral de operadores de consulta padrão (Visual Basic)
O *operadores de consulta padrão* são os métodos que formam o padrão LINQ. A maioria desses métodos operam em sequências, onde uma sequência é um objeto cujo tipo implementa o <xref:System.Collections.Generic.IEnumerable%601>interface ou <xref:System.Linq.IQueryable%601>interface.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601> Operadores de consulta padrão fornecem recursos de consulta, incluindo a filtragem, projeção, agregação, classificação e muito mais.  
  
 Há dois conjuntos de operadores de consulta padrão da LINQ, que opera em objetos de tipo <xref:System.Collections.Generic.IEnumerable%601>e outros que opera em objetos do tipo <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601> Os métodos que compõem cada conjunto são membros estáticos de <xref:System.Linq.Enumerable>e <xref:System.Linq.Queryable>classes, respectivamente.</xref:System.Linq.Queryable> </xref:System.Linq.Enumerable> Eles são definidos como *métodos de extensão* do tipo que operam em. Isso significa que eles podem ser chamados usando a sintaxe de método estático ou sintaxe de método de instância.  
  
 Além disso, vários métodos de operador de consulta padrão operam em tipos diferentes daqueles com base nos <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601> O <xref:System.Linq.Enumerable>tipo define dois métodos que ambos operam em objetos do tipo <xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable> </xref:System.Linq.Enumerable> Esses métodos, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29>e <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, permitem que você habilitar uma coleção sem parâmetros ou não genérica, a ser consultado no padrão de LINQ.</xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> </xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> Eles fazem isso criando uma coleção de objetos fortemente tipados. A <xref:System.Linq.Queryable>classe define dois métodos semelhantes <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29>e <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, que operam em objetos do tipo <xref:System.Linq.Queryable>.</xref:System.Linq.Queryable> </xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable>  
  
 Os operadores de consulta padrão são diferentes de tempo de sua execução, dependendo se elas retornam um valor singleton ou uma sequência de valores. Os métodos que retornam um valor singleton (por exemplo, <xref:System.Linq.Enumerable.Average%2A>e <xref:System.Linq.Enumerable.Sum%2A>) são executadas imediatamente.</xref:System.Linq.Enumerable.Sum%2A> </xref:System.Linq.Enumerable.Average%2A> Métodos que retornam uma sequência de adiar a execução da consulta e retornam um objeto enumerável.  
  
 No caso de métodos que operam em coleções na memória, ou seja, os métodos que estendem <xref:System.Collections.Generic.IEnumerable%601>, o objeto enumerável retornado captura os argumentos foram passados para o método.</xref:System.Collections.Generic.IEnumerable%601> Quando esse objeto é enumerado, a lógica do operador de consulta é empregada e os resultados da consulta são retornados.  
  
 Por outro lado, métodos que estendem <xref:System.Linq.IQueryable%601>não implementam qualquer comportamento de consulta, mas criar uma árvore de expressão que representa a consulta a ser executada.</xref:System.Linq.IQueryable%601> O processamento de consulta é tratado pela origem <xref:System.Linq.IQueryable%601>objeto.</xref:System.Linq.IQueryable%601>  
  
 Chamadas para métodos de consulta podem ser encadeadas em uma consulta, que permite que consultas ser arbitrariamente complexos.  
  
 O exemplo de código a seguir demonstra como os operadores de consulta padrão podem ser usados para obter informações sobre uma sequência.  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a>Sintaxe de expressão de consulta  
 Alguns dos operadores de consulta padrão usados com mais frequência dedicou c# e Visual Basic sintaxe da palavra-chave linguagem que permita a ser chamado como parte de um *consulta* *expressão*. Para obter mais informações sobre operadores de consulta padrão que têm palavras-chave e suas sintaxes correspondentes dedicados, consulte [sintaxe de expressão de consulta para operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Estendendo operadores de consulta padrão  
 Você pode aumentar o conjunto de operadores de consulta padrão por criando métodos específicos de domínio apropriadas para o domínio de destino ou a tecnologia. Você também pode substituir os operadores de consulta padrão com suas próprias implementações que fornecem serviços adicionais, como avaliação remota, a tradução da consulta e a otimização. Consulte <xref:System.Linq.Enumerable.AsEnumerable%2A>para obter um exemplo.</xref:System.Linq.Enumerable.AsEnumerable%2A>  
  
## <a name="related-sections"></a>Seções relacionadas  
 Os links a seguir levam você a tópicos que fornecem informações adicionais sobre os vários operadores de consulta padrão com base na funcionalidade.  
  
 [Classificando Dados](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [Operações de conjunto (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtragem de dados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [Operações de quantificador (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Operações de projeção (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [Particionamento de dados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Ingressar em operações (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [Agrupando dados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [Operações de geração (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [Operações de igualdade (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [Operações de elemento (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [Convertendo tipos de dados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Operações de concatenação (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Operações de agregação (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 <xref:System.Linq.Queryable></xref:System.Linq.Queryable>   
 [Introdução ao LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)   
 [Sintaxe de expressão de consulta para operadores de consulta padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)   
 [Classificação de operadores de consulta padrão por meio da execução (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)   
 [Métodos de Extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

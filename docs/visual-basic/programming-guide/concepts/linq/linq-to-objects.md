---
title: LINQ to Objects (Visual Basic) | Documentos do Microsoft
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
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d2bc048fea9affd4998430783d20b978317f3897
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
O termo "LINQ to Objects" refere-se ao uso do LINQ consulta com qualquer <xref:System.Collections.IEnumerable>ou <xref:System.Collections.Generic.IEnumerable%601>coleção diretamente, sem o uso de um provedor LINQ intermediário ou a API como [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) ou [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable> Você pode usar o LINQ para consultar qualquer coleção enumerável como <xref:System.Collections.Generic.List%601>, <xref:System.Array>, ou <xref:System.Collections.Generic.Dictionary%602>.</xref:System.Collections.Generic.Dictionary%602> </xref:System.Array> </xref:System.Collections.Generic.List%601> A coleção pode ser definido pelo usuário ou pode ser retornada por uma API do .NET Framework.  
  
 Basicamente, o LINQ to Objects representa uma nova abordagem para coleções. Na forma antiga, você precisava escrever loops `For Each` complexos que especificavam como recuperar dados de uma coleção. A abordagem do LINQ, você escreve código declarativo que descreve o que você deseja recuperar.  
  
 Além disso, consultas LINQ oferecem três principais vantagens tradicionais `For Each` loops:  
  
1.  Elas são mais concisas e legíveis, especialmente quando você filtra várias condições.  
  
2.  Elas fornecem poderosos recursos de filtragem, ordenação e agrupamento com um mínimo de código do aplicativo.  
  
3.  Elas podem ser movidas para outras fontes de dados com pouca ou nenhuma modificação.  
  
 Em geral, quanto mais complexa a operação que você deseja executar nos dados, o maior benefício você perceberá usando LINQ em vez de técnicas tradicionais de iteração.  
  
 O objetivo desta seção é demonstrar a abordagem do LINQ com alguns exemplos selecionados. Não pretendemos que ela seja detalhada.  
  
## <a name="in-this-section"></a>Nesta seção  
 [LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 Explica como o LINQ pode ser usado para consultar e transformar coleções de cadeias de caracteres e cadeias de caracteres. Também inclui links para tópicos que demonstram esses princípios.  
  
 [LINQ e reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Links para um exemplo que demonstra como LINQ usa reflexão.  
  
 [LINQ e diretórios de arquivos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Explica como o LINQ pode ser usado para interagir com sistemas de arquivos. Também inclui links para tópicos que demonstram esses conceitos.  
  
 [Como: consultar um ArrayList com LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Demonstra como consultar um ArrayList no c#.  
  
 [Como: adicionar métodos personalizados para consultas LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Explica como estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando métodos de extensão para o <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601>  
  
 [Consulta integrada à linguagem (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Fornece links para tópicos que explicam o LINQ e fornecem exemplos de código que executam consultas.

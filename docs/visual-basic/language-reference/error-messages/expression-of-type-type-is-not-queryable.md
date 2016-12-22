---
title: "A express&#227;o do tipo &lt;type&gt; n&#227;o pode ser consultada | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36593"
  - "vbc36593"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36593"
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A express&#227;o do tipo &lt;type&gt; n&#227;o pode ser consultada
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Expressão do tipo \<type\>. não é que podem ser consultados.Certifique\-se de que não estiver faltando um conjunto de módulos \(assembly\) de referência e \/ ou namespace de importação para o provedor LINQ.  
  
 Queryable tipos são definidos na caixa <xref:System.Linq>, <xref:System.Data.Linq> e <xref:System.Xml.Linq> namespaces.  Você deve importar um ou mais desses namespaces para executar consultas LINQ.  
  
 O <xref:System.Linq> namespace permite consulta objetos, como Coleções e matrizes usando LINQ.  
  
 O <xref:System.Data.Linq> namespace permite que você consultar o ADO.NET DataSets e SQL Server bancos de dados usando LINQ.  
  
 O <xref:System.Xml.Linq> namespace permite que você XML consulta usando LINQ e para utilizar os recursos XML Visual Basic.  
  
 **Identificação do erro:**  BC36593  
  
### Para corrigir este erro  
  
1.  Adicione uma instrução `Import` para o <xref:System.Linq>, <xref:System.Data.Linq>, ou <xref:System.Xml.Linq> namespace para o arquivo de código.  Você também pode importar namespaces para o seu projeto, usando a página **References** do criador do projeto \( **My Project** \).  
  
2.  Certifique\-se de que o tipo que você tenha identificado como a origem da sua consulta é um tipo passível de consulta.  Ou seja, um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.  
  
## Consulte também  
 <xref:System.Linq>   
 <xref:System.Data.Linq>   
 <xref:System.Xml.Linq>   
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Instrução Imports \(tipo e namespace .NET\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Página Referências, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)
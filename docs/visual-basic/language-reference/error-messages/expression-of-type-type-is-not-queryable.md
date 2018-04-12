---
title: A expressão do tipo &lt;tipo&gt; não é passível de consulta
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f2b98bf48f0b3965929f9211c2944ff97754f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>A expressão do tipo &lt;tipo&gt; não é passível de consulta
A expressão do tipo \<tipo > não é passível de consulta. Certifique-se de que não está faltando uma importação de referência e/ou namespace do assembly para o provedor LINQ.  
  
 Queryable tipos são definidos no <xref:System.Linq>, <xref:System.Data.Linq>, e <xref:System.Xml.Linq> namespaces. Você deve importar um ou mais desses namespaces para executar consultas LINQ.  
  
 O <xref:System.Linq> namespace permite consulta objetos, como coleções e matrizes usando LINQ.  
  
 O <xref:System.Data.Linq> namespace permite que você consultar conjuntos de dados ADO.NET e bancos de dados do SQL Server usando LINQ.  
  
 O <xref:System.Xml.Linq> namespace permite que você XML consulta usando LINQ e para usar os recursos de XML no Visual Basic.  
  
 **ID do erro:** BC36593  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Adicionar uma `Import` instrução para o <xref:System.Linq>, <xref:System.Data.Linq>, ou <xref:System.Xml.Linq> namespace ao seu arquivo de código. Você também pode importar namespaces para o seu projeto usando o **referências** página no Designer de projeto (**meu projeto**).  
  
2.  Certifique-se de que o tipo que você identificou como a fonte da consulta é um tipo passível de consulta. Ou seja, um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Referências e a Instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Página Referências, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

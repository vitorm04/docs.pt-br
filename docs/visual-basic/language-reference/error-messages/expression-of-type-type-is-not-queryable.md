---
title: "Expressão do tipo &lt;tipo&gt; não é questionável | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
dev_langs:
- VB
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1e7e1e2652cf730ef6d14b0579d8a3ee3de67fbb
ms.lasthandoff: 03/13/2017

---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>Expressão do tipo &lt;tipo&gt; não é questionável
Expressão do tipo \<tipo > não é questionável. Verifique se que você não está faltando uma importação de referência e/ou namespace do assembly para o provedor LINQ.  
  
 Queryable tipos são definidos no <xref:System.Linq>, <xref:System.Data.Linq>, e <xref:System.Xml.Linq>namespaces.</xref:System.Xml.Linq> </xref:System.Data.Linq> </xref:System.Linq> Você deve importar um ou mais desses espaços para nome para executar consultas LINQ.  
  
 O <xref:System.Linq>espaço para nome permite consulta objetos, como coleções e matrizes usando LINQ.</xref:System.Linq>  
  
 O <xref:System.Data.Linq>namespace permite consultar conjuntos de dados ADO.NET e bancos de dados do SQL Server usando LINQ.</xref:System.Data.Linq>  
  
 O <xref:System.Xml.Linq>namespace permite que você XML consulta usando LINQ e para utilizar os recursos XML no Visual Basic.</xref:System.Xml.Linq>  
  
 **ID do erro:** BC36593  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Adicionar uma `Import` instrução para o <xref:System.Linq>, <xref:System.Data.Linq>, ou <xref:System.Xml.Linq>espaço para nome para o arquivo de código.</xref:System.Xml.Linq> </xref:System.Data.Linq> </xref:System.Linq> Você também pode importar namespaces para o seu projeto usando o **referências** página do Project Designer (**meu projeto**).  
  
2.  Certifique-se de que o tipo que você tenha identificado como a fonte da consulta é um tipo que pode ser consultado. Ou seja, um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq></xref:System.Linq>   
 <xref:System.Data.Linq></xref:System.Data.Linq>   
 <xref:System.Xml.Linq>   
 [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Página Referências, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)

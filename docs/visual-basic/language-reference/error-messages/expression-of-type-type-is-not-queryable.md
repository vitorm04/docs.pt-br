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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84563c7339ffe7415017280d74a13d6501236da5
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="f2d16-102">Expressão do tipo &lt;tipo&gt; não é questionável</span><span class="sxs-lookup"><span data-stu-id="f2d16-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="f2d16-103">Expressão do tipo \<tipo > não é questionável.</span><span class="sxs-lookup"><span data-stu-id="f2d16-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="f2d16-104">Verifique se que você não está faltando uma importação de referência e/ou namespace do assembly para o provedor LINQ.</span><span class="sxs-lookup"><span data-stu-id="f2d16-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="f2d16-105">Queryable tipos são definidos no <xref:System.Linq>, <xref:System.Data.Linq>, e <xref:System.Xml.Linq>namespaces.</xref:System.Xml.Linq> </xref:System.Data.Linq> </xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="f2d16-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="f2d16-106">Você deve importar um ou mais desses espaços para nome para executar consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="f2d16-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="f2d16-107">O <xref:System.Linq>espaço para nome permite consulta objetos, como coleções e matrizes usando LINQ.</xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="f2d16-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="f2d16-108">O <xref:System.Data.Linq>namespace permite consultar conjuntos de dados ADO.NET e bancos de dados do SQL Server usando LINQ.</xref:System.Data.Linq></span><span class="sxs-lookup"><span data-stu-id="f2d16-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="f2d16-109">O <xref:System.Xml.Linq>namespace permite que você XML consulta usando LINQ e para utilizar os recursos XML no Visual Basic.</xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="f2d16-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="f2d16-110">**ID do erro:** BC36593</span><span class="sxs-lookup"><span data-stu-id="f2d16-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f2d16-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f2d16-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="f2d16-112">Adicionar uma `Import` instrução para o <xref:System.Linq>, <xref:System.Data.Linq>, ou <xref:System.Xml.Linq>espaço para nome para o arquivo de código.</xref:System.Xml.Linq> </xref:System.Data.Linq> </xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="f2d16-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="f2d16-113">Você também pode importar namespaces para o seu projeto usando o **referências** página do Project Designer (**meu projeto**).</span><span class="sxs-lookup"><span data-stu-id="f2d16-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="f2d16-114">Certifique-se de que o tipo que você tenha identificado como a fonte da consulta é um tipo que pode ser consultado.</span><span class="sxs-lookup"><span data-stu-id="f2d16-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="f2d16-115">Ou seja, um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="f2d16-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d16-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2d16-116">See Also</span></span>  
 <span data-ttu-id="f2d16-117"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="f2d16-117"><xref:System.Linq></span></span>   
 <span data-ttu-id="f2d16-118"><xref:System.Data.Linq></xref:System.Data.Linq></span><span class="sxs-lookup"><span data-stu-id="f2d16-118"><xref:System.Data.Linq></span></span>   
 <span data-ttu-id="f2d16-119"><xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="f2d16-119"><xref:System.Xml.Linq></span></span>   
<span data-ttu-id="f2d16-120"> [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="f2d16-120"> [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="f2d16-121"> [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="f2d16-121"> [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="f2d16-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="f2d16-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="f2d16-123"> [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f2d16-123"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="f2d16-124"> [Instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="f2d16-124"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="f2d16-125"> [Página Referências, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="f2d16-125"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>

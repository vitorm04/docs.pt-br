---
title: A expressão do tipo &lt;tipo&gt; não é passível de consulta
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 9d333abda5e303f8fab6d1f707df7ac77d8e03ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589003"
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="72356-102">A expressão do tipo &lt;tipo&gt; não é passível de consulta</span><span class="sxs-lookup"><span data-stu-id="72356-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="72356-103">A expressão do tipo \<tipo > não é passível de consulta.</span><span class="sxs-lookup"><span data-stu-id="72356-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="72356-104">Certifique-se de que não está faltando uma importação de referência e/ou namespace do assembly para o provedor LINQ.</span><span class="sxs-lookup"><span data-stu-id="72356-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="72356-105">Queryable tipos são definidos no <xref:System.Linq>, <xref:System.Data.Linq>, e <xref:System.Xml.Linq> namespaces.</span><span class="sxs-lookup"><span data-stu-id="72356-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="72356-106">Você deve importar um ou mais desses namespaces para executar consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="72356-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="72356-107">O <xref:System.Linq> namespace permite consulta objetos, como coleções e matrizes usando LINQ.</span><span class="sxs-lookup"><span data-stu-id="72356-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="72356-108">O <xref:System.Data.Linq> namespace permite que você consultar conjuntos de dados ADO.NET e bancos de dados do SQL Server usando LINQ.</span><span class="sxs-lookup"><span data-stu-id="72356-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="72356-109">O <xref:System.Xml.Linq> namespace permite que você XML consulta usando LINQ e para usar os recursos de XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72356-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="72356-110">**ID do erro:** BC36593</span><span class="sxs-lookup"><span data-stu-id="72356-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="72356-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="72356-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="72356-112">Adicionar uma `Import` instrução para o <xref:System.Linq>, <xref:System.Data.Linq>, ou <xref:System.Xml.Linq> namespace ao seu arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="72356-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="72356-113">Você também pode importar namespaces para o seu projeto usando o **referências** página no Designer de projeto (**meu projeto**).</span><span class="sxs-lookup"><span data-stu-id="72356-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="72356-114">Certifique-se de que o tipo que você identificou como a fonte da consulta é um tipo passível de consulta.</span><span class="sxs-lookup"><span data-stu-id="72356-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="72356-115">Ou seja, um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="72356-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72356-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72356-116">See Also</span></span>  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="72356-117">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72356-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="72356-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="72356-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="72356-119">XML</span><span class="sxs-lookup"><span data-stu-id="72356-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="72356-120">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="72356-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="72356-121">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="72356-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="72356-122">Página Referências, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72356-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

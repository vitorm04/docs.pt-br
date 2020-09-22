---
title: A expressão do tipo <type> não pode ser consultada
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 78b47601bf0a013d079f638f6dac27511e01aec4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874210"
---
# <a name="expression-of-type-type-is-not-queryable"></a><span data-ttu-id="d055e-102">A expressão do tipo \<type> não pode ser consultada</span><span class="sxs-lookup"><span data-stu-id="d055e-102">Expression of type \<type> is not queryable</span></span>

<span data-ttu-id="d055e-103">A expressão do tipo \<type> não é passível de consulta.</span><span class="sxs-lookup"><span data-stu-id="d055e-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="d055e-104">Verifique se você não tem uma referência de assembly e/ou uma importação de namespace para o provedor LINQ.</span><span class="sxs-lookup"><span data-stu-id="d055e-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="d055e-105">Os tipos consultáveis são definidos <xref:System.Linq> nos <xref:System.Data.Linq> <xref:System.Xml.Linq> namespaces, e.</span><span class="sxs-lookup"><span data-stu-id="d055e-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="d055e-106">Você deve importar um ou mais desses namespaces para executar consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="d055e-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="d055e-107">O <xref:System.Linq> namespace permite que você consulte objetos como coleções e matrizes usando LINQ.</span><span class="sxs-lookup"><span data-stu-id="d055e-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="d055e-108">O <xref:System.Data.Linq> namespace permite que você consulte conjuntos de dados do ADO.net e SQL Server bancos de dados usando o LINQ.</span><span class="sxs-lookup"><span data-stu-id="d055e-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="d055e-109">O <xref:System.Xml.Linq> namespace permite que você consulte XML usando LINQ e use recursos XML no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d055e-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="d055e-110">**ID do erro:** BC36593</span><span class="sxs-lookup"><span data-stu-id="d055e-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d055e-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d055e-111">To correct this error</span></span>  
  
1. <span data-ttu-id="d055e-112">Adicione uma `Import` instrução para o <xref:System.Linq> <xref:System.Data.Linq> namespace, ou <xref:System.Xml.Linq> ao seu arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="d055e-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="d055e-113">Você também pode importar namespaces para seu projeto usando a página **referências** do designer de projeto (**meu projeto**).</span><span class="sxs-lookup"><span data-stu-id="d055e-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2. <span data-ttu-id="d055e-114">Certifique-se de que o tipo que você identificou como a origem da consulta é um tipo consultável.</span><span class="sxs-lookup"><span data-stu-id="d055e-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="d055e-115">Ou seja, um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="d055e-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d055e-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="d055e-116">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="d055e-117">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d055e-117">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d055e-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="d055e-118">LINQ</span></span>](../../programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="d055e-119">XML</span><span class="sxs-lookup"><span data-stu-id="d055e-119">XML</span></span>](../../programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="d055e-120">Referências e a instrução Imports</span><span class="sxs-lookup"><span data-stu-id="d055e-120">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="d055e-121">Instrução Imports (tipo e namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="d055e-121">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="d055e-122">Página Referências, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d055e-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)

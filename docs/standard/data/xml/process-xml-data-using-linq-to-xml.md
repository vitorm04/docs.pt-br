---
title: Dados XML do processo usando LINQ to XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4e8e4a826fda20a39576ca78259bb7b389bbf75
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424443"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="35171-102">Dados XML do processo usando LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="35171-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="35171-103">LINQ to XML é o novo modelo no .NET Framework versão 3.5 para processar dados XML.</span><span class="sxs-lookup"><span data-stu-id="35171-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="35171-104">LINQ to XML permite que os desenvolvedores de tudo o que esperariam com dados XML: consultando, modificando, criando, salvar, e serialização documentos XML.</span><span class="sxs-lookup"><span data-stu-id="35171-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="35171-105">A mentira real das vantagens dos recursos de consulta e de design.</span><span class="sxs-lookup"><span data-stu-id="35171-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="35171-106">As consultas em LINQ to XML são sucintos e expressivos, usando a sintaxe mais semelhante ao SQL que para o XPath ou XQuery.</span><span class="sxs-lookup"><span data-stu-id="35171-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="35171-107">Porque os resultados da consulta podem ser retornados como coleções de elementos ou atributos e podem ser usados como parâmetros para objetos de XElement, as árvores XML podem ser facilmente transformadas de uma forma para outra.</span><span class="sxs-lookup"><span data-stu-id="35171-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="35171-108">LINQ to XML aproveita a tecnologia language-integrated de consulta (LINQ) no .NET Framework versão 3.5.</span><span class="sxs-lookup"><span data-stu-id="35171-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="35171-109">LINQ estende a sintaxe de linguagem C# e Visual Basic para fornecer recursos poderosos de consulta que podem ser estendidos potencialmente qualquer armazenamento de dados.</span><span class="sxs-lookup"><span data-stu-id="35171-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="35171-110">Para obter uma discussão detalhada sobre o uso, confira [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) e [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="35171-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="35171-111">Para obter uma visão geral da estrutura da LINQ, confira [LINQ (consulta integrada à linguagem) – C#](../../../csharp/programming-guide/concepts/linq/index.md) ou [LINQ (consulta integrada à linguagem) – Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="35171-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35171-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35171-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="35171-113">LINQ to XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="35171-113">LINQ to XML vs. DOM (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="35171-114">LINQ to XML vs. DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35171-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="35171-115">LINQ to XML vs. outras tecnologias XML (C#)</span><span class="sxs-lookup"><span data-stu-id="35171-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- [<span data-ttu-id="35171-116">LINQ to XML vs. outras tecnologias XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35171-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)

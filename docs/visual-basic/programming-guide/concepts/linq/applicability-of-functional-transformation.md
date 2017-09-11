---
title: "Aplicabilidade de transformação funcional (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 45e83c86b2cfd7bceef57dbf354e29cc35c56051
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="applicability-of-functional-transformation-visual-basic"></a><span data-ttu-id="8c222-102">Aplicabilidade de transformação funcional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c222-102">Applicability of Functional Transformation (Visual Basic)</span></span>
<span data-ttu-id="8c222-103">Transformações e puras são aplicáveis em uma variedade de situações.</span><span class="sxs-lookup"><span data-stu-id="8c222-103">Pure functional transformations are applicable in a wide variety of situations.</span></span>  
  
 <span data-ttu-id="8c222-104">A abordagem funcional de transformação é mais idealmente consultando e manipulando dados; estruturados portanto couber bem com as tecnologias LINQ.</span><span class="sxs-lookup"><span data-stu-id="8c222-104">The functional transformation approach is ideally suited for querying and manipulating structured data; therefore it fits well with LINQ technologies.</span></span> <span data-ttu-id="8c222-105">No entanto, a transformação funcional tem uma aplicabilidade muito maior do que o uso com LINQ.</span><span class="sxs-lookup"><span data-stu-id="8c222-105">However, functional transformation has a much wider applicability than use with LINQ.</span></span> <span data-ttu-id="8c222-106">Alguns processam onde o foco principal está em transformar dados de um formulário para outro provavelmente deve ser considerado como um candidato para a transformação funcional.</span><span class="sxs-lookup"><span data-stu-id="8c222-106">Any process where the main focus is on transforming data from one form to another should probably be considered as a candidate for functional transformation.</span></span>  
  
 <span data-ttu-id="8c222-107">Essa abordagem é aplicável a muitos problemas que não podem parecer à primeira vista para ser um candidato.</span><span class="sxs-lookup"><span data-stu-id="8c222-107">This approach is applicable to many problems that might not appear at first glance to be a candidate.</span></span> <span data-ttu-id="8c222-108">Usado em conjunto ou separadamente com LINQ, a transformação funcional deve ser considerada para as seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="8c222-108">Used in conjunction with or separately from LINQ, functional transformation should be considered for the following areas:</span></span>  
  
-   <span data-ttu-id="8c222-109">Documentos com base em XML.</span><span class="sxs-lookup"><span data-stu-id="8c222-109">XML-based documents.</span></span> <span data-ttu-id="8c222-110">Os dados bem formado do dialeto de XML podem facilmente ser manipulados pela transformação funcional.</span><span class="sxs-lookup"><span data-stu-id="8c222-110">Well-formed data of any XML dialect can be easily manipulated through functional transformation.</span></span> <span data-ttu-id="8c222-111">Para obter mais informações, consulte [funcional transformação de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8c222-111">For more information, see [Functional Transformation of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md).</span></span>  
  
-   <span data-ttu-id="8c222-112">Outros formatos de arquivo estruturados.</span><span class="sxs-lookup"><span data-stu-id="8c222-112">Other structured file formats.</span></span> <span data-ttu-id="8c222-113">De Windows.ini arquivos aos documentos de texto sem formatação, a maioria dos arquivos têm qualquer estrutura que se empresta a análise e a transformação.</span><span class="sxs-lookup"><span data-stu-id="8c222-113">From Windows.ini files to plain text documents, most files have some structure that lends itself to analysis and transformation.</span></span>  
  
-   <span data-ttu-id="8c222-114">Os protocolos de streaming de dados.</span><span class="sxs-lookup"><span data-stu-id="8c222-114">Data streaming protocols.</span></span> <span data-ttu-id="8c222-115">Os dados de codificação e nos dados de decodificação dos protocolos de comunicação geralmente podem ser representados por um funcional simples tornam-se.</span><span class="sxs-lookup"><span data-stu-id="8c222-115">Encoding data into and decoding data from communication protocols can often be represented by a simple functional transform.</span></span>  
  
-   <span data-ttu-id="8c222-116">Dados de RDBMS e de OODBMS.</span><span class="sxs-lookup"><span data-stu-id="8c222-116">RDBMS and OODBMS data.</span></span> <span data-ttu-id="8c222-117">Os bases de dados relacionais e orientados a objeto, assim como XML, são estruturados fontes de dados amplamente usadas.</span><span class="sxs-lookup"><span data-stu-id="8c222-117">Relational and object-oriented databases, just like XML, are widely-used structured data sources.</span></span>  
  
-   <span data-ttu-id="8c222-118">Matemático, estatística, e soluções de ciência.</span><span class="sxs-lookup"><span data-stu-id="8c222-118">Mathematic, statistic, and science solutions.</span></span> <span data-ttu-id="8c222-119">Esses campos tendem a manipular grandes conjuntos de dados para ajudar o usuário em visualizar, em estimar, ou realmente em resolver problemas não triviais.</span><span class="sxs-lookup"><span data-stu-id="8c222-119">These fields tend to manipulate large data sets to assist the user in visualizing, estimating, or actually solving non-trivial problems.</span></span>  
  
 <span data-ttu-id="8c222-120">Conforme descrito em [refatoração em funções puras (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md), usar funções puras é um exemplo de programação funcional.</span><span class="sxs-lookup"><span data-stu-id="8c222-120">As described in [Refactoring Into Pure Functions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md), using pure functions is an example of functional programming.</span></span> <span data-ttu-id="8c222-121">Em adicional a seus benefícios imediatos, usar funções puras fornece a experiência valiosa no pensamento sobre problemas de uma perspectiva funcional de transformação.</span><span class="sxs-lookup"><span data-stu-id="8c222-121">In additional to their immediate benefits, using pure functions provides valuable experience in thinking about problems from a functional transformation perspective.</span></span> <span data-ttu-id="8c222-122">Essa abordagem pode também ter o impacto principal no design do programa e da classe.</span><span class="sxs-lookup"><span data-stu-id="8c222-122">This approach can also have major impact on program and class design.</span></span> <span data-ttu-id="8c222-123">Isso é especialmente verdadeiro quando um problema se empresta a uma solução de transformação de dados como descrito acima.</span><span class="sxs-lookup"><span data-stu-id="8c222-123">This is especially true when a problem lends itself to a data transformation solution as described above.</span></span>  
  
 <span data-ttu-id="8c222-124">Embora eles sejam além do escopo deste tutorial, os projetos que são influenciados pela perspectiva funcional de transformação tendem a centralizar sobre processam mais do que em objetos como atores, e a solução resultante tendem a ser implementados como série de transformações em grande escala, em vez de alterações de estado individuais de objeto.</span><span class="sxs-lookup"><span data-stu-id="8c222-124">Although they are beyond the scope of this tutorial, designs that are influenced by the functional transformation perspective tend to center on processes more than on objects as actors, and the resulting solution tends to be implemented as series of large-scale transformations, rather than individual object state changes.</span></span>  
  
 <span data-ttu-id="8c222-125">Novamente, lembre-se de que o Visual Basic suporta abordagens imperativas e funcionais, portanto o melhor design para o seu aplicativo pode inserir os elementos de ambos.</span><span class="sxs-lookup"><span data-stu-id="8c222-125">Again, remember that Visual Basic supports both imperative and functional approaches, so the best design for your application might incorporate elements of both.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c222-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c222-126">See Also</span></span>  
 <span data-ttu-id="8c222-127">[Introdução às transformações e puras (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="8c222-127">[Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span></span>  
<span data-ttu-id="8c222-128"> [Transformação funcional XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md) </span><span class="sxs-lookup"><span data-stu-id="8c222-128"> [Functional Transformation of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md) </span></span>  
<span data-ttu-id="8c222-129"> [Refatoração em funções puras (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)</span><span class="sxs-lookup"><span data-stu-id="8c222-129"> [Refactoring Into Pure Functions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)</span></span>

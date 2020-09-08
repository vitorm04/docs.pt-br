---
title: Comparação entre XPath e LINQ to XML-LINQ to XML
description: As consultas XPath e LINQ to XML podem consultar árvores XML. Este artigo compara as duas opções e localiza LINQ to XML consultas para serem, em todo, a opção mais potente, versátil, mais rápida, segura e mais conveniente.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: b98651ffd7e0df0057164f40bedbc43d654d8c81
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551994"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="ce0df-104">Comparação XPath e de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="ce0df-104">Comparison of XPath and LINQ to XML</span></span>

<span data-ttu-id="ce0df-105">XPath e LINQ to XML são semelhantes de algumas maneiras.</span><span class="sxs-lookup"><span data-stu-id="ce0df-105">XPath and LINQ to XML are similar in some ways.</span></span> <span data-ttu-id="ce0df-106">Ambos podem ser usados para ver uma árvore XML, retornando resultados como uma coleção de elementos, uma coleção de atributos, uma coleção de nós, ou o valor de um elemento ou de um atributo.</span><span class="sxs-lookup"><span data-stu-id="ce0df-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="ce0df-107">No entanto, há diferenças significativas entre as duas opções.</span><span class="sxs-lookup"><span data-stu-id="ce0df-107">However, there are significant differences between the two options.</span></span>

## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="ce0df-108">Diferenças entre XPath e LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="ce0df-108">Differences between XPath and LINQ to XML</span></span>

<span data-ttu-id="ce0df-109">O XPath não permite a projeção de novos tipos.</span><span class="sxs-lookup"><span data-stu-id="ce0df-109">XPath doesn't allow projection of new types.</span></span> <span data-ttu-id="ce0df-110">Somente é possível retornar coleções de nós de árvore, enquanto o LINQ to XML pode executar uma consulta e projetar um grafo de objeto ou uma árvore XML em uma nova forma.</span><span class="sxs-lookup"><span data-stu-id="ce0df-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="ce0df-111">LINQ to XML consultas podem fazer muito mais do que expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="ce0df-111">LINQ to XML queries can do much more than XPath expressions.</span></span>

<span data-ttu-id="ce0df-112">As expressões XPath existem no isolamento dentro de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ce0df-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="ce0df-113">O compilador C# não pode ajudar a analisar a expressão XPath no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ce0df-113">The C# compiler can't help parse the XPath expression at compile time.</span></span> <span data-ttu-id="ce0df-114">Por outro lado, as consultas do LINQ to XML são analisadas e compiladas pelo compilador do C#.</span><span class="sxs-lookup"><span data-stu-id="ce0df-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="ce0df-115">O compilador pode capturar muitos erros de consulta.</span><span class="sxs-lookup"><span data-stu-id="ce0df-115">The compiler can catch many query errors.</span></span>

<span data-ttu-id="ce0df-116">Os resultados XPath não são fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="ce0df-116">XPath results aren't strongly typed.</span></span> <span data-ttu-id="ce0df-117">Em várias circunstâncias, o resultado da avaliação de uma expressão XPath é um objeto, e cabe ao desenvolvedor determinar o tipo adequado e converter o resultado conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="ce0df-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it's up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="ce0df-118">Por outro lado, as projeções de uma consulta do LINQ to XML são fortemente tipadas.</span><span class="sxs-lookup"><span data-stu-id="ce0df-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>

## <a name="result-ordering"></a><span data-ttu-id="ce0df-119">Ordenação de resultados</span><span class="sxs-lookup"><span data-stu-id="ce0df-119">Result ordering</span></span>

<span data-ttu-id="ce0df-120">A recomendação do XPath 1,0 afirma que uma coleção que é o resultado da avaliação de uma expressão XPath não é ordenada.</span><span class="sxs-lookup"><span data-stu-id="ce0df-120">The XPath 1.0 Recommendation states that a collection that's the result of evaluating an XPath expression is unordered.</span></span>

<span data-ttu-id="ce0df-121">Entretanto, ao fazer iterações por uma coleção retornada por um método do eixo XPath do LINQ to XML, os nós na coleção são retornados na ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="ce0df-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="ce0df-122">Este é o caso mesmo quando acessando os eixos XPath onde os predicados são expressos em termos de ordem inversa de documento, como `preceding` e `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="ce0df-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>

<span data-ttu-id="ce0df-123">Por outro lado, a maioria dos eixos de LINQ to XML retorna coleções na ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="ce0df-123">By contrast, most of the LINQ to XML axes return collections in document order.</span></span> <span data-ttu-id="ce0df-124">No entanto, dois deles, <xref:System.Xml.Linq.XNode.Ancestors%2A> e <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> , retornam coleções na ordem inversa do documento.</span><span class="sxs-lookup"><span data-stu-id="ce0df-124">However, two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="ce0df-125">A tabela a seguir enumera os eixos e indica a ordem da coleção para cada um:</span><span class="sxs-lookup"><span data-stu-id="ce0df-125">The following table enumerates the axes, and indicates the collection order for each:</span></span>

|<span data-ttu-id="ce0df-126">O eixo LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="ce0df-126">LINQ to XML axis</span></span>|<span data-ttu-id="ce0df-127">Ordenando</span><span class="sxs-lookup"><span data-stu-id="ce0df-127">Ordering</span></span>|
|----------------------|--------------|
|<span data-ttu-id="ce0df-128">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="ce0df-128">XContainer.DescendantNodes</span></span>|<span data-ttu-id="ce0df-129">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-129">Document order</span></span>|
|<span data-ttu-id="ce0df-130">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="ce0df-130">XContainer.Descendants</span></span>|<span data-ttu-id="ce0df-131">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-131">Document order</span></span>|
|<span data-ttu-id="ce0df-132">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="ce0df-132">XContainer.Elements</span></span>|<span data-ttu-id="ce0df-133">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-133">Document order</span></span>|
|<span data-ttu-id="ce0df-134">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="ce0df-134">XContainer.Nodes</span></span>|<span data-ttu-id="ce0df-135">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-135">Document order</span></span>|
|<span data-ttu-id="ce0df-136">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="ce0df-136">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="ce0df-137">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-137">Document order</span></span>|
|<span data-ttu-id="ce0df-138">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="ce0df-138">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="ce0df-139">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-139">Document order</span></span>|
|<span data-ttu-id="ce0df-140">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="ce0df-140">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="ce0df-141">Ordem inversa de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-141">Reverse document order</span></span>|
|<span data-ttu-id="ce0df-142">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="ce0df-142">XElement.Attributes</span></span>|<span data-ttu-id="ce0df-143">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-143">Document order</span></span>|
|<span data-ttu-id="ce0df-144">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="ce0df-144">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="ce0df-145">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-145">Document order</span></span>|
|<span data-ttu-id="ce0df-146">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="ce0df-146">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="ce0df-147">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-147">Document order</span></span>|
|<span data-ttu-id="ce0df-148">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="ce0df-148">XNode.Ancestors</span></span>|<span data-ttu-id="ce0df-149">Ordem inversa de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-149">Reverse document order</span></span>|
|<span data-ttu-id="ce0df-150">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="ce0df-150">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="ce0df-151">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-151">Document order</span></span>|
|<span data-ttu-id="ce0df-152">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="ce0df-152">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="ce0df-153">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-153">Document order</span></span>|
|<span data-ttu-id="ce0df-154">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="ce0df-154">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="ce0df-155">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-155">Document order</span></span>|
|<span data-ttu-id="ce0df-156">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="ce0df-156">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="ce0df-157">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="ce0df-157">Document order</span></span>|

## <a name="positional-predicates"></a><span data-ttu-id="ce0df-158">Predicados posicionais</span><span class="sxs-lookup"><span data-stu-id="ce0df-158">Positional predicates</span></span>

<span data-ttu-id="ce0df-159">Dentro de uma expressão XPath, os predicados de posição são expressos em termos de ordem de documentos para muitos eixos, mas são expressos em ordem inversa de documentos para eixos inversos.</span><span class="sxs-lookup"><span data-stu-id="ce0df-159">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes.</span></span> <span data-ttu-id="ce0df-160">Os eixos inversos são: `preceding` , `preceding-sibling` , `ancestor` e `ancestor-or-self` .</span><span class="sxs-lookup"><span data-stu-id="ce0df-160">The reverse axes are: `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="ce0df-161">Por exemplo, a expressão XPath `preceding-sibling::*[1]` retorna imediatamente antes o irmão.</span><span class="sxs-lookup"><span data-stu-id="ce0df-161">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="ce0df-162">Este é o caso mesmo que o conjunto de resultados final é apresentado na ordem de documento.</span><span class="sxs-lookup"><span data-stu-id="ce0df-162">This is the case even though the final result set is presented in document order.</span></span>

<span data-ttu-id="ce0df-163">Por outro lado, todos os predicados posicionais em LINQ to XML sempre são expressos em termos de pedido do eixo.</span><span class="sxs-lookup"><span data-stu-id="ce0df-163">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="ce0df-164">Por exemplo, `anElement.ElementsBeforeSelf().ElementAt(0)` retorna o primeiro elemento filho do pai do elemento consultado, não irmão anterior imediato.</span><span class="sxs-lookup"><span data-stu-id="ce0df-164">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="ce0df-165">Outro exemplo: `anElement.Ancestors().ElementAt(0)` retorna o elemento pai.</span><span class="sxs-lookup"><span data-stu-id="ce0df-165">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>

<span data-ttu-id="ce0df-166">Se você desejar localizar imediatamente o elemento precedente no LINQ to XML, escreva a expressão a seguir:</span><span class="sxs-lookup"><span data-stu-id="ce0df-166">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>

```csharp
ElementsBeforeSelf().Last()
```

```vb
ElementsBeforeSelf().Last()
```

## <a name="performance-differences"></a><span data-ttu-id="ce0df-167">Diferenças de desempenho</span><span class="sxs-lookup"><span data-stu-id="ce0df-167">Performance differences</span></span>

<span data-ttu-id="ce0df-168">As consultas XPath que usam a funcionalidade XPath no LINQ to XML serão mais lentas do que LINQ to XML consultas.</span><span class="sxs-lookup"><span data-stu-id="ce0df-168">XPath queries that use the XPath functionality in LINQ to XML will be slower than LINQ to XML queries.</span></span>

## <a name="comparison-of-composition"></a><span data-ttu-id="ce0df-169">Comparação de composição</span><span class="sxs-lookup"><span data-stu-id="ce0df-169">Comparison of composition</span></span>

<span data-ttu-id="ce0df-170">A composição de uma consulta de LINQ to XML é semelhante à composição de uma expressão XPath, mas a sintaxe é muito diferente.</span><span class="sxs-lookup"><span data-stu-id="ce0df-170">Composition of a LINQ to XML query is similar to composition of an XPath expression, but the syntax is very different.</span></span>

<span data-ttu-id="ce0df-171">Por exemplo, se você tiver um elemento em uma variável chamada `customers` e quiser encontrar um elemento neto chamado `CompanyName` em todos os elementos filho chamados `Customer` , escreveria essa expressão XPath:</span><span class="sxs-lookup"><span data-stu-id="ce0df-171">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write this XPath expression:</span></span>

```csharp
customers.XPathSelectElements("./Customer/CompanyName")
```

```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

<span data-ttu-id="ce0df-172">A consulta do LINQ to XML equivalente é:</span><span class="sxs-lookup"><span data-stu-id="ce0df-172">The equivalent LINQ to XML query is:</span></span>

```csharp
customers.Elements("Customer").Elements("CompanyName")
```

```vb
customers.Elements("Customer").Elements("CompanyName")
```

<span data-ttu-id="ce0df-173">Há paralelas semelhantes para cada um dos eixos XPath.</span><span class="sxs-lookup"><span data-stu-id="ce0df-173">There are similar parallels for each of the XPath axes.</span></span>

|<span data-ttu-id="ce0df-174">O eixo XPath</span><span class="sxs-lookup"><span data-stu-id="ce0df-174">XPath axis</span></span>|<span data-ttu-id="ce0df-175">O eixo LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="ce0df-175">LINQ to XML axis</span></span>|
|----------------|----------------------|
|<span data-ttu-id="ce0df-176">o eixo filho (padrão)</span><span class="sxs-lookup"><span data-stu-id="ce0df-176">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ce0df-177">Pai (.).</span><span class="sxs-lookup"><span data-stu-id="ce0df-177">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ce0df-178">o eixo de atributo (@)</span><span class="sxs-lookup"><span data-stu-id="ce0df-178">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="ce0df-179">ou</span><span class="sxs-lookup"><span data-stu-id="ce0df-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ce0df-180">o eixo de ancestral</span><span class="sxs-lookup"><span data-stu-id="ce0df-180">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ce0df-181">o eixo de antepassado-ou- auto</span><span class="sxs-lookup"><span data-stu-id="ce0df-181">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ce0df-182">o eixo descendente (/)</span><span class="sxs-lookup"><span data-stu-id="ce0df-182">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="ce0df-183">ou</span><span class="sxs-lookup"><span data-stu-id="ce0df-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ce0df-184">descendente-ou-auto</span><span class="sxs-lookup"><span data-stu-id="ce0df-184">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="ce0df-185">ou</span><span class="sxs-lookup"><span data-stu-id="ce0df-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ce0df-186">seguir-irmão</span><span class="sxs-lookup"><span data-stu-id="ce0df-186">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="ce0df-187">ou</span><span class="sxs-lookup"><span data-stu-id="ce0df-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ce0df-188">acima-irmão</span><span class="sxs-lookup"><span data-stu-id="ce0df-188">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="ce0df-189">ou</span><span class="sxs-lookup"><span data-stu-id="ce0df-189">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="ce0df-190">após</span><span class="sxs-lookup"><span data-stu-id="ce0df-190">following</span></span>|<span data-ttu-id="ce0df-191">Nenhum equivalente direto.</span><span class="sxs-lookup"><span data-stu-id="ce0df-191">No direct equivalent.</span></span>|
|<span data-ttu-id="ce0df-192">precedência</span><span class="sxs-lookup"><span data-stu-id="ce0df-192">preceding</span></span>|<span data-ttu-id="ce0df-193">Nenhum equivalente direto.</span><span class="sxs-lookup"><span data-stu-id="ce0df-193">No direct equivalent.</span></span>|

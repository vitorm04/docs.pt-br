---
title: Comparação XPath e de LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: afd8701c6a37fd981d9fc23b57904da80eabf86e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583150"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="0f2d4-102">Comparação XPath e de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="0f2d4-102">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="0f2d4-103">O XPath e o LINQ to XML fornecem alguma funcionalidade semelhante.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-103">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="0f2d4-104">Ambos podem ser usados para ver uma árvore XML, retornando resultados como uma coleção de elementos, uma coleção de atributos, uma coleção de nós, ou o valor de um elemento ou de um atributo.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-104">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="0f2d4-105">No entanto, também há algumas diferenças.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-105">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="0f2d4-106">Diferenças entre o XPath e o LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="0f2d4-106">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="0f2d4-107">O XPath não permite a projeção de novos tipos.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-107">XPath does not allow projection of new types.</span></span> <span data-ttu-id="0f2d4-108">Somente é possível retornar coleções de nós de árvore, enquanto o LINQ to XML pode executar uma consulta e projetar um grafo de objeto ou uma árvore XML em uma nova forma.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-108">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="0f2d4-109">Consultas do LINQ to XML abrangem muito mais funcionalidade e são muito mais avançadas do que expressões XPath.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-109">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="0f2d4-110">As expressões XPath existem no isolamento dentro de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-110">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="0f2d4-111">O compilador do C# não pode ajudar a analisar em tempo de compilação a expressão XPath.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-111">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="0f2d4-112">Por outro lado, as consultas do LINQ to XML são analisadas e compiladas pelo compilador do C#.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-112">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="0f2d4-113">O compilador pode capturar muitos erros de consulta.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-113">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="0f2d4-114">Os resultados XPath não são altamente digitados.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-114">XPath results are not strongly typed.</span></span> <span data-ttu-id="0f2d4-115">Em um número das circunstâncias, o resultado para avaliar uma expressão XPath é um objeto, e até o desenvolvedor para determinar o tipo apropriado e conforme necessário para converter o resultado.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-115">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="0f2d4-116">Por outro lado, as projeções de uma consulta do LINQ to XML são fortemente tipadas.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-116">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="0f2d4-117">Ordenação de resultado</span><span class="sxs-lookup"><span data-stu-id="0f2d4-117">Result Ordering</span></span>  
 <span data-ttu-id="0f2d4-118">O XPath 1,0 estados de recomendação que uma coleção que é o resultado de avaliar uma expressão XPath é não ordenada.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-118">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="0f2d4-119">Entretanto, ao fazer iterações por uma coleção retornada por um método do eixo XPath do LINQ to XML, os nós na coleção são retornados na ordem do documento.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-119">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="0f2d4-120">Este é o caso mesmo quando acessando os eixos XPath onde os predicados são expressos em termos de ordem inversa de documento, como `preceding` e `preceding-sibling`.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-120">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="0f2d4-121">Por outro lado, a maioria dos eixos do LINQ to XML retorna coleções na ordem de documento, mas por dois deles, <xref:System.Xml.Linq.XNode.Ancestors%2A> e <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, retornam coleções na ordem inversa do documento.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-121">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="0f2d4-122">A tabela a seguir enumera os eixos, e indica a ordem de coleção para cada:</span><span class="sxs-lookup"><span data-stu-id="0f2d4-122">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="0f2d4-123">O eixo LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="0f2d4-123">LINQ to XML axis</span></span>|<span data-ttu-id="0f2d4-124">Ordenando</span><span class="sxs-lookup"><span data-stu-id="0f2d4-124">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="0f2d4-125">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="0f2d4-125">XContainer.DescendantNodes</span></span>|<span data-ttu-id="0f2d4-126">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-126">Document order</span></span>|  
|<span data-ttu-id="0f2d4-127">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="0f2d4-127">XContainer.Descendants</span></span>|<span data-ttu-id="0f2d4-128">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-128">Document order</span></span>|  
|<span data-ttu-id="0f2d4-129">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="0f2d4-129">XContainer.Elements</span></span>|<span data-ttu-id="0f2d4-130">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-130">Document order</span></span>|  
|<span data-ttu-id="0f2d4-131">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="0f2d4-131">XContainer.Nodes</span></span>|<span data-ttu-id="0f2d4-132">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-132">Document order</span></span>|  
|<span data-ttu-id="0f2d4-133">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="0f2d4-133">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="0f2d4-134">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-134">Document order</span></span>|  
|<span data-ttu-id="0f2d4-135">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="0f2d4-135">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="0f2d4-136">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-136">Document order</span></span>|  
|<span data-ttu-id="0f2d4-137">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="0f2d4-137">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="0f2d4-138">Ordem inversa de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-138">Reverse document order</span></span>|  
|<span data-ttu-id="0f2d4-139">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="0f2d4-139">XElement.Attributes</span></span>|<span data-ttu-id="0f2d4-140">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-140">Document order</span></span>|  
|<span data-ttu-id="0f2d4-141">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="0f2d4-141">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="0f2d4-142">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-142">Document order</span></span>|  
|<span data-ttu-id="0f2d4-143">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="0f2d4-143">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="0f2d4-144">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-144">Document order</span></span>|  
|<span data-ttu-id="0f2d4-145">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="0f2d4-145">XNode.Ancestors</span></span>|<span data-ttu-id="0f2d4-146">Ordem inversa de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-146">Reverse document order</span></span>|  
|<span data-ttu-id="0f2d4-147">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="0f2d4-147">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="0f2d4-148">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-148">Document order</span></span>|  
|<span data-ttu-id="0f2d4-149">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="0f2d4-149">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="0f2d4-150">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-150">Document order</span></span>|  
|<span data-ttu-id="0f2d4-151">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="0f2d4-151">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="0f2d4-152">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-152">Document order</span></span>|  
|<span data-ttu-id="0f2d4-153">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="0f2d4-153">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="0f2d4-154">Ordem de documento</span><span class="sxs-lookup"><span data-stu-id="0f2d4-154">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="0f2d4-155">Predicados posicionais</span><span class="sxs-lookup"><span data-stu-id="0f2d4-155">Positional Predicates</span></span>  
 <span data-ttu-id="0f2d4-156">Em uma expressão XPath, os predicados posicionais são expressos em termos de pedido de documento para muitos eixos, mas expressos na ordem inversa de documento para os eixos invertidos, que são `preceding`, `preceding-sibling`, `ancestor`, e `ancestor-or-self`.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-156">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="0f2d4-157">Por exemplo, a expressão XPath `preceding-sibling::*[1]` retorna imediatamente antes o irmão.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-157">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="0f2d4-158">Este é o caso mesmo que o conjunto de resultados final é apresentado na ordem de documento.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-158">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="0f2d4-159">Por outro lado, todos os predicados posicionais em LINQ to XML sempre são expressos em termos de pedido do eixo.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-159">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="0f2d4-160">Por exemplo, `anElement.ElementsBeforeSelf().ElementAt(0)` retorna o primeiro elemento filho do pai do elemento consultado, não irmão anterior imediato.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-160">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="0f2d4-161">Outro exemplo: `anElement.Ancestors().ElementAt(0)` retorna o elemento pai.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-161">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="0f2d4-162">Se você desejar localizar imediatamente o elemento precedente no LINQ to XML, escreva a expressão a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f2d4-162">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="0f2d4-163">Diferenças de desempenho</span><span class="sxs-lookup"><span data-stu-id="0f2d4-163">Performance Differences</span></span>  
 <span data-ttu-id="0f2d4-164">As consultas XPath que usam a funcionalidade XPath no LINQ to XML não serão tão bem executadas como as consultas do LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-164">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="0f2d4-165">Comparação de composição</span><span class="sxs-lookup"><span data-stu-id="0f2d4-165">Comparison of Composition</span></span>  
 <span data-ttu-id="0f2d4-166">A composição de uma consulta do LINQ to XML é um pouco paralela à composição de uma expressão XPath, embora muito diferente na sintaxe.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-166">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="0f2d4-167">Por exemplo, se você tiver um elemento em uma variável chamada `customers`, e você desejar localizar um elemento de neto chamado `CompanyName` em todos os elementos filho chamados `Customer`, escreva uma expressão XPath como segue:</span><span class="sxs-lookup"><span data-stu-id="0f2d4-167">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="0f2d4-168">A consulta do LINQ to XML equivalente é:</span><span class="sxs-lookup"><span data-stu-id="0f2d4-168">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="0f2d4-169">Há paralelas semelhantes para cada um dos eixos XPath.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-169">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="0f2d4-170">O eixo XPath</span><span class="sxs-lookup"><span data-stu-id="0f2d4-170">XPath axis</span></span>|<span data-ttu-id="0f2d4-171">O eixo LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="0f2d4-171">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="0f2d4-172">o eixo filho (padrão)</span><span class="sxs-lookup"><span data-stu-id="0f2d4-172">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f2d4-173">Pai (.).</span><span class="sxs-lookup"><span data-stu-id="0f2d4-173">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f2d4-174">o eixo de atributo (@)</span><span class="sxs-lookup"><span data-stu-id="0f2d4-174">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="0f2d4-175">ou</span><span class="sxs-lookup"><span data-stu-id="0f2d4-175">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f2d4-176">o eixo de ancestral</span><span class="sxs-lookup"><span data-stu-id="0f2d4-176">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f2d4-177">o eixo de antepassado-ou- auto</span><span class="sxs-lookup"><span data-stu-id="0f2d4-177">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f2d4-178">o eixo descendente (/)</span><span class="sxs-lookup"><span data-stu-id="0f2d4-178">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="0f2d4-179">ou</span><span class="sxs-lookup"><span data-stu-id="0f2d4-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f2d4-180">descendente-ou-auto</span><span class="sxs-lookup"><span data-stu-id="0f2d4-180">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="0f2d4-181">ou</span><span class="sxs-lookup"><span data-stu-id="0f2d4-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f2d4-182">seguir-irmão</span><span class="sxs-lookup"><span data-stu-id="0f2d4-182">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="0f2d4-183">ou</span><span class="sxs-lookup"><span data-stu-id="0f2d4-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f2d4-184">acima-irmão</span><span class="sxs-lookup"><span data-stu-id="0f2d4-184">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="0f2d4-185">ou</span><span class="sxs-lookup"><span data-stu-id="0f2d4-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f2d4-186">após</span><span class="sxs-lookup"><span data-stu-id="0f2d4-186">following</span></span>|<span data-ttu-id="0f2d4-187">Nenhum equivalente direto.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-187">No direct equivalent.</span></span>|  
|<span data-ttu-id="0f2d4-188">precedência</span><span class="sxs-lookup"><span data-stu-id="0f2d4-188">preceding</span></span>|<span data-ttu-id="0f2d4-189">Nenhum equivalente direto.</span><span class="sxs-lookup"><span data-stu-id="0f2d4-189">No direct equivalent.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f2d4-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f2d4-190">See also</span></span>

- [<span data-ttu-id="0f2d4-191">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="0f2d4-191">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

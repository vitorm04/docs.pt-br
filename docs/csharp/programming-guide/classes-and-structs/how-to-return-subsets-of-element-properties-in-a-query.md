---
title: 'Como: retornar subconjuntos de propriedades de elementos em uma consulta – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 36e910328651cc4f91acdfb2d40edea56cde2a9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676478"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="e7e16-102">Como: retornar subconjuntos de propriedades de elementos em uma consulta (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e7e16-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="e7e16-103">Use um tipo anônimo em uma expressão de consulta quando essas duas condições se aplicarem:</span><span class="sxs-lookup"><span data-stu-id="e7e16-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="e7e16-104">Você deseja retornar apenas algumas das propriedades de cada elemento de origem.</span><span class="sxs-lookup"><span data-stu-id="e7e16-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="e7e16-105">Você não precisa armazenar os resultados da consulta fora do escopo do método em que a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="e7e16-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="e7e16-106">Se você deseja retornar apenas uma propriedade ou campo de cada elemento de origem, use somente o operador de ponto na cláusula `select`.</span><span class="sxs-lookup"><span data-stu-id="e7e16-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="e7e16-107">Por exemplo, para retornar somente a `ID` de cada `student`, escreva a cláusula `select` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e7e16-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="e7e16-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7e16-108">Example</span></span>  
 <span data-ttu-id="e7e16-109">O exemplo a seguir mostra como usar um tipo anônimo para retornar apenas um subconjunto das propriedades de cada elemento de origem que corresponda à condição especificada.</span><span class="sxs-lookup"><span data-stu-id="e7e16-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 <span data-ttu-id="e7e16-110">Observe que o tipo anônimo usa nomes do elemento de origem para suas propriedades, se nenhum nome for especificado.</span><span class="sxs-lookup"><span data-stu-id="e7e16-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="e7e16-111">Para fornecer novos nomes para as propriedades no tipo anônimo, escreva a instrução `select` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e7e16-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="e7e16-112">Se você tentar fazer isso no exemplo anterior, a instrução `Console.WriteLine` também deve ser alterada:</span><span class="sxs-lookup"><span data-stu-id="e7e16-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7e16-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e7e16-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="e7e16-114">Para executar esse código, copie e cole a classe em um projeto de aplicativo de console do Visual C# que foi criado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e7e16-114">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="e7e16-115">Por padrão, esse projeto é direcionado para a versão 3.5 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e ele terá uma referência ao System.Core.dll e uma diretriz `using` para System.Linq.</span><span class="sxs-lookup"><span data-stu-id="e7e16-115">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="e7e16-116">Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.</span><span class="sxs-lookup"><span data-stu-id="e7e16-116">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="e7e16-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7e16-117">See also</span></span>

- [<span data-ttu-id="e7e16-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e7e16-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e7e16-119">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="e7e16-119">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="e7e16-120">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="e7e16-120">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)

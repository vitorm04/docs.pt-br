---
title: Como retornar subconjuntos de propriedades de elementos em uma consulta - C# Guia de programação
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714866"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="80e13-102">Como retornar subconjuntos de propriedades de elemento em uma consulta (C# Guia de programação)</span><span class="sxs-lookup"><span data-stu-id="80e13-102">How to return subsets of element properties in a query (C# Programming Guide)</span></span>
<span data-ttu-id="80e13-103">Use um tipo anônimo em uma expressão de consulta quando essas duas condições se aplicarem:</span><span class="sxs-lookup"><span data-stu-id="80e13-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="80e13-104">Você deseja retornar apenas algumas das propriedades de cada elemento de origem.</span><span class="sxs-lookup"><span data-stu-id="80e13-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="80e13-105">Você não precisa armazenar os resultados da consulta fora do escopo do método em que a consulta é executada.</span><span class="sxs-lookup"><span data-stu-id="80e13-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="80e13-106">Se você deseja retornar apenas uma propriedade ou campo de cada elemento de origem, use somente o operador de ponto na cláusula `select`.</span><span class="sxs-lookup"><span data-stu-id="80e13-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="80e13-107">Por exemplo, para retornar somente a `ID` de cada `student`, escreva a cláusula `select` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="80e13-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="80e13-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80e13-108">Example</span></span>  
 <span data-ttu-id="80e13-109">O exemplo a seguir mostra como usar um tipo anônimo para retornar apenas um subconjunto das propriedades de cada elemento de origem que corresponda à condição especificada.</span><span class="sxs-lookup"><span data-stu-id="80e13-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="80e13-110">Observe que o tipo anônimo usa nomes do elemento de origem para suas propriedades, se nenhum nome for especificado.</span><span class="sxs-lookup"><span data-stu-id="80e13-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="80e13-111">Para fornecer novos nomes para as propriedades no tipo anônimo, escreva a instrução `select` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="80e13-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="80e13-112">Se você tentar fazer isso no exemplo anterior, a instrução `Console.WriteLine` também deve ser alterada:</span><span class="sxs-lookup"><span data-stu-id="80e13-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80e13-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="80e13-113">Compiling the Code</span></span>  
  
<span data-ttu-id="80e13-114">Para executar esse código, copie e cole a classe em um aplicativo de console em C# com uma diretiva `using` para System.Linq.</span><span class="sxs-lookup"><span data-stu-id="80e13-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="80e13-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="80e13-115">See also</span></span>

- [<span data-ttu-id="80e13-116">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="80e13-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="80e13-117">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="80e13-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="80e13-118">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="80e13-118">LINQ in C#</span></span>](../../linq/index.md)

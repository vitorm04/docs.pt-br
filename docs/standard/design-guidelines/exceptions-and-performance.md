---
title: Desempenho e exceções
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfffc2a1c0f607541194a7f51717d5bf8a8537f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575330"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="7fb67-102">Desempenho e exceções</span><span class="sxs-lookup"><span data-stu-id="7fb67-102">Exceptions and Performance</span></span>
<span data-ttu-id="7fb67-103">Uma preocupação comuns relacionada às exceções é que, se as exceções são usadas para código rotineiramente falha, o desempenho da implementação será inaceitável.</span><span class="sxs-lookup"><span data-stu-id="7fb67-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="7fb67-104">Isso é uma preocupação válida.</span><span class="sxs-lookup"><span data-stu-id="7fb67-104">This is a valid concern.</span></span> <span data-ttu-id="7fb67-105">Quando um membro lança uma exceção, o desempenho pode ser mais lentas ordens de magnitude.</span><span class="sxs-lookup"><span data-stu-id="7fb67-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="7fb67-106">No entanto, é possível atingir um bom desempenho ao estritamente aderindo às diretrizes de exceção que não é permitido usar códigos de erro.</span><span class="sxs-lookup"><span data-stu-id="7fb67-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="7fb67-107">Dois padrões descritos nesta seção sugerem maneiras de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="7fb67-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="7fb67-108">**X não** usar códigos de erro devido a questões que exceções podem afetar negativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="7fb67-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="7fb67-109">Para melhorar o desempenho, é possível usar o testador mal-intencionado padrão ou o padrão de análise Try, descrito nas próximas duas seções.</span><span class="sxs-lookup"><span data-stu-id="7fb67-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="7fb67-110">Testador mal-intencionado padrão</span><span class="sxs-lookup"><span data-stu-id="7fb67-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="7fb67-111">Às vezes, é possível melhorar o desempenho de um membro geradoras de exceções dividindo o membro em duas.</span><span class="sxs-lookup"><span data-stu-id="7fb67-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="7fb67-112">Vamos examinar a <xref:System.Collections.Generic.ICollection%601.Add%2A> método o <xref:System.Collections.Generic.ICollection%601> interface.</span><span class="sxs-lookup"><span data-stu-id="7fb67-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="7fb67-113">O método `Add` lança a coleção é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="7fb67-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="7fb67-114">Isso pode ser um problema de desempenho em cenários em que a chamada do método deve falhar com frequência.</span><span class="sxs-lookup"><span data-stu-id="7fb67-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="7fb67-115">Uma das maneiras de reduzir o problema é se a coleção é gravável antes de tentar adicionar um valor de teste.</span><span class="sxs-lookup"><span data-stu-id="7fb67-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="7fb67-116">O membro usado para testar uma condição, que, em nosso exemplo, é a propriedade `IsReadOnly`, é conhecido como o teste.</span><span class="sxs-lookup"><span data-stu-id="7fb67-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="7fb67-117">O membro usado para executar uma operação potencialmente sendo lançada, o `Add` método em nosso exemplo, é conhecido como o mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="7fb67-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="7fb67-118">**✓ CONSIDERE** o padrão de mal-intencionado Testador de membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.</span><span class="sxs-lookup"><span data-stu-id="7fb67-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="7fb67-119">Tente a análise padrão</span><span class="sxs-lookup"><span data-stu-id="7fb67-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="7fb67-120">Para desempenho extremamente sensíveis APIs, um padrão ainda mais rápido do que o padrão de testador mal-intencionado descrito na seção anterior deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="7fb67-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="7fb67-121">O padrão de chamadas para ajustar o nome do membro para fazer um teste bem definido caso uma parte da semântica de membros.</span><span class="sxs-lookup"><span data-stu-id="7fb67-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="7fb67-122">Por exemplo, <xref:System.DateTime> define um <xref:System.DateTime.Parse%2A> método que gera uma exceção se a análise de uma cadeia de caracteres falhar.</span><span class="sxs-lookup"><span data-stu-id="7fb67-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="7fb67-123">Ele também define correspondente <xref:System.DateTime.TryParse%2A> método que tenta analisar, mas retornará false se a análise for bem-sucedida e retorna o resultado de uma análise com êxito usando um `out` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7fb67-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="7fb67-124">Ao usar esse padrão, é importante definir a funcionalidade de tente em termos estritos.</span><span class="sxs-lookup"><span data-stu-id="7fb67-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="7fb67-125">Se o membro falhar por algum motivo que não seja o tente bem definido, o membro ainda deve lançar uma exceção correspondente.</span><span class="sxs-lookup"><span data-stu-id="7fb67-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="7fb67-126">**✓ CONSIDERE** o padrão de Try-análise para os membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.</span><span class="sxs-lookup"><span data-stu-id="7fb67-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="7fb67-127">**FAZER ✓** usam o prefixo "Try" e Boolean tipo de retorno para métodos de implementar esse padrão.</span><span class="sxs-lookup"><span data-stu-id="7fb67-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="7fb67-128">**FAZER ✓** fornecem um membro geradoras de exceções para cada membro usando o padrão de análise de Try.</span><span class="sxs-lookup"><span data-stu-id="7fb67-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="7fb67-129">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="7fb67-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7fb67-130">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="7fb67-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb67-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fb67-131">See Also</span></span>  
 [<span data-ttu-id="7fb67-132">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="7fb67-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="7fb67-133">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="7fb67-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)

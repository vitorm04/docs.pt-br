---
title: Exceções e desempenho
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: KrzysztofCwalina
ms.openlocfilehash: ab125117836545b9a2436347375ed0e08c591c7b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153742"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="c7fd0-102">Exceções e desempenho</span><span class="sxs-lookup"><span data-stu-id="c7fd0-102">Exceptions and Performance</span></span>
<span data-ttu-id="c7fd0-103">Uma preocupação comuns relacionada às exceções é que, se as exceções são usadas para o código que rotineiramente falha, o desempenho da implementação será inaceitável.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="c7fd0-104">Isso é uma preocupação válida.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-104">This is a valid concern.</span></span> <span data-ttu-id="c7fd0-105">Quando um membro lança uma exceção, seu desempenho pode ser ordens de magnitude mais lentas.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="c7fd0-106">No entanto, é possível atingir um bom desempenho enquanto estritamente aderindo às diretrizes exceção que não é permitido usar códigos de erro.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="c7fd0-107">Dois padrões descritos nesta seção sugerem maneiras de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="c7fd0-108">**X DO NOT** usar códigos de erro devido a questões que exceções podem afetar negativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="c7fd0-109">Para melhorar o desempenho, é possível usar o padrão de testador mal-intencionado ou o padrão Try Parse, descritas nas próximas duas seções.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="c7fd0-110">Padrão de testador mal-intencionado</span><span class="sxs-lookup"><span data-stu-id="c7fd0-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="c7fd0-111">Às vezes, o desempenho de um membro de exceções pode ser melhorado ao dividir o membro em duas.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="c7fd0-112">Vamos examinar a <xref:System.Collections.Generic.ICollection%601.Add%2A> método da <xref:System.Collections.Generic.ICollection%601> interface.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="c7fd0-113">O método `Add` gera se a coleção é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="c7fd0-114">Isso pode ser um problema de desempenho em cenários em que a chamada de método deve falhar com frequência.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="c7fd0-115">Uma das maneiras de atenuar o problema é se a coleção é gravável antes de tentar adicionar um valor de teste.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="c7fd0-116">O membro usado para testar uma condição, que, em nosso exemplo, é a propriedade `IsReadOnly`, é conhecido como o testador.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="c7fd0-117">O membro usado para executar uma operação potencialmente gerando, o `Add` método em nosso exemplo, é conhecido como o mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="c7fd0-118">**✓ CONSIDER** o padrão de mal-intencionado Testador de membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="c7fd0-119">Padrão de try Parse</span><span class="sxs-lookup"><span data-stu-id="c7fd0-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="c7fd0-120">Para APIs extremamente sensíveis ao desempenho, um padrão ainda mais rápido que o padrão de testador mal-intencionado descrito na seção anterior deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="c7fd0-121">O padrão de chamadas para ajustar o nome do membro para fazer um teste bem definido caso uma parte da semântica de membros.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="c7fd0-122">Por exemplo, <xref:System.DateTime> define um <xref:System.DateTime.Parse%2A> método que lança uma exceção se uma cadeia de caracteres de análise falhar.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="c7fd0-123">Ele também define uma correspondente <xref:System.DateTime.TryParse%2A> método que tenta analisar, mas retorna false se a análise for bem-sucedida e retorna o resultado de uma bem-sucedida análise usando um `out` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
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
  
 <span data-ttu-id="c7fd0-124">Ao usar esse padrão, é importante definir a funcionalidade de try em termos estritos.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="c7fd0-125">Se o membro falhar por algum motivo que não seja a tentativa bem definido, o membro ainda deve lançar uma exceção correspondente.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="c7fd0-126">**✓ CONSIDER** o padrão de Try-análise para os membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="c7fd0-127">**✓ DO** usam o prefixo "Try" e Boolean tipo de retorno para métodos de implementar esse padrão.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="c7fd0-128">**✓ DO** fornecem um membro geradoras de exceções para cada membro usando o padrão de análise de Try.</span><span class="sxs-lookup"><span data-stu-id="c7fd0-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="c7fd0-129">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="c7fd0-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c7fd0-130">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c7fd0-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7fd0-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7fd0-131">See also</span></span>

- [<span data-ttu-id="c7fd0-132">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="c7fd0-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="c7fd0-133">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="c7fd0-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)

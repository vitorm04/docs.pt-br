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
ms.openlocfilehash: afa4e748599781a5979823320d8913ff5357d415
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741651"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="92abc-102">Exceções e desempenho</span><span class="sxs-lookup"><span data-stu-id="92abc-102">Exceptions and Performance</span></span>
<span data-ttu-id="92abc-103">Uma preocupação comum relacionada às exceções é que, se as exceções forem usadas para o código que falha rotineiramente, o desempenho da implementação será inaceitável.</span><span class="sxs-lookup"><span data-stu-id="92abc-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="92abc-104">Essa é uma preocupação válida.</span><span class="sxs-lookup"><span data-stu-id="92abc-104">This is a valid concern.</span></span> <span data-ttu-id="92abc-105">Quando um membro gera uma exceção, seu desempenho pode ser uma ordem de magnitude mais lenta.</span><span class="sxs-lookup"><span data-stu-id="92abc-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="92abc-106">No entanto, é possível obter um bom desempenho, atendendo estritamente às diretrizes de exceção que não permitem o uso de códigos de erro.</span><span class="sxs-lookup"><span data-stu-id="92abc-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="92abc-107">Dois padrões descritos nesta seção sugerem maneiras de fazer isso.</span><span class="sxs-lookup"><span data-stu-id="92abc-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="92abc-108">❌ não usam códigos de erro devido a problemas que as exceções podem afetar negativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="92abc-108">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="92abc-109">Para melhorar o desempenho, é possível usar o padrão Tester-doer ou o padrão try-Parse, descrito nas duas próximas seções.</span><span class="sxs-lookup"><span data-stu-id="92abc-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="92abc-110">Padrão de teste-doer</span><span class="sxs-lookup"><span data-stu-id="92abc-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="92abc-111">Às vezes, o desempenho de um membro de lançamento de exceção pode ser melhorado ao dividir o membro em dois.</span><span class="sxs-lookup"><span data-stu-id="92abc-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="92abc-112">Vejamos o método <xref:System.Collections.Generic.ICollection%601.Add%2A> da interface <xref:System.Collections.Generic.ICollection%601>.</span><span class="sxs-lookup"><span data-stu-id="92abc-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="92abc-113">O método `Add` gera se a coleção é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="92abc-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="92abc-114">Isso pode ser um problema de desempenho em cenários em que a chamada do método deve falhar com frequência.</span><span class="sxs-lookup"><span data-stu-id="92abc-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="92abc-115">Uma das maneiras de mitigar o problema é testar se a coleção é gravável antes de tentar adicionar um valor.</span><span class="sxs-lookup"><span data-stu-id="92abc-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="92abc-116">O membro usado para testar uma condição, que, em nosso exemplo, é a propriedade `IsReadOnly`, é chamado de testador.</span><span class="sxs-lookup"><span data-stu-id="92abc-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="92abc-117">O membro usado para executar uma operação potencialmente de lançamento, o método `Add` em nosso exemplo, é chamado de doer.</span><span class="sxs-lookup"><span data-stu-id="92abc-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="92abc-118">✔️ Considere o padrão Tester-doer para membros que podem gerar exceções em cenários comuns para evitar problemas de desempenho relacionados a exceções.</span><span class="sxs-lookup"><span data-stu-id="92abc-118">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="92abc-119">Padrão Experimente-Parse</span><span class="sxs-lookup"><span data-stu-id="92abc-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="92abc-120">Para APIs extremamente sensíveis ao desempenho, um padrão ainda mais rápido do que o padrão testador doer descrito na seção anterior deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="92abc-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="92abc-121">O padrão chama o ajuste do nome do membro para fazer com que um caso de teste bem definido faça parte da semântica do membro.</span><span class="sxs-lookup"><span data-stu-id="92abc-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="92abc-122">Por exemplo, <xref:System.DateTime> define um método <xref:System.DateTime.Parse%2A> que gera uma exceção se a análise de uma cadeia de caracteres falhar.</span><span class="sxs-lookup"><span data-stu-id="92abc-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="92abc-123">Ele também define um método <xref:System.DateTime.TryParse%2A> correspondente que tenta analisar, mas retorna false se a análise não for bem-sucedida e retornar o resultado de uma análise bem-sucedida usando um parâmetro `out`.</span><span class="sxs-lookup"><span data-stu-id="92abc-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="92abc-124">Ao usar esse padrão, é importante definir a funcionalidade Try em termos estritos.</span><span class="sxs-lookup"><span data-stu-id="92abc-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="92abc-125">Se o membro falhar por algum motivo além da tentativa definida, o membro ainda deverá lançar uma exceção correspondente.</span><span class="sxs-lookup"><span data-stu-id="92abc-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="92abc-126">✔️ Considere o padrão Experimente-Parse para membros que podem gerar exceções em cenários comuns para evitar problemas de desempenho relacionados a exceções.</span><span class="sxs-lookup"><span data-stu-id="92abc-126">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="92abc-127">✔️ Use o prefixo "try" e o tipo de retorno booliano para métodos que implementam esse padrão.</span><span class="sxs-lookup"><span data-stu-id="92abc-127">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="92abc-128">✔️ fornecer um membro de lançamento de exceção para cada membro usando o padrão try-Parse.</span><span class="sxs-lookup"><span data-stu-id="92abc-128">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="92abc-129">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="92abc-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="92abc-130">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="92abc-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="92abc-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92abc-131">See also</span></span>

- [<span data-ttu-id="92abc-132">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="92abc-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="92abc-133">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="92abc-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)

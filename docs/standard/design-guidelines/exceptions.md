---
title: Diretrizes de design para exceções
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
ms.openlocfilehash: d7580d4d3953b279824bba76b44c4134a7293b7a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289766"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="71869-102">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="71869-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="71869-103">O tratamento de exceções tem muitas vantagens sobre o relatório de erros baseado em valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="71869-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="71869-104">Um bom design de estrutura ajuda o desenvolvedor de aplicativos a obter os benefícios das exceções.</span><span class="sxs-lookup"><span data-stu-id="71869-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="71869-105">Esta seção aborda os benefícios das exceções e apresenta as diretrizes para usá-las com eficiência.</span><span class="sxs-lookup"><span data-stu-id="71869-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71869-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="71869-106">In This Section</span></span>  
 [<span data-ttu-id="71869-107">Lançamento de exceção</span><span class="sxs-lookup"><span data-stu-id="71869-107">Exception Throwing</span></span>](exception-throwing.md)  
 [<span data-ttu-id="71869-108">Usar tipos de exceção padrão</span><span class="sxs-lookup"><span data-stu-id="71869-108">Using Standard Exception Types</span></span>](using-standard-exception-types.md)  
 [<span data-ttu-id="71869-109">Exceções e desempenho</span><span class="sxs-lookup"><span data-stu-id="71869-109">Exceptions and Performance</span></span>](exceptions-and-performance.md)  
 <span data-ttu-id="71869-110">*Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="71869-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="71869-111">*Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="71869-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71869-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="71869-112">See also</span></span>

- [<span data-ttu-id="71869-113">Diretrizes de design de estrutura</span><span class="sxs-lookup"><span data-stu-id="71869-113">Framework Design Guidelines</span></span>](index.md)

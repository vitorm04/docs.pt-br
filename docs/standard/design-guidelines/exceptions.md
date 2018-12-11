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
author: KrzysztofCwalina
ms.openlocfilehash: 60c3d25138c224f5eabf44d06b6c9a8373eb5f96
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153183"
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="67880-102">Diretrizes de design para exceções</span><span class="sxs-lookup"><span data-stu-id="67880-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="67880-103">Manipulação de exceção tem muitas vantagens sobre o relatório de erros com base no valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="67880-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="67880-104">Design de boa estrutura ajuda o desenvolvedor do aplicativo perceber os benefícios de exceções.</span><span class="sxs-lookup"><span data-stu-id="67880-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="67880-105">Esta seção aborda os benefícios de exceções e apresenta diretrizes para usá-los com eficiência.</span><span class="sxs-lookup"><span data-stu-id="67880-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67880-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="67880-106">In This Section</span></span>  
 [<span data-ttu-id="67880-107">Gerando exceções</span><span class="sxs-lookup"><span data-stu-id="67880-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="67880-108">Usando tipos de exceção padrão</span><span class="sxs-lookup"><span data-stu-id="67880-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="67880-109">Exceções e desempenho</span><span class="sxs-lookup"><span data-stu-id="67880-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="67880-110">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="67880-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="67880-111">*Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="67880-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67880-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67880-112">See also</span></span>

- [<span data-ttu-id="67880-113">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="67880-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)

---
title: Interoperabilidade de exceções
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 2aff71e97e1be0dbb584f4fe43c322cea86d2480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795171"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="c135c-102">Trabalhando com exceções de interoperabilidade em código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="c135c-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="c135c-103">A interoperabilidade de exceção de código não gerenciado tem suporte apenas em plataformas Windows.</span><span class="sxs-lookup"><span data-stu-id="c135c-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="c135c-104">Os problemas de portabilidade surgem em plataformas que não são do Windows.</span><span class="sxs-lookup"><span data-stu-id="c135c-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="c135c-105">Como a ABI do Unix não tem nenhuma definição para tratamento de exceções, o código gerenciado não sabe como os mecanismos de exceção funcionam nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="c135c-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="c135c-106">Portanto, as exceções podem acabar resultando em comportamentos imprevisíveis e falhas.</span><span class="sxs-lookup"><span data-stu-id="c135c-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="c135c-107">Comportamentos de setjmp/longjmp</span><span class="sxs-lookup"><span data-stu-id="c135c-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="c135c-108">Não há suporte para a interoperabilidade com funções `setjmp` e `longjmp` C.</span><span class="sxs-lookup"><span data-stu-id="c135c-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="c135c-109">Você não pode usar `longjmp` para ignorar os quadros gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c135c-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="c135c-110">Para obter mais informações, consulte a [documentação do longjmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).</span><span class="sxs-lookup"><span data-stu-id="c135c-110">For more information, see [longjmp documentation](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="c135c-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="c135c-111">See also</span></span>

- [<span data-ttu-id="c135c-112">Exceções</span><span class="sxs-lookup"><span data-stu-id="c135c-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="c135c-113">Interoperabilidade com bibliotecas nativas</span><span class="sxs-lookup"><span data-stu-id="c135c-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)

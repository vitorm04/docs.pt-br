---
title: Interoperabilidade de exceções
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 90774b5d1b64feb34e01f48708d94f8f841a7c9d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550866"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="a092b-102">Trabalhando com exceções de interoperabilidade em código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="a092b-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="a092b-103">A interoperabilidade de exceção de código não gerenciado tem suporte apenas em plataformas Windows.</span><span class="sxs-lookup"><span data-stu-id="a092b-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="a092b-104">Os problemas de portabilidade surgem em plataformas que não são do Windows.</span><span class="sxs-lookup"><span data-stu-id="a092b-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="a092b-105">Como a ABI do Unix não tem nenhuma definição para tratamento de exceções, o código gerenciado não sabe como os mecanismos de exceção funcionam nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="a092b-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="a092b-106">Portanto, as exceções podem acabar resultando em comportamentos imprevisíveis e falhas.</span><span class="sxs-lookup"><span data-stu-id="a092b-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="a092b-107">Comportamentos de setjmp/longjmp</span><span class="sxs-lookup"><span data-stu-id="a092b-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="a092b-108">`setjmp` `longjmp` Não há suporte para as funções Interop com e C.</span><span class="sxs-lookup"><span data-stu-id="a092b-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="a092b-109">Não é possível usar o `longjmp` para ignorar os quadros gerenciados.</span><span class="sxs-lookup"><span data-stu-id="a092b-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="a092b-110">Para obter mais informações, consulte a [documentação do longjmp](/cpp/c-runtime-library/reference/longjmp).</span><span class="sxs-lookup"><span data-stu-id="a092b-110">For more information, see [longjmp documentation](/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="a092b-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="a092b-111">See also</span></span>

- [<span data-ttu-id="a092b-112">Exceções</span><span class="sxs-lookup"><span data-stu-id="a092b-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="a092b-113">Interoperabilidade com bibliotecas nativas</span><span class="sxs-lookup"><span data-stu-id="a092b-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)

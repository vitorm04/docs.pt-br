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
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>Trabalhando com exceções de interoperabilidade em código não gerenciado

A interoperabilidade de exceção de código não gerenciado tem suporte apenas em plataformas Windows. Os problemas de portabilidade surgem em plataformas que não são do Windows. Como a ABI do Unix não tem nenhuma definição para tratamento de exceções, o código gerenciado não sabe como os mecanismos de exceção funcionam nos bastidores. Portanto, as exceções podem acabar resultando em comportamentos imprevisíveis e falhas.

## <a name="setjmplongjmp-behaviors"></a>Comportamentos de setjmp/longjmp

`setjmp` `longjmp` Não há suporte para as funções Interop com e C. Não é possível usar o `longjmp` para ignorar os quadros gerenciados.

Para obter mais informações, consulte a [documentação do longjmp](/cpp/c-runtime-library/reference/longjmp).

## <a name="see-also"></a>Confira também

- [Exceções](index.md)
- [Interoperabilidade com bibliotecas nativas](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)

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
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>Trabalhando com exceções de interoperabilidade em código não gerenciado

A interoperabilidade de exceção de código não gerenciado tem suporte apenas em plataformas Windows. Os problemas de portabilidade surgem em plataformas que não são do Windows. Como a ABI do Unix não tem nenhuma definição para tratamento de exceções, o código gerenciado não sabe como os mecanismos de exceção funcionam nos bastidores. Portanto, as exceções podem acabar resultando em comportamentos imprevisíveis e falhas.

## <a name="setjmplongjmp-behaviors"></a>Comportamentos de setjmp/longjmp

Não há suporte para a interoperabilidade com funções `setjmp` e `longjmp` C. Você não pode usar `longjmp` para ignorar os quadros gerenciados.

Para obter mais informações, consulte a [documentação do longjmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).

## <a name="see-also"></a>Veja também

- [Exceções](index.md)
- [Interoperabilidade com bibliotecas nativas](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)

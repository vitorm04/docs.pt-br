---
description: '#endif – Referência de C#'
title: '#endif – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 8068a6e437145178fd5c88763c86692a8700c349
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138157"
---
# <a name="endif-c-reference"></a>#endif (Referência de C#)
O `#endif` especifica o final de uma diretiva condicional, que começou com a diretiva [#if](./preprocessor-if.md). Por exemplo,  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a>Comentários  
 Uma diretiva condicional, começando com uma diretiva `#if`, deve ser encerrada explicitamente com uma diretiva `#endif`. Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#endif`.  
  
## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Guia de programação C#](../../programming-guide/index.md)
- [Diretivas de pré-processador do C#](./index.md)

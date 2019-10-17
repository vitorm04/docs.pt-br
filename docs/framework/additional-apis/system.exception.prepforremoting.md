---
title: Método Exception. PrepForRemoting (sistema)
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405028"
---
# <a name="exceptionprepforremoting-method"></a>Método Exception. PrepForRemoting

Preserva o rastreamento de pilha do lado do servidor anexando-o à mensagem antes que a exceção seja relançada no site de chamada do cliente.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Retorna

<xref:System.Exception>  
Esta instância <xref:System.Exception>.

## <a name="remarks"></a>Comentários

> [!WARNING]
> O método `Exception.PrepForRemoting` é interno e não deve ser usado diretamente no seu código.
>
> A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.

## <a name="requirements"></a>Requisitos

**Namespace:** <xref:System>

**Assembly:** mscorlib. dll (em mscorlib. dll)

**.NET Framework versões:** Disponível desde 1,0.

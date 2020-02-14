---
title: Método Exception. PrepForRemoting (sistema)
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214893"
---
# <a name="exceptionprepforremoting-method"></a>Método Exception.PrepForRemoting

Preserva o rastreamento de pilha do lado do servidor anexando-o à mensagem antes que a exceção seja relançada no site de chamada do cliente.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Retornos

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

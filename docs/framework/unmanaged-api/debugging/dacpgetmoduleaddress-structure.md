---
title: Estrutura DacpGetModuleAddress
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c0a12ab638adfccfb6406aa495bd3568911ee969
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619773"
---
# <a name="dacpgetmoduleaddress-structure"></a>Estrutura DacpGetModuleAddress

Define o contêiner para uma solicitação de endereço do módulo.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a>Membros

| Membro      | Descrição                |
| ----------- | -------------------------- |
| `ModulePtr` | O ponteiro para o módulo. |

## <a name="methods"></a>Métodos

| Método                                                                                               | Descrição                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Solicitação](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | Executa uma solicitação para preencher a estrutura da estrutura de determinado tempo de execução. |

## <a name="remarks"></a>Comentários

Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca. Para usá-lo, definir a estrutura conforme especificado acima, onde `CLRDATA_ADDRESS` é um inteiro sem sinal de 64 bits.

## <a name="requirements"></a>Requisitos
**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)

---
title: ICorDebugILCode2::Método GetInstrumentedILMap
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: 728a6c83dc321fa28dc4ff84c4e874d886524b36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788565"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>ICorDebugILCode2::Método GetInstrumentedILMap
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Retorna um mapa dos deslocamentos da linguagem intermediária (IL) instrumentados pelo criador de perfis para os deslocamentos da IL do método original para esta instância.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 cMap  
 [in] A capacidade de armazenamento da matriz de `map`. Consulte a seção Comentários para obter mais informações.  
  
 pcMap  
 [out] O número dos valores COR_IL_MAP gravados na matriz de mapa.  
  
 map  
 [out] Uma matriz de valores do COR_IL_MAP que fornece informações sobre mapeamentos da IL instrumentada pelo criador de perfis para a IL do método original.  
  
## <a name="remarks"></a>Comentários  
 Se o criador de perfil definir o mapeamento chamando o método [ICorProfilerInfo:: SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , o depurador poderá chamar esse método para recuperar o mapeamento e usar o mapeamento internamente ao calcular deslocamentos de Il para rastreamentos de pilha e tempos de vida variáveis.  
  
 Se `cMap` for 0 e `pcMap` for não**nulo**, `pcMap` será definido como o número de valores de COR_IL_MAP disponíveis. Se `cMap` for não zero, representará a capacidade de armazenamento da matriz do `map`. Quando o método retorna, `map` contém um máximo de `cMap` itens e `pcMap` é definido como o número de valores de COR_IL_MAP gravados na matriz de `map`.  
  
 Se a IL não tiver sido instrumentada ou o mapeamento não tiver sido fornecido por um criador de perfil, esse método retorna `S_OK` e define `pcMap` para 0.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [Interface ICorDebugILCode2](icordebugilcode2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)

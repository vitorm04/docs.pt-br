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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a712ed9e3534ca6bb2962989f1ab3750a25d539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
  
#### <a name="parameters"></a>Parâmetros  
 cMap  
 [in] A capacidade de armazenamento da matriz de `map`. Consulte a seção Comentários para obter mais informações.  
  
 pcMap  
 [out] O número de valores COR_IL_MAP gravado para a matriz de mapa.  
  
 map  
 [out] Uma matriz de valores COR_IL_MAP que fornecem informações sobre mapeamentos de IL instrumentado criador de perfil para o nível de integridade do método original.  
  
## <a name="remarks"></a>Comentários  
 Se o criador de perfil define o mapeamento chamando o [: Setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) método, o depurador pode chamar esse método para recuperar o mapeamento e usar o mapeamento internamente ao calcular IL desloca para a pilha os rastreamentos e tempos de vida de variáveis.  
  
 Se `cMap` é 0 e `pcMap` é não -**nulo**, `pcMap` é definido como o número de valores COR_IL_MAP disponíveis. Se `cMap` for não zero, representará a capacidade de armazenamento da matriz do `map`. Quando o método retorna, `map` conterá um máximo de `cMap` itens, e `pcMap` é definido como o número de valores COR_IL_MAP gravados a `map` matriz.  
  
 Se a IL não tiver sido instrumentada ou o mapeamento não tiver sido fornecido por um criador de perfil, esse método retorna `S_OK` e define `pcMap` para 0.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [: Setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)  
 [Interface ICorDebugILCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

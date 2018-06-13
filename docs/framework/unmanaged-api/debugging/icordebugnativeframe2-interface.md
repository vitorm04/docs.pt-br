---
title: Interface ICorDebugNativeFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd8f1adee6bbcb3b57b87a2d6c85c01c624da9ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421224"
---
# <a name="icordebugnativeframe2-interface"></a>Interface ICorDebugNativeFrame2
Fornece métodos que testam relações de quadros pai e filho.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método IsChild](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|Determina se o quadro atual é um quadro filho.|  
|[Método IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|Determina se o intervalo especificado é o pai do quadro atual.|  
|[Método GetStackParameterSize](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|Retorna o tamanho cumulativo dos parâmetros na pilha em sistemas operacionais x86.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface logicamente estende a interface de "ICorDebugNativeFrame".  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
    
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)

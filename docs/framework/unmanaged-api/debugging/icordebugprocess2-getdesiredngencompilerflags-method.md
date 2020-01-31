---
title: Método ICorDebugProcess2::GetDesiredNGENCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: 015735e1c6c3b6c146f2fca3a9bdc28baeca2f92
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792515"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>Método ICorDebugProcess2::GetDesiredNGENCompilerFlags
Obtém as configurações de sinalizador do compilador atual que o Common Language Runtime (CLR) usa para selecionar a imagem pré-compilada (ou seja, nativa) correta a ser carregada nesse processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pdwFlags`  
 fora Um ponteiro para uma combinação de bits de valor de enumeração de [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) que são usados para selecionar a imagem pré-compilada correta a ser carregada.  
  
## <a name="remarks"></a>Comentários  
 Use o método [ICorDebugProcess2:: SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) para definir os sinalizadores que o CLR usará para selecionar a imagem previamente compilada correta a ser carregada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

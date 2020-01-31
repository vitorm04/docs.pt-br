---
title: Método ICorDebugEval::NewObjectNoConstructor
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: 45efa1939813a319e996a72fef62ada167b877c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788694"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a>Método ICorDebugEval::NewObjectNoConstructor
Aloca uma nova instância de objeto do tipo especificado, sem tentar chamar um método de construtor.  
  
 Esse método é obsoleto no .NET Framework versão 2,0. Use [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pClass`  
 no Ponteiro para um objeto ICorDebugClass que representa o tipo de objeto a ser instanciado.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 1,1, 1,0  
  
## <a name="see-also"></a>Veja também

- [Método NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md)

---
title: Método ICorProfilerInfo::GetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2960bc0cfc39adb9b7cbca236d495baf630a173
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991842"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>Método ICorProfilerInfo::GetILFunctionBody
Obtém um ponteiro para o corpo de um método no código do Microsoft intermediate language (MSIL), começando em seu cabeçalho.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] A ID do módulo no qual a função reside.  
  
 `methodId`  
 [in] O token de metadados para o método.  
  
 `ppMethodHeader`  
 [out] Um ponteiro para o cabeçalho do método.  
  
 `pcbMethodSize`  
 [out] Um inteiro que especifica o tamanho do método.  
  
## <a name="remarks"></a>Comentários  
 Um método é delimitado pelo módulo no qual ele reside. Porque o `GetILFunctionBody` método foi projetado para fornecer um acesso à ferramenta para o código MSIL antes de eles terem sido carregados pelo common language runtime (CLR), ele usa o token de metadados do método para localizar a instância desejada.  
  
 `GetILFunctionBody` pode retornar um HRESULT de CORPROF_E_FUNCTION_NOT_IL se o `methodId` aponta para um método sem qualquer MSIL de código (como um método abstrato ou uma plataforma de invocação de método (PInvoke)).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

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
ms.openlocfilehash: 8160bb5b9ca5e0a4e22a1a831e978eaf125e7605
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870486"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>Método ICorProfilerInfo::GetILFunctionBody
Obtém um ponteiro para o corpo de um método no código da MSIL (Microsoft Intermediate Language), começando em seu cabeçalho.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 no A ID do módulo no qual a função reside.  
  
 `methodId`  
 no O token de metadados para o método.  
  
 `ppMethodHeader`  
 fora Um ponteiro para o cabeçalho do método.  
  
 `pcbMethodSize`  
 fora Um inteiro que especifica o tamanho do método.  
  
## <a name="remarks"></a>Comentários  
 Um método tem o escopo definido pelo módulo no qual reside. Como o método `GetILFunctionBody` foi projetado para fornecer uma ferramenta de acesso ao código MSIL antes de ser carregado pelo Common Language Runtime (CLR), ele usa o token de metadados do método para localizar a instância desejada.  
  
 `GetILFunctionBody` pode retornar um CORPROF_E_FUNCTION_NOT_IL HRESULT se o `methodId` aponta para um método sem qualquer código MSIL (como um método abstrato ou um método de invocação de plataforma (PInvoke)).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)

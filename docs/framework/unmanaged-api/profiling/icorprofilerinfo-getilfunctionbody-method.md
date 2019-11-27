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
ms.openlocfilehash: a7ec50c91ce02958d0d44643d4f79da1680532aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450362"
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
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

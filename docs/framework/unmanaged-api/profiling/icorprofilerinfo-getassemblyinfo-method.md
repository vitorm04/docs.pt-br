---
title: Método ICorProfilerInfo::GetAssemblyInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 4f3d9bc94d25ca70e0589e1beb86b8ef96807a71
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448169"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>Método ICorProfilerInfo::GetAssemblyInfo
Aceita uma ID de assembly e retorna o nome do assembly e a ID do seu módulo de manifesto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `assemblyId`  
 no O identificador do assembly.  
  
 `cchName`  
 no O comprimento, em caracteres, de `szName`.  
  
 `pcchName`  
 fora Um ponteiro para o comprimento total do caractere do nome do assembly.  
  
 `szName`  
 fora Um buffer de caracteres largo fornecido pelo chamador. Quando a função retornar, ela conterá o nome do assembly.  
  
 `pAppDomainId`  
 fora Um ponteiro para a ID do domínio do aplicativo que contém o assembly.  
  
 `pModuleId`  
 fora Um ponteiro para a ID do módulo de manifesto do assembly.  
  
## <a name="remarks"></a>Comentários  
 Após esse método retornar, você deve verificar se o buffer de `szName` era grande o suficiente para conter o nome completo do assembly. Para fazer isso, compare o valor que `pcchName` aponta com o valor do parâmetro `cchName`. Se `pcchName` apontar para um valor maior que `cchName`, aloque um buffer de `szName` maior, atualize `cchName` com o tamanho novo, maior e chame `GetAssemblyInfo` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetAssemblyInfo` com um buffer de `szName` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode ajustar o tamanho do buffer com base no valor retornado em `pcchName` e chamar `GetAssemblyInfo` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)

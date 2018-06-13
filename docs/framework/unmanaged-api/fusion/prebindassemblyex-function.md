---
title: Função PreBindAssemblyEx
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d3e2535851d39be642de56a86b78c328ecaf446
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431995"
---
# <a name="prebindassemblyex-function"></a>Função PreBindAssemblyEx
Obtém o nome de exibição de pós-política para um assembly.  
  
 Essa função dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAppCtx`  
 [in] Identifica o contexto do aplicativo.  
  
 `pName`  
 [in] Identifica o nome do assembly.  
  
 `pAsmParent`  
 [in] Identifica o assembly pai. Este parâmetro é ignorado.  
  
 `pwzRuntimeVersion`  
 [in] Identifica a versão de tempo de execução.  
  
 `ppNamePostPolicy`  
 [out] Contém o nome de exibição de pós política de.  
  
 `pvReserved`  
 [in] Reservado para extensibilidade futura. `pvReserved` deve ser uma referência nula.  
  
## <a name="remarks"></a>Comentários  
 O `ppNamePostPolicy` parâmetro de saída é definido somente se a função retorna um HRESULT FUSION_E_REF_DEF_MISMATCH. Caso contrário, será nulo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

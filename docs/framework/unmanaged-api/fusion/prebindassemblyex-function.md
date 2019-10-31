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
ms.openlocfilehash: db3ba3380d1fc30a8f34683618b5cc326d7d1906
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123052"
---
# <a name="prebindassemblyex-function"></a>Função PreBindAssemblyEx
Obtém o nome de exibição de pós-política para um assembly.  
  
 Essa função dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAppCtx`  
 no Identifica o contexto do aplicativo.  
  
 `pName`  
 no Identifica o nome do assembly.  
  
 `pAsmParent`  
 no Identifica o assembly pai. Este parâmetro é ignorado.  
  
 `pwzRuntimeVersion`  
 no Identifica a versão de tempo de execução.  
  
 `ppNamePostPolicy`  
 fora Contém o nome de exibição de pós-política.  
  
 `pvReserved`  
 no Reservado para extensibilidade futura. `pvReserved` deve ser uma referência nula.  
  
## <a name="remarks"></a>Comentários  
 O parâmetro de saída `ppNamePostPolicy` será definido somente se a função retornar HRESULT FUSION_E_REF_DEF_MISMATCH. Caso contrário, será nulo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções estáticas globais de fusão](fusion-global-static-functions.md)

---
title: Função CoInitializeEE
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 061a54dd3b3700840f90843a135cf81d8ed81a2e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481151"
---
# <a name="coinitializeee-function"></a>Função CoInitializeEE
Garante que o mecanismo de execução do common language runtime é carregado em um processo. Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Use o [iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `fFlags`  
 [in] Um dos [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) constantes de enumeração.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro padrão COM conforme definido em Winerror. h e os valores na tabela a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O mecanismo de execução foi carregado com êxito.|  
|S_FALSE|O mecanismo de execução já está carregado.|  
|E_FAIL|Não foi possível carregar o mecanismo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Esse método carrega o mecanismo de execução, se ele não foi carregado anteriormente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Funções estáticas globais de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

---
title: Método IValidator::FormatEventInfo
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecbecec86d81357000679ab50e12f06d91c9f50d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217075"
---
# <a name="ivalidatorformateventinfo-method"></a>Método IValidator::FormatEventInfo
Obtém a mensagem de erro correspondente ao erro de validação especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `hVECode`  
 [in] O valor HRESULT que foi passado para o manipulador de erro de validação.  
  
 `Context`  
 [in] Um `VEContext` instância que contém informações de contexto sobre o erro de validação.  
  
 `msg`  
 [no, out] Uma cadeia de caracteres que contém a mensagem de erro retornado.  
  
 `ulMaxLength`  
 [in] O comprimento máximo da mensagem de erro.  
  
 `psa`  
 [in] Uma matriz segura que contém os parâmetros adicionais que descreve o erro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** IValidator.idl, IValidator.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  

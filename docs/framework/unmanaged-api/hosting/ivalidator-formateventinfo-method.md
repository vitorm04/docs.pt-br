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
ms.openlocfilehash: 9b3a6bab8672f3ef3fca5f89c60b03a43477cce5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123306"
---
# <a name="ivalidatorformateventinfo-method"></a>Método IValidator::FormatEventInfo
Obtém a mensagem de erro correspondente ao erro de validação especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no O valor HRESULT que foi passado para o manipulador de erro de validação.  
  
 `Context`  
 no Uma instância de `VEContext` que contém informações de contexto sobre o erro de validação.  
  
 `msg`  
 [entrada, saída] Uma cadeia de caracteres que contém a mensagem de erro retornada.  
  
 `ulMaxLength`  
 no O comprimento máximo da mensagem de erro.  
  
 `psa`  
 no Uma matriz segura que contém parâmetros adicionais que descrevem o erro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** IValidator. idl, IValidator. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  

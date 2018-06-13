---
title: Método IValidator::Validate
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf2c343db459879ca95372e104aee68b22dee6b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440610"
---
# <a name="ivalidatorvalidate-method"></a>Método IValidator::Validate
Valida o especificado PE (executável portátil) ou arquivo do Microsoft intermediate language (MSIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `veh`  
 [in] Um ponteiro para um `IVEHandler` instância que manipula erros de validação.  
  
 `pAppDomain`  
 [in] Um ponteiro para o domínio de aplicativo no qual o arquivo é carregado.  
  
 `ulFlags`  
 [in] Uma combinação bit a bit de [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valores, indicando as validações que devem ser executadas.  
  
 `ulMaxError`  
 [in] O número máximo de erros permitido antes de sair da validação.  
  
 `token`  
 [in] Não usado.  
  
 `fileName`  
 [in] Uma cadeia de caracteres que especifica o nome do arquivo a ser validado.  
  
 `pe`  
 [in] Um ponteiro para o buffer de memória no qual o arquivo está armazenado.  
  
 `ulSize`  
 [in] O tamanho, em bytes, do arquivo a ser validado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** IValidator.idl, IValidator.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 

---
title: "Função CreateVersionStringFromModule"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9d7d545256393cfbe37216f0d6db064d5e7cb410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="createversionstringfrommodule-function"></a>Função CreateVersionStringFromModule
Cria uma cadeia de caracteres de versão de um caminho de runtime (CLR) de linguagem comum em um processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pidDebuggee`  
 [in] Identificador do processo no qual o destino CLR é carregado.  
  
 `szModuleName`  
 [in] Caminho completo ou relativo para o CLR que é carregado no processo de destino.  
  
 `pBuffer`  
 [out] Retorna o buffer para armazenar a cadeia de caracteres de versão do CLR de destino.  
  
 `cchBuffer`  
 [in] Tamanho de `pBuffer`.  
  
 `pdwLength`  
 [out] Comprimento da cadeia de caracteres de versão retornado por `pBuffer`.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 A cadeia de caracteres de versão para o destino do CLR foi retornada com êxito no `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName`é null ou uma `pBuffer` ou `cchBuffer` é nulo. `pBuffer`e `cchBuffer` devem ser nulos ou não nulo.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` é maior que `cchBuffer`. Isso pode ser um resultado esperado se você passar null para ambos `pBuffer` e `cchBuffer`e consultar o tamanho do buffer necessário usando `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName`não contém um caminho para um CLR válido no processo de destino.  
  
 E_FAIL (ou outros códigos de retorno E_)  
 `pidDebuggee`não faz referência a um processo válido ou outra falha.  
  
## <a name="remarks"></a>Comentários  
 Essa função aceita um processo CLR que é identificado pelo `pidDebuggee` e um caminho de cadeia de caracteres que é especificado pelo `szModuleName`. A cadeia de caracteres de versão é retornada no buffer que `pBuffer` aponta para. Essa cadeia de caracteres é opaca para o usuário de função; ou seja, não há nenhum significado intrínseco na cadeia de versão em si. Ele é usado somente no contexto dessa função e o [função CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Essa função deve ser chamada duas vezes. Quando você chamá-lo na primeira vez, passar null para ambos `pBuffer` e `cchBuffer`. Quando você fizer isso, o tamanho do buffer necessário para `pBuffer` será retornado no `pdwLength`. Em seguida, você pode chamar a função uma segunda vez e passar o buffer no `pBuffer` e seu tamanho no `cchBuffer`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim.h  
  
 **Biblioteca:** dbgshim.dll  
  
 **Versões do .NET framework:** 3.5 SP1

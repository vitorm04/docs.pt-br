---
title: Função CreateVersionStringFromModule
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b68624b962ed610dbeecd3e4cead769ab1400f4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739217"
---
# <a name="createversionstringfrommodule-function"></a>Função CreateVersionStringFromModule
Cria uma cadeia de caracteres de versão de um caminho de runtime (CLR) de linguagem comum em um processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pidDebuggee`  
 [in] Identificador do processo no qual o CLR de destino é carregado.  
  
 `szModuleName`  
 [in] Caminho completo ou relativo para o CLR que é carregado no processo de destino.  
  
 `pBuffer`  
 [out] Retorne o buffer para armazenar a cadeia de caracteres de versão para o CLR de destino.  
  
 `cchBuffer`  
 [in] Tamanho de `pBuffer`.  
  
 `pdwLength`  
 [out] Comprimento da cadeia de caracteres de versão retornada pelo `pBuffer`.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 A cadeia de caracteres de versão para o CLR de destino foi retornada com êxito no `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName` é null ou uma `pBuffer` ou `cchBuffer` é nulo. `pBuffer` e `cchBuffer` devem ser ambos nulos ou não nulo.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` é maior que `cchBuffer`. Isso pode ser um resultado esperado se você passar null para ambos `pBuffer` e `cchBuffer`e consultou o tamanho do buffer necessário usando `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` não contém um caminho para um CLR válido no processo de destino.  
  
 E_FAIL (ou outros códigos de retorno e _)  
 `pidDebuggee` não faz referência a um processo válido ou outra falha.  
  
## <a name="remarks"></a>Comentários  
 Essa função aceita um processo CLR é identificado por `pidDebuggee` e um caminho de cadeia de caracteres que é especificado pelo `szModuleName`. A cadeia de caracteres de versão é retornada no buffer que `pBuffer` aponta. Essa cadeia de caracteres é opaca para o usuário de função; ou seja, não há nenhum significado intrínseco na cadeia de versão em si. Ele é usado somente no contexto dessa função e o [função CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Essa função deve ser chamada duas vezes. Quando você chamá-lo na primeira vez, passar null para ambos `pBuffer` e `cchBuffer`. Quando você fizer isso, o tamanho do buffer necessário para `pBuffer` será retornado em `pdwLength`. Em seguida, você pode chamar a função uma segunda vez e passar o buffer no `pBuffer` e seu tamanho em `cchBuffer`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim.h  
  
 **Biblioteca:** dbgshim  
  
 **Versões do .NET framework:** 3,5 SP1

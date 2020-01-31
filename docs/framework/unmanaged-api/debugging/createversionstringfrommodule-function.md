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
ms.openlocfilehash: 609d6e47c951aa104cb23084b65e98827a6851f1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789171"
---
# <a name="createversionstringfrommodule-function"></a>Função CreateVersionStringFromModule
Cria uma cadeia de caracteres de versão de um caminho Common Language Runtime (CLR) em um processo de destino.  
  
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
 no Identificador do processo no qual o CLR de destino é carregado.  
  
 `szModuleName`  
 no Caminho completo ou relativo para o CLR de destino que é carregado no processo.  
  
 `pBuffer`  
 fora Buffer de retorno para armazenar a cadeia de caracteres de versão para o CLR de destino.  
  
 `cchBuffer`  
 no Tamanho de `pBuffer`.  
  
 `pdwLength`  
 fora Comprimento da cadeia de caracteres de versão retornada por `pBuffer`.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 A cadeia de caracteres de versão para o CLR de destino foi retornada com êxito no `pBuffer`.  
  
 {1&gt;E_INVALIDARG&lt;1}  
 o `szModuleName` é nulo ou `pBuffer` ou `cchBuffer` é nulo. `pBuffer` e `cchBuffer` devem ser nulos ou não nulos.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` é maior que `cchBuffer`. Esse pode ser um resultado esperado se você tiver passado nulo para `pBuffer` e `cchBuffer`e consultado o tamanho de buffer necessário usando `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` não contém um caminho para um CLR válido no processo de destino.  
  
 E_FAIL (ou outros códigos de retorno de E_)  
 `pidDebuggee` não se refere a um processo válido ou a outra falha.  
  
## <a name="remarks"></a>Comentários  
 Essa função aceita um processo CLR identificado por `pidDebuggee` e um caminho de cadeia de caracteres especificado por `szModuleName`. A cadeia de caracteres de versão é retornada no buffer ao qual `pBuffer` aponta. Essa cadeia de caracteres é opaca para o usuário da função; ou seja, não há nenhum significado intrínseco na própria cadeia de caracteres de versão. Ele é usado unicamente no contexto dessa função e da [função CreateDebuggingInterfaceFromVersion](createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Essa função deve ser chamada duas vezes. Quando você o chama pela primeira vez, passe NULL para `pBuffer` e `cchBuffer`. Quando você fizer isso, o tamanho do buffer necessário para `pBuffer` será retornado em `pdwLength`. Em seguida, você pode chamar a função uma segunda vez e passar o buffer em `pBuffer` e seu tamanho em `cchBuffer`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim. h  
  
 **Biblioteca:** dbgshim. dll  
  
 **Versões do .NET Framework:** 3,5 SP1

---
title: Função CloseCLREnumeration
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18903bd00b0a9d09365d03c155531a25dc013189
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406082"
---
# <a name="closeclrenumeration-function"></a>Função CloseCLREnumeration
Fecha qualquer válido language runtime (CLR) inicialização continuar eventos comuns localizados em uma matriz de identificadores retornado pelo [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera a memória para as matrizes de caminho do identificador e a cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pHandleArray`  
 [in] Ponteiro para a matriz de identificadores de eventos retornado do [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `pStringArray`  
 [in] Ponteiro para a matriz de caminhos de cadeia de caracteres CLR retornado do [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [in] DWORD que contém o tamanho (comprimento) do `pHandleArray` ou `pStringArray` (eles são os mesmos).  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 Identificadores abertos pelo [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) são fechadas, e a memória alocada para as matrizes de identificador e a cadeia de caracteres é liberada.  
  
 E_INVALIDARG  
 O comprimento de `pHandleArray` não corresponde ao tamanho que é transmitido `dwArrayLength`.  
  
 E_FAIL (ou outros códigos de retorno E_)  
 A função é não é possível liberar a memória para `pHandleArray` e `pStringArray`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim.h  
  
 **Biblioteca:** dbgshim.dll  
  
 **Versões do .NET framework:** 3.5 SP1

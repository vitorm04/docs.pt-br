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
ms.openlocfilehash: 60b6d9c302cd3af9f41e5a8dce62d7eb268c4198
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491871"
---
# <a name="closeclrenumeration-function"></a>Função CloseCLREnumeration
Fecha qualquer válido runtime (CLR) inicialização continuar eventos de common language localizados em uma matriz de identificadores retornado pela [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera a memória para as matrizes de caminho do identificador e a cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pHandleArray`  
 [in] Ponteiro para a matriz de identificadores de eventos retornados do [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `pStringArray`  
 [in] Ponteiro para a matriz de caminhos de cadeia de caracteres CLR retornado do [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).  
  
 `dwArrayLength`  
 [in] Que contém o tamanho (comprimento) de um DWORD `pHandleArray` ou `pStringArray` (eles são iguais).  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 Identificadores abertos pelo [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) são fechados, e a memória alocada para as matrizes de cadeia de caracteres de identificador é liberada.  
  
 E_INVALIDARG  
 O comprimento da `pHandleArray` não corresponde ao tamanho que é passado no `dwArrayLength`.  
  
 E_FAIL (ou outros códigos de retorno e _)  
 A função não é possível liberar a memória para `pHandleArray` e `pStringArray`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** dbgshim.h  
  
 **Biblioteca:** dbgshim  
  
 **Versões do .NET framework:** 3,5 SP1

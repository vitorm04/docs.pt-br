---
title: Função _EFN_GetManagedObjectName
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: 9230e1fcba7c0492e50773e7ca13fb16f07238a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789142"
---
# <a name="_efn_getmanagedobjectname-function"></a>Função \_EFN\_GetManagedObjectName
Obtém o nome de um tipo usando o ponteiro de objeto gerenciado fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `Client`  
 no Um ponteiro para o cliente de depuração.  
  
 `objAddr`  
 no Um ponteiro de objeto gerenciado.  
  
 szName  
 fora O nome do tipo.  
  
 `cbName`  
 fora O número de caracteres disponíveis no buffer de cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Se não houver nenhum código gerenciado no thread atualmente no contexto, a função retornará HRESULT SOS_E_NOMANAGEDCODE com um valor de recurso de 0XA0 e um código de erro de 0x1000.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** SOS_Stacktrace. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando funções estáticas globais](debugging-global-static-functions.md)

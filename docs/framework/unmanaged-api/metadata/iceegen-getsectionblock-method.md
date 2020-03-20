---
title: Método ICeeGen::GetSectionBlock
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176078"
---
# <a name="iceegengetsectionblock-method"></a>Método ICeeGen::GetSectionBlock
Obtém um bloco de seção da base de código.  
  
 Este método é obsoleto e não deve ser utilizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a>parâmetros  
 `section`  
 [em] A seção a partir da qual recuperar um bloco da base de código.  
  
 `len`  
 [em] O comprimento do bloco a ser recuperado.  
  
 `align`  
 [em] O byte, relativo ao início da seção, com o qual alinhar o primeiro byte do bloco. Esta é a posição do bloco dentro da seção.  
  
 `ppBytes`  
 [fora] Um ponteiro para um local que recebe o endereço do bloco recuperado.  
  
## <a name="remarks"></a>Comentários  
 Ligue `GetSectionBlock` somente se tiver requisitos especiais de seção que não sejam tratados por outros métodos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

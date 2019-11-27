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
ms.openlocfilehash: 0731053fb37c775d25052a5fd99a479a44ff5862
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434872"
---
# <a name="iceegengetsectionblock-method"></a>Método ICeeGen::GetSectionBlock
Obtém um bloco de seção da base de código.  
  
 Este método é obsoleto e não deve ser usado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `section`  
 no A seção da qual recuperar um bloco da base de código.  
  
 `len`  
 no O comprimento do bloco a ser recuperado.  
  
 `align`  
 no O byte, em relação ao início da seção, com o qual alinhar o primeiro byte do bloco. Essa é a posição do bloco dentro da seção.  
  
 `ppBytes`  
 fora Um ponteiro para um local que recebe o endereço do bloco recuperado.  
  
## <a name="remarks"></a>Comentários  
 Chame `GetSectionBlock` somente se você tiver requisitos de seção especiais que não são tratados por outros métodos.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

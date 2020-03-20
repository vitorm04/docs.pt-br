---
title: Método ICeeGen::AddSectionReloc
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176104"
---
# <a name="iceegenaddsectionreloc-method"></a>Método ICeeGen::AddSectionReloc
Adiciona uma instrução .reloc à base de código.  
  
 Este método é obsoleto e não deve ser utilizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `section`  
 [em] A seção de código de memória para adicionar uma instrução .reloc.  
  
 `offset`  
 [em] O deslocamento da seção.  
  
 `relativeTo`  
 [em] A seção `offset` a que se refere.  
  
 `relocType`  
 [em] Um dos valores [de CeeSectionRelocType,](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) indicando o tipo de instrução .reloc a ser adicionado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

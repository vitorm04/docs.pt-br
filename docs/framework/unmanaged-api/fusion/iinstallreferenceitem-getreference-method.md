---
title: Método IInstallReferenceItem::GetReference
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9395fcc6d896114c25770edbc17761323285099f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796401"
---
# <a name="iinstallreferenceitemgetreference-method"></a>Método IInstallReferenceItem::GetReference
Obtém um ponteiro para a estrutura [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) representada por este objeto [IInstallReferenceItem](iinstallreferenceitem-interface.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppRefData`  
 fora O ponteiro `FUSION_INSTALL_REFERENCE` retornado.  
  
 `dwFlags`  
 no Reservado para extensibilidade futura. `dwFlags`deve ser 0 (zero).  
  
 `pvReserved`  
 no Reservado para extensibilidade futura. `pvReserved`deve ser uma referência nula.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IInstallReferenceItem](iinstallreferenceitem-interface.md)
- [Estrutura FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md)

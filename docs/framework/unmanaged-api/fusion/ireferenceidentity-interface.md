---
title: Interface IReferenceIdentity
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb8686342b20bd6afe0a4c4803d64428ed95c98b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665767"
---
# <a name="ireferenceidentity-interface"></a>Interface IReferenceIdentity
Representa uma referência para a assinatura exclusiva de um objeto de código.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Obtém um ponteiro de interface para um novo `IReferenceIdentity` que é idêntica a esta instância `IReferenceIdentity`, exceto para as alterações de atributo especificado.|  
|`IReferenceIdentity::EnumAttributes`|Obtém um ponteiro de interface para um `IEnumIDENTITY_ATTRIBUTE` instância que contém os atributos associados a este `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Obtém o valor do atributo no namespace especificado, com o nome especificado.|  
|`IReferenceIdentity::SetAttribute`|Define o atributo que tem o namespace especificado e o nome especificado para o valor especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [Interface IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)

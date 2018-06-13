---
title: Método ICLRDataTarget::GetMachineType
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c515a8184e8c01b0e292057f3f66ffef28f2c5fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402875"
---
# <a name="iclrdatatargetgetmachinetype-method"></a>Método ICLRDataTarget::GetMachineType
Obtém o identificador para o tipo de conjunto de instruções que o processo de destino está usando.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `machineType`  
 [out] Um ponteiro para um valor que indica a instrução que definir o processo de destino está usando. Retornado `machineType` é uma das constantes IMAGE_FILE_MACHINE, que são definidas no arquivo de cabeçalho Winnt. H.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)

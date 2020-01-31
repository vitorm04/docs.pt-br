---
title: Método ICLRDataTarget::GetImageBase
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
ms.openlocfilehash: fcf0ab73c79a5fa116a89cdfcc2e73b17d9eabfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785488"
---
# <a name="iclrdatatargetgetimagebase-method"></a>Método ICLRDataTarget::GetImageBase
Obtém o endereço de memória base da imagem especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `imagePath`  
 no O nome do arquivo da imagem, incluindo seu caminho.  
  
 `baseAddress`  
 fora Um ponteiro para um CLRDATA_ADDRESS que armazena o endereço base da imagem.  
  
## <a name="remarks"></a>Comentários  
 O nome do arquivo de imagem pode ou não ter um caminho. Se um caminho for especificado, a correspondência será feita no caminho inteiro; caso contrário, a correspondência será feita apenas no nome do arquivo.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRDataTarget](iclrdatatarget-interface.md)

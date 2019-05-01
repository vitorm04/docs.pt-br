---
title: Enumeração CorPinvokeMap
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941092f67f66c5b17c8ae592569c2a8e6a675
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045390"
---
# <a name="corpinvokemap-enumeration"></a>Enumeração CorPinvokeMap
Especifica opções para uma chamada de PInvoke.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`pmNoMangle`|Use o nome de cada membro conforme especificado.|  
|`pmCharSetMask`|Reservado.|  
|`pmCharSetNotSpec`|Reservado.|  
|`pmCharSetAnsi`|Realizar marshaling de cadeias de caracteres como cadeias de caracteres de vários bytes.|  
|`pmCharSetUnicode`|Realizar marshaling de cadeias de caracteres como cadeias de caracteres Unicode de 2 bytes.|  
|`pmCharSetAuto`|Realizar marshaling automático de cadeias de caracteres apropriado para o sistema operacional de destino. O padrão é Unicode no Windows NT, Windows 2000, Windows XP e a família Windows Server 2003. o padrão é ANSI no Windows 98 e Windows Me.|  
|`pmBestFitUseAssem`|Reservado.|  
|`pmBestFitEnabled`|Execute o mapeamento de melhor ajuste de caracteres Unicode que não têm uma correspondência exata no conjunto de caracteres ANSI.|  
|`pmBestFitDisabled`|Não execute o mapeamento de melhor ajuste de caracteres Unicode. Nesse caso, todos os caracteres não mapeável serão substituídos por um '?'.|  
|`pmBestFitMask`|Reservado.|  
|`pmThrowOnUnmappableCharUseAssem`|Reservado.|  
|`pmThrowOnUnmappableCharEnabled`|Gera uma exceção quando o marshaler de interoperabilidade encontra um caractere não mapeável.|  
|`pmThrowOnUnmappableCharDisabled`|Não lance uma exceção quando o marshaler de interoperabilidade encontra um caractere não mapeável.|  
|`pmThrowOnUnmappableCharMask`|Reservado|  
|`pmSupportsLastError`|Permitir que o receptor chamar o Win32 `SetLastError` função antes de retornar do método atribuído.|  
|`pmCallConvMask`|Reservado|  
|`pmCallConvWinapi`|Use a plataforma padrão de convenção de chamada. Por exemplo, no Windows o padrão é `StdCall` e no Windows CE .NET é `Cdecl`.|  
|`pmCallConvCdecl`|Use o `Cdecl` convenção de chamada. Nesse caso, o chamador limpa a pilha. Isso permite chamar funções com `varargs` (ou seja, funções que aceitam um número variável de parâmetros).|  
|`pmCallConvStdcall`|Use o `StdCall` convenção de chamada. Nesse caso, o receptor limpa a pilha. Essa é a convenção padrão para chamar funções não gerenciadas com a invocação da plataforma.|  
|`pmCallConvThiscall`|Use o `ThisCall` convenção de chamada. Nesse caso, o primeiro parâmetro é o `this` ponteiro e é armazenado no ecx. Outros parâmetros são enviados por push na pilha. O `ThisCall` convenção de chamada é usada para chamar métodos em classes exportadas de uma DLL não gerenciada.|  
|`pmCallConvFastcall`|Reservado.|  
|`pmMaxValue`|Reservado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

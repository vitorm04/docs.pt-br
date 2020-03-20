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
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176143"
---
# <a name="corpinvokemap-enumeration"></a>Enumeração CorPinvokeMap
Especifica opções para uma chamada PInvoke.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`pmCharSetAuto`|Realizar marshaling automático de cadeias de caracteres apropriado para o sistema operacional de destino. O padrão é Unicode no Windows NT, Windows 2000, Windows XP e a família Windows Server 2003; o padrão é ANSI no Windows 98 e Windows Me.|  
|`pmBestFitUseAssem`|Reservado.|  
|`pmBestFitEnabled`|Execute o mapeamento mais adequado de caracteres Unicode que não possuem uma correspondência exata no conjunto de caracteres ANSI.|  
|`pmBestFitDisabled`|Não execute o mapeamento de melhor ajuste de caracteres Unicode. Neste caso, todos os caracteres inabitáveis serão substituídos por um '?'.|  
|`pmBestFitMask`|Reservado.|  
|`pmThrowOnUnmappableCharUseAssem`|Reservado.|  
|`pmThrowOnUnmappableCharEnabled`|Adumam uma exceção quando o interop marshaler encontra um personagem inabitável.|  
|`pmThrowOnUnmappableCharDisabled`|Não lance uma exceção quando o interop marshaler encontra um personagem inabitável.|  
|`pmThrowOnUnmappableCharMask`|Reservado|  
|`pmSupportsLastError`|Permita que o callee ligue `SetLastError` para a função Win32 antes de retornar do método atribuído.|  
|`pmCallConvMask`|Reservado|  
|`pmCallConvWinapi`|Use a convenção de chamada de plataforma padrão. Por exemplo, no Windows `StdCall` o padrão é e `Cdecl`no Windows CE .NET é .|  
|`pmCallConvCdecl`|Use `Cdecl` a convenção de chamada. Neste caso, o chamador limpa a pilha. Isso permite funções `varargs` de chamada com (ou seja, funções que aceitam um número variável de parâmetros).|  
|`pmCallConvStdcall`|Use `StdCall` a convenção de chamada. Neste caso, a calha limpa a pilha. Essa é a convenção padrão para chamar funções não gerenciadas com a invocação da plataforma.|  
|`pmCallConvThiscall`|Use `ThisCall` a convenção de chamada. Neste caso, o primeiro parâmetro `this` é o ponteiro e é armazenado no registro ECX. Outros parâmetros são enviados por push na pilha. A `ThisCall` convenção de chamada é usada para chamar métodos em classes exportadas de um DLL não gerenciado.|  
|`pmCallConvFastcall`|Reservado.|  
|`pmMaxValue`|Reservado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

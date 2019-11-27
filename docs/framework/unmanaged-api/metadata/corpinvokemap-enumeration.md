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
ms.openlocfilehash: 17b7af7016cf88fd3ae263dd952502d515b0c833
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441564"
---
# <a name="corpinvokemap-enumeration"></a>Enumeração CorPinvokeMap
Especifica as opções para uma chamada PInvoke.  
  
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
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`pmNoMangle`|Use cada nome de membro conforme especificado.|  
|`pmCharSetMask`|Reservado.|  
|`pmCharSetNotSpec`|Reservado.|  
|`pmCharSetAnsi`|Realizar marshaling de cadeias de caracteres como cadeias de caracteres de vários bytes.|  
|`pmCharSetUnicode`|Realizar marshaling de cadeias de caracteres como cadeias de caracteres Unicode de 2 bytes.|  
|`pmCharSetAuto`|Realizar marshaling automático de cadeias de caracteres apropriado para o sistema operacional de destino. O padrão é Unicode no Windows NT, Windows 2000, Windows XP e na família Windows Server 2003; o padrão é ANSI no Windows 98 e Windows me.|  
|`pmBestFitUseAssem`|Reservado.|  
|`pmBestFitEnabled`|Execute o mapeamento de melhor ajuste de caracteres Unicode que não têm uma correspondência exata no conjunto de caracteres ANSI.|  
|`pmBestFitDisabled`|Não execute o mapeamento de melhor ajuste de caracteres Unicode. Nesse caso, todos os caracteres mapeável serão substituídos por um '? '.|  
|`pmBestFitMask`|Reservado.|  
|`pmThrowOnUnmappableCharUseAssem`|Reservado.|  
|`pmThrowOnUnmappableCharEnabled`|Gerar uma exceção quando o marshaling interop encontrar um caractere mapeável.|  
|`pmThrowOnUnmappableCharDisabled`|Não lance uma exceção quando o marshaling interop encontra um caractere mapeável.|  
|`pmThrowOnUnmappableCharMask`|Reservado|  
|`pmSupportsLastError`|Permitir que o receptor chame a função de `SetLastError` do Win32 antes de retornar do método atribuído.|  
|`pmCallConvMask`|Reservado|  
|`pmCallConvWinapi`|Use a Convenção de chamada de plataforma padrão. Por exemplo, no Windows, o padrão é `StdCall` e Windows CE .NET é `Cdecl`.|  
|`pmCallConvCdecl`|Use a Convenção de chamada `Cdecl`. Nesse caso, o chamador limpa a pilha. Isso permite chamar funções com `varargs` (ou seja, funções que aceitam um número variável de parâmetros).|  
|`pmCallConvStdcall`|Use a Convenção de chamada `StdCall`. Nesse caso, o receptor limpa a pilha. Essa é a convenção padrão para chamar funções não gerenciadas com a invocação da plataforma.|  
|`pmCallConvThiscall`|Use a Convenção de chamada `ThisCall`. Nesse caso, o primeiro parâmetro é o ponteiro `this` e é armazenado no Registro ECX. Outros parâmetros são enviados por push na pilha. A Convenção de chamada `ThisCall` é usada para chamar métodos em classes exportadas de uma DLL não gerenciada.|  
|`pmCallConvFastcall`|Reservado.|  
|`pmMaxValue`|Reservado.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

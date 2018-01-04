---
title: "Enumeração CorNativeType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeType
helpviewer_keywords: CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6be442dd74f6a71494e140b76357be1bc9e1b747
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cornativetype-enumeration"></a>Enumeração CorNativeType
Contém valores que descrevem os tipos nativos de não gerenciados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|Obsoleto.|  
|`NATIVE_TYPE_VOID`|Obsoleto.|  
|`NATIVE_TYPE_BOOLEAN`|Um valor booliano de 4 bytes, onde TRUE é diferente de zero e FALSE é zero.|  
|`NATIVE_TYPE_I1`|Um valor inteiro assinado de 8 bits.|  
|`NATIVE_TYPE_U1`|Um valor inteiro não assinado de 8 bits.|  
|`NATIVE_TYPE_I2`|Um valor inteiro de 16 bits com sinal.|  
|`NATIVE_TYPE_U2`|Um valor inteiro de 16 bits sem sinal.|  
|`NATIVE_TYPE_I4`|Um valor inteiro de 32 bits com sinal.|  
|`NATIVE_TYPE_U4`|Um valor inteiro de 32 bits sem sinal.|  
|`NATIVE_TYPE_I8`|Um valor inteiro com sinal de 64 bits.|  
|`NATIVE_TYPE_U8`|Um valor inteiro não assinado de 64 bits.|  
|`NATIVE_TYPE_R4`|Um valor numérico ponto flutuante de 4 bytes.|  
|`NATIVE_TYPE_R8`|Um valor numérico ponto flutuante de 8 bytes.|  
|`NATIVE_TYPE_SYSCHAR`|Obsoleto.|  
|`NATIVE_TYPE_VARIANT`|Obsoleto.|  
|`NATIVE_TYPE_CURRENCY`|Um tipo numérico COM que corresponde ao gerenciado <xref:System.Decimal> tipo.|  
|`NATIVE_TYPE_PTR`|Obsoleto.|  
|`NATIVE_TYPE_DECIMAL`|Obsoleto.|  
|`NATIVE_TYPE_DATE`|Obsoleto.|  
|`NATIVE_TYPE_BSTR`|Interoperabilidade COM.|  
|`NATIVE_TYPE_LPSTR`|Um valor de cadeia de caracteres LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|Um valor de cadeia de caracteres LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Um valor de cadeia de caracteres LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Um valor de cadeia de caracteres fixa, definido pelo sistema.|  
|`NATIVE_TYPE_OBJECTREF`|Obsoleto.|  
|`NATIVE_TYPE_IUNKNOWN`|Interoperabilidade COM.|  
|`NATIVE_TYPE_IDISPATCH`|Interoperabilidade COM.|  
|`NATIVE_TYPE_STRUCT`|Um valor de estrutura nativa.|  
|`NATIVE_TYPE_INTF`|Interoperabilidade COM.|  
|`NATIVE_TYPE_SAFEARRAY`|Interoperabilidade COM.|  
|`NATIVE_TYPE_FIXEDARRAY`|Um valor de matriz de comprimento fixo.|  
|`NATIVE_TYPE_INT`|Um valor inteiro assinado de 16 bits nativo.|  
|`NATIVE_TYPE_UINT`|Um valor inteiro não assinado de 16 bits nativo.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Obsoleto.<br /><br /> Use NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|Interoperabilidade COM.|  
|`NATIVE_TYPE_ANSIBSTR`|Interoperabilidade COM.|  
|`NATIVE_TYPE_TBSTR`|Interoperabilidade COM.<br /><br /> Selecione BSTR ou ANSIBSTR dependendo da plataforma.|  
|`NATIVE_TYPE_VARIANTBOOL`|Um 2 bytes valor booliano, onde TRUE é -1 e FALSE é zero.|  
|`NATIVE_TYPE_FUNC`|Um ponteiro de função.|  
|`NATIVE_TYPE_ASANY`|Uma referência a qualquer tipo nativo.|  
|`NATIVE_TYPE_ARRAY`|Uma referência a uma matriz com membros de um tipo não especificado.|  
|`NATIVE_TYPE_LPSTRUCT`|Um ponteiro de inteiro de 32 bits para uma estrutura.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Um tipo nativo do marshaler personalizado.<br /><br /> Isso deve ser seguido por uma cadeia de caracteres de formato a seguir: "empacotador de nome/0Custom tipo nativo de tipo de cookie de nome/0Optional/0" ou "{nativo digite GUID} 0Custom marshaler cookie de nome/0Optional/0 do tipo"|  
|`NATIVE_TYPE_ERROR`|Interoperabilidade COM.<br /><br /> Com ELEMENT_TYPE_I4 esse tipo é mapeado para VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Um nativo `IInspectable` tipo.|  
|`NATIVE_TYPE_HSTRING`|Um nativo `HString`.|  
|`NATIVE_TYPE_MAX`|Um valor inválido.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.UnmanagedType>  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

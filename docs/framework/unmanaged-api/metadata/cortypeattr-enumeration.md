---
title: "Enumeração CorTypeAttr"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 501488c0ac03ebf508145572ed73163d7940bfbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cortypeattr-enumeration"></a>Enumeração CorTypeAttr
Contém valores que indicam o tipo de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`tdVisibilityMask`|Usado para obter informações de visibilidade de tipo.|  
|`tdNotPublic`|Especifica que o tipo não está no escopo público.|  
|`tdPublic`|Especifica que o tipo de escopo público.|  
|`tdNestedPublic`|Especifica que o tipo é aninhado com visibilidade pública.|  
|`tdNestedPrivate`|Especifica que o tipo é aninhado com visibilidade privada.|  
|`tdNestedFamily`|Especifica que o tipo é aninhado com visibilidade de família.|  
|`tdNestedAssembly`|Especifica que o tipo é aninhado com visibilidade do assembly.|  
|`tdNestedFamANDAssem`|Especifica que o tipo é aninhado com visibilidade de família e ao assembly.|  
|`tdNestedFamORAssem`|Especifica que o tipo é aninhado com visibilidade de família ou assembly.|  
|`tdLayoutMask`|Obtém informações de layout para o tipo.|  
|`tdAutoLayout`|Especifica que os campos deste tipo são dispostos automaticamente.|  
|`tdSequentialLayout`|Especifica que os campos deste tipo são apresentados em sequência.|  
|`tdExplicitLayout`|Especifica o que layout do campo que é fornecido explicitamente.|  
|`tdClassSemanticsMask`|Obtém informações semânticas sobre o tipo.|  
|`tdClass`|Especifica que o tipo é uma classe.|  
|`tdInterface`|Especifica que o tipo é uma interface.|  
|`tdAbstract`|Especifica que o tipo é abstrato.|  
|`tdSealed`|Especifica que o tipo não pode ser estendido.|  
|`tdSpecialName`|Especifica que o nome de classe especial. Descreve seu nome como.|  
|`tdImport`|Especifica que o tipo é importado.|  
|`tdSerializable`|Especifica que o tipo é serializável.|  
|`tdWindowsRuntime`|Especifica que esse tipo é um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipo.|  
|`tdStringFormatMask`|Obtém informações sobre como cadeias de caracteres são codificadas e formatadas.|  
|`tdAnsiClass`|Especifica que esse tipo interpreta um LPTSTR como ANSI.|  
|`tdUnicodeClass`|Especifica que esse tipo interpreta um LPTSTR como Unicode.|  
|`tdAutoClass`|Especifica que esse tipo interpreta um LPTSTR automaticamente.|  
|`tdCustomFormatClass`|Especifica que o tipo tem uma codificação não padrão, conforme especificado por `CustomFormatMask`.|  
|`tdCustomFormatMask`|Use essa máscara para obter informações de codificação não padrão para interoperabilidade nativa. O significado dos valores desses dois bits não está especificado.|  
|`tdBeforeFieldInit`|Especifica que o tipo deve ser inicializado antes da primeira tentativa de acessar um campo estático.|  
|`tdForwarder`|Especifica que o tipo é exportado e um encaminhador de tipo.|  
|`tdReservedMask`|Este sinalizador e os sinalizadores a seguir são usados internamente pelo common language runtime.|  
|`tdRTSpecialName`|Especifica que o common language runtime deve verificar a codificação de nome.|  
|`tdHasSecurity`|Especifica que o tipo tem segurança associada a ele.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

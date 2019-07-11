---
title: Enumeração AssemblyOptions
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 324e30f6cbcaa1d1d81c7c03967dbb629d2cd6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742270"
---
# <a name="assemblyoptions-enumeration"></a>Enumeração AssemblyOptions
Enumera as opções de assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>Campos  
  
|Campo|Descrição|  
|-----------|-----------------|  
|optAssemTitle|Cadeia de caracteres - representa o título do assembly.|  
|optAssemDescription|Cadeia de caracteres - contém a descrição do assembly.|  
|optAssemConfig|Cadeia de caracteres - contém a configuração do assembly.|  
|optAssemOS|Cadeia de caracteres, codificada como: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|Cadeia de caracteres - contém a localidade do assembly.|  
|optAssemVersion|Cadeia de caracteres - codificada como: "Major".|  
|optAssemCompany|Cadeia de caracteres - contém a empresa.|  
|optAssemProduct|Cadeia de caracteres - contém o nome do produto.|  
|optAssemProductVersion|Cadeia de caracteres (também conhecido como InformationalVersion).|  
|optAssemCopyright|Cadeia de caracteres - contém as informações de direitos autorais.|  
|optAssemTrademark|Cadeia de caracteres - contém as informações de marca.|  
|optAssemKeyFile|Cadeia de caracteres (nome de arquivo).|  
|optAssemKeyName|Cadeia de caracteres (o nome da chave).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (também conhecido como DelaySign).|  
|optAssemFileVersion|Cadeia de caracteres - codificada como "Major" – mesmo que ProductVersion.|  
|optAssemSatelliteVer|Cadeia de caracteres - codificada como "Major".|  
|optLastAssemOption|Um contador do número de elementos.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** alink.h  
  
 **Biblioteca**: ALink  
  
## <a name="see-also"></a>Consulte também

- [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)

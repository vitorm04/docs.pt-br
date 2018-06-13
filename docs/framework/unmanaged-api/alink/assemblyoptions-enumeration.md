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
ms.openlocfilehash: e3926a0d49b2db02cf52a3cc943b05edc4cc36a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406261"
---
# <a name="assemblyoptions-enumeration"></a>Enumeração AssemblyOptions
Enumera as opções de assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|optAssemTitle|Cadeia de caracteres – representa o título do assembly.|  
|optAssemDescription|Cadeia de caracteres - contém a descrição do assembly.|  
|optAssemConfig|Cadeia de caracteres - contém a configuração de assembly.|  
|optAssemOS|Cadeia de caracteres - codificada como: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|Cadeia de caracteres - contém a localidade de assembly.|  
|optAssemVersion|Cadeia de caracteres - codificada como: "Revision".|  
|optAssemCompany|Cadeia de caracteres - contém a empresa.|  
|optAssemProduct|Cadeia de caracteres - contém o nome do produto.|  
|optAssemProductVersion|Cadeia de caracteres (também conhecido como InformationalVersion).|  
|optAssemCopyright|Cadeia de caracteres - contém as informações de direitos autorais.|  
|optAssemTrademark|Cadeia de caracteres - contém as informações de marca comercial.|  
|optAssemKeyFile|Cadeia de caracteres (nome de arquivo).|  
|optAssemKeyName|Cadeia de caracteres (o nome da chave).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (também conhecido como DelaySign).|  
|optAssemFileVersion|Cadeia de caracteres - codificada como "Revision" – mesmo que ProductVersion.|  
|optAssemSatelliteVer|Cadeia de caracteres - codificada como "Revision".|  
|optLastAssemOption|Um contador do número de elementos.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** alink.h  
  
 **Biblioteca**: arquivo  
  
## <a name="see-also"></a>Consulte também  
 [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)

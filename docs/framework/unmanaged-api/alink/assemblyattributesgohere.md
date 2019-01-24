---
title: AssemblyAttributesGoHere
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHere
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cde96ed9089416fa5febe55e49b4109cfeb11f40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722134"
---
# <a name="assemblyattributesgohere"></a>AssemblyAttributesGoHere
Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a>Comentários  
 Referências a esse tipo podem ser incorporadas dentro dos netmodules cujas fontes contêm atributos de assembly personalizado. Ao criar um manifesto do assembly de um ou mais dos netmodules que contêm referências a esses tipos, o ALink usa informações associadas a essas referências para emissão de atributos personalizados real. Como tal, esse tipo nunca é instanciado e as referências a ele são usadas apenas como parte do processo de compilação e nenhuma finalidade no assembly final.  
  
 Referências a esse tipo de indicam os atributos personalizados que não estão relacionadas à segurança e não uso múltiplo.  
  
 Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados em <xref:System.Runtime.CompilerServices>.  
  
## <a name="requirements"></a>Requisitos  
 mscorlib.dll  
  
## <a name="see-also"></a>Consulte também
- [AssemblyAttributesGoHereM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)

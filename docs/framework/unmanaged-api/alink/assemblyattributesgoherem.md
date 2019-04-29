---
title: Classe AssemblyAttributesGoHereM (CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69167fda194e9d916f44751fd1f9dcee92822377
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790137"
---
# <a name="assemblyattributesgoherem-class"></a>Classe AssemblyAttributesGoHereM

Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.

## <a name="syntax"></a>Sintaxe

```csharp
internal sealed class AssemblyAttributesGoHereM
```

## <a name="remarks"></a>Comentários

Referências a esse tipo podem ser incorporadas dentro dos netmodules cujas fontes contêm atributos de assembly personalizado. Ao criar um manifesto do assembly de um ou mais dos netmodules que contêm referências a esses tipos, o ALink usa informações associadas a essas referências para emissão de atributos personalizados real. Como tal, esse tipo nunca é instanciado e as referências a ele são usadas apenas como parte do processo de compilação e nenhuma finalidade no assembly final.

Referências a esse tipo de indicam atributos personalizados que não estão relacionadas à segurança, mas uso múltiplo.

Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados no <xref:System.Runtime.CompilerServices> namespace.

## <a name="requirements"></a>Requisitos

mscorlib.dll

## <a name="see-also"></a>Consulte também

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)

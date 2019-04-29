---
title: Classe AssemblyAttributesGoHereSM (CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01b156ed9c318e71a408ea10f2744911a85faedc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790332"
---
# <a name="assemblyattributesgoheresm-class"></a>Classe AssemblyAttributesGoHereSM

Usado pelo ALink como um espaço reservado para armazenar informações sobre atributos personalizados.

## <a name="syntax"></a>Sintaxe

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a>Comentários

Referências a esse tipo podem ser incorporadas dentro dos netmodules cujas fontes contêm atributos de assembly personalizado. Ao criar um manifesto do assembly de um ou mais dos netmodules que contêm referências a esses tipos, o ALink usa informações associadas a essas referências para emissão de atributos personalizados real. Como tal, esse tipo nunca é instanciado e as referências a ele são usadas apenas como parte do processo de compilação e nenhuma finalidade no assembly final.

Referências a esse tipo de indicam os atributos personalizados que estão relacionada e uso múltiplo de segurança.

Esses tipos são marcados como "internos" dentro do .NET Framework e estão localizados no <xref:System.Runtime.CompilerServices> namespace.

## <a name="requirements"></a>Requisitos

mscorlib.dll

## <a name="see-also"></a>Consulte também

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)

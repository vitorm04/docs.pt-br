---
title: A referência de assembly amigável <reference> é inválida.
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 72c030d18d5339908c5088e104f6a8ad3e76943b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874091"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>A referência de assembly amigável \<reference> é inválida.

A referência do assembly Friend \<reference> é inválida. O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.  
  
 O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Construtor de atributo identifica um assembly de nome forte, mas não inclui um `PublicKey` atributo.  
  
 **ID do erro:** BC31535  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Determine a chave pública para o assembly Friend de nome forte. Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Construtor de atributo usando o `PublicKey` atributo.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Reflection.AssemblyName>
- [Assemblies amigáveis](../../../standard/assembly/friend.md)

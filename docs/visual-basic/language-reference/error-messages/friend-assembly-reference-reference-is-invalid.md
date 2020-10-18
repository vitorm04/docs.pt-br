---
title: A referência de assembly amigável <reference> é inválida.
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: a42dd99ffaa06dce4823ce5d022fac02ae99c6bd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160705"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a>BC31535: a referência do assembly Friend \<reference> é inválida

A referência do assembly Friend \<reference> é inválida. O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.

 O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Construtor de atributo identifica um assembly de nome forte, mas não inclui um `PublicKey` atributo.

 **ID do erro:** BC31535

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Determine a chave pública para o assembly Friend de nome forte. Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Construtor de atributo usando o `PublicKey` atributo.

## <a name="see-also"></a>Veja também

- <xref:System.Reflection.AssemblyName>
- [Assemblies amigáveis](../../../standard/assembly/friend.md)

---
title: Referência de assembly Friend &lt;referência&gt; é inválido
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: c47fae9c60dc04ee02b1ff015d3dde87b8920c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Referência de assembly Friend &lt;referência&gt; é inválido
Referência de assembly Friend \<referência > é inválido. O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.  
  
 O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.  
  
 **ID do erro:** BC31535  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine a chave pública do assembly friend com nome forte. Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo usando o `PublicKey` atributo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.AssemblyName>  
 [Assemblies Amigáveis](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 


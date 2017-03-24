---
title: "Referência de assembly Friend &lt;referência&gt; inválido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
dev_langs:
- VB
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: 5
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9d66ae81c2311023e163a89d6076450ae5ca6ba2
ms.lasthandoff: 03/13/2017

---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Referência de assembly Friend &lt;referência&gt; é inválido
Referência de assembly Friend \<referência > é inválido. Assemblies assinados com nome forte devem especificar uma chave pública em suas declarações InternalsVisibleTo.  
  
 O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>Construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
 **ID do erro:** BC31535  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine a chave pública do assembly de nome forte amigo. Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>Construtor de atributo usando o `PublicKey` atributo.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName>   
 [Assemblies amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)   
 [Como criar assemblies amigáveis assinados](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)

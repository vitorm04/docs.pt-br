---
title: "Referência de assembly Friend &lt;referência&gt; é inválido"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Referência de assembly Friend &lt;referência&gt; é inválido
Referência de assembly Friend \<referência > é inválido. O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.  
  
 O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.  
  
 **ID do erro:** BC31535  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine a chave pública do assembly friend com nome forte. Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo usando o `PublicKey` atributo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Reflection.AssemblyName>  
 [Assemblies Amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [Como criar assemblies amigáveis assinados](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)

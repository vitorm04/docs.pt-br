---
title: "A refer&#234;ncia de assembly amig&#225;vel &lt;reference&gt; &#233; inv&#225;lida. | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31535"
  - "bc31535"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31535"
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A refer&#234;ncia de assembly amig&#225;vel &lt;reference&gt; &#233; inv&#225;lida.
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Referência de assembly Friend \<reference\> não é válido.Conjuntos de módulos \(assemblies\) de alta segurança devem especificar um chave pública em suas declarações InternalsVisibleTo.  
  
 O nome do assembly passado para o construtor de atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> identifica um assembly de alta segurança, mas ele não inclui um atributo `PublicKey`.  
  
 **Identificação do erro:**  BC31535  
  
### Para corrigir este erro  
  
1.  Determine a chave pública para o assembly autorizado de alta segurança.  Inclua a chave pública como parte do nome do conjunto de módulos \(assembly\) passado para o construtor de atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> usando o atributo `PublicKey`.  
  
## Consulte também  
 <xref:System.Reflection.AssemblyName>   
 [Assemblies amigáveis](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Como criar assemblies amigáveis assinados](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)
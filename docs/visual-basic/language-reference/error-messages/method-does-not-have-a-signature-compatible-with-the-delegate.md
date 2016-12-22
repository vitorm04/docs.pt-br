---
title: "O m&#233;todo n&#227;o tem uma assinatura compat&#237;vel com o delegado | Microsoft Docs"
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
  - "bc36563"
  - "vbc36563"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36563"
ms.assetid: 3ca8b873-e98d-419b-95f2-d75bd2a9eb6c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O m&#233;todo n&#227;o tem uma assinatura compat&#237;vel com o delegado
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Há uma incompatibilidade entre as assinaturas do método e do delegado que você está tentando usar.  A declaração `Delegate` define tipos de parâmetro e retorna tipos da classe delegada.  Qualquer procedimento que possui parâmetros compatíveis de tipos e tipos de retorno compatíveis pode ser usado para criar uma instância do tipo delegado.  
  
 **Identificação do Erro**: BC36563  
  
## Consulte também  
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Resolução de sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
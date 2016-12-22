---
title: "Operador AddressOf (Visual Basic) | Microsoft Docs"
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
  - "AddressOf"
  - "vb.AddressOf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "endereços, transmitindo para procedimentos de API"
  - "Operador AddressOf"
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador AddressOf (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cria uma instância delegada de procedimento que refere\-se ao procedimento específico.  
  
## Sintaxe  
  
```  
  
AddressOf procedurename  
```  
  
## Partes  
 `procedurename`  
 Obrigatório.  Especifica o procedimento para ser referenciado pelo delegado de procedimento recém\-criado.  
  
## Comentários  
 O operador `AddressOf` cria um delegado de função que aponta para a função especificada por `procedurename`.  Quando o procedimento especificado é um método de instância, então o delegado de função refere\-se tanto à instância quanto ao método.  Então, quando o delegado de função é invocado, o método especificado da instância especificada é chamado.  
  
 O operador `AddressOf` pode ser usado como o operando do construtor delegado ou pode ser usado num contexto no qual  o tipo do delegado pode ser determinado pelo compilador.  
  
## Exemplo  
 Este exemplo usa o operador `AddressOf` para designar um delegado para manipular o evento `Click` de um botão.  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## Exemplo  
 O exemplo a seguir usa o operador `AddressOf` para designar a função de inicialização para uma linha.  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## Consulte também  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)
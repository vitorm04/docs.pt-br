---
title: "Instru&#231;&#227;o Implements | Microsoft Docs"
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
  - "vb.Implements"
  - "Implements"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instrução Implements"
  - "instrução Implements, sintaxe"
  - "implementação de interface, instrução Implements"
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Implements
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica uma ou mais interfaces, ou membros de inteface, que devem ser implementadas na definição da classe ou estrutura onde aparece.  
  
## Sintaxe  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## Partes  
 `interfacename`  
 Obrigatório.  Uma interface cujas propriedades, procedimentos, e eventos estão para ser implementados por membros correspondentes de classes ou estruturas.  
  
 `interfacemember`  
 Obrigatório.  O membro da interface que está sendo implementado.  
  
## Comentários  
 Uma interface é uma coleção de protótipos representando os membros \(propriedades, procedimentos e eventos\) que a interface encapsula.  Interfaces contém unicamente as declaração para membros; classes e estruturas implementam esses membros.  Para obter mais informações, consulte [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md).  
  
 A declaração `Implements` deve seguir a declaração `Class` or `Structure` imediatamente.  
  
 Quando você implementa uma interface, você deve implementar todos os membros declarados na mesma.  Omitir qualquer membro é considerado um erro de sintaxe.  Para implementar um membro individual, você deve especificar a palavra chave [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) \( que é separada da declaração `Implements`\) quando você declara o membro na classe ou estrutura.  Para obter mais informações, consulte [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md).  
  
 Classes podem usar implementações de propriedades e procedimentos [Particular](../../../visual-basic/language-reference/modifiers/private.md), mas esses membros são acessíveis somente chamando uma instância da classe implementada dentro de uma variável declarada com o tipo da interface.  
  
## Exemplo  
 O seguinte exemplo mostra como cusar a declaração `Implements` para implementar membros de uma interface.  Ele define uma interface nomeada como `ICustomerInfo` com um evento, uma propriedade e um procedimento.  A classe `customerInfo` implementa todos os membros definidos na interface.  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 Note que a classe `customerInfo` usa a  declaração `Implements` num código fonte separado para indicar que a classe implementa todos os membros da interface `ICustomerInfo`.  Depois cada membro na classe usa a palavra chave `Implements` como parte de sua declaração de membros para indicar que cada um implementa o membro da interface.  
  
## Exemplo  
 Os próximos dois procedimentos mostram como você poderia usar a interface implementada no exemplo anterior.  Para testar essa implementação, adicione esses procedimentos no seu projeto e chame o procedimento `testImplements`.  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## Consulte também  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)   
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)
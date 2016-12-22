---
title: "Diferen&#231;as entre passar um argumento por valor e por refer&#234;ncia (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "argumentos [Visual Basic], transmitindo por valor ou por referência"
  - "Palavra-chave ByRef, transmitindo argumentos por referência"
  - "Palavra-chave ByVal, transmitindo argumentos por valor"
  - "procedimentos, argumentos de passagem"
  - "código do Visual Basic, procedimentos"
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diferen&#231;as entre passar um argumento por valor e por refer&#234;ncia (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você passa um ou mais argumentos para um procedimento, cada argumento corresponde a um elemento de programação oculto no código de chamada.  Você passar tanto o valor desse elemento como uma referência a ele.  Isso é conhecido como *Mecanismo de passagem*.  
  
## Passagem por valor  
 Você passa um argumento *por favor* especificando a palavra\-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) para o parâmetro correspondente na definição do procedimento.  Quando você usa este mecanismo de passagem, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copia o valor do elemento de programação oculto numa variável local do procedimento.  O çodigo do procedimento não tem nenhum acesso ao elemento no código de chamada.  
  
## Passagem por referência  
 Você passa um argumento *por referência* especificando a palavra\-chave [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para o parâmetro correspondente na definição do procedimento.  Quando você usa esse mecanismo de passagem, o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] dá ao procedimento uma referência direta ao elemento oculto no código de chamada.  
  
## Mecanismo de passagem e Tipo do Elemento  
 A escolha do mecanismo de passagem não é a mesma dependendo do tipo do elemento.  Passagem por valor ou referência se refere ao que o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece ao código do procedimento.  Um tipo de valor ou tipo de referência se refere a como o elemento de programação é armazenado na memória.  
  
 Entretanto, o mecanismo de passagem e tipo de elemento se relacionam.  O valor de um tipo de referência é um ponteiro para os dados em algum lugar da memória.  Isso significa que quando você passa um tipo de referência por valor, o código do procedimento tem um ponteiro para os dados do elemento, mesmo que ele não possa acessar o elemento em si.  Por exemplo, se o elemento é uma variável array, o código do procedimento não tem acesso à variável em si, mas ele pode acessar os membros do array.  
  
## Capacidade de Modificar  
 Quando você passa um elemento não\-modificável como argumento, o procedimento nunca pode modificá\-lo no código de chamada, se é passado `ByVal` ou `ByRef`.  
  
 Para um elemento modificável, a seguinte tabela resume a interação entre o tipo de elemento e o mecanismo de passagem.  
  
|Tipo de elemento|Passado `ByVal`|Passado `ByRef`|  
|----------------------|---------------------|---------------------|  
|Tipo de valor \(contém apenas um valor\)|O procedimento não pode mudar a variável ou qualquer um dos seus membros.|O procedimento pode mudar a variável e seus membros.|  
|Tipo de referência \(contém um ponteiro para a instância de classe ou estrutura\).|O procedimento não pode mudar a variável mas pode mudar membros da instância para qual ele aponta.|O procedimento pode mudar a variável e mudar membros da instância para qual ele aponta.|  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Como passar argumentos para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Diferenças entre argumentos modificáveis e não modificáveis](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Como alterar o valor de um argumento de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [Como proteger um argumento de procedimento contra alterações de valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Como forçar um argumento a ser passado por Valor](../Topic/How%20to:%20Force%20an%20Argument%20to%20Be%20Passed%20by%20Value%20\(Visual%20Basic\).md)   
 [Passando argumentos por posição e nome](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
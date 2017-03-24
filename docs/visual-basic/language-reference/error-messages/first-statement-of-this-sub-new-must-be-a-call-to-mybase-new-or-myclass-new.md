---
title: "A primeira instrução deste &quot;Sub New&quot; deve ser uma chamada para &quot;MyBase. New&quot; ou &quot;MyClass. New&quot; (nenhum construtor acessível sem parâmetros) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30148
- vbc30148
dev_langs:
- VB
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: 11
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
ms.openlocfilehash: 6459d5ed57b805bee6ffcb0d5cbcc54ac168efc0
ms.lasthandoff: 03/13/2017

---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>A primeira instrução deste 'Sub New' deve ser uma chamada para 'MyBase. New' ou 'MyClass. New' (nenhum construtor acessível sem parâmetros)
A primeira instrução deste 'Sub New' deve ser uma chamada para 'MyBase. New' ou 'MyClass. New' porque classe base\<basename >' de '\<derivedname >' não tem um 'Sub New' acessível que pode ser chamado sem argumentos.  
  
 Em uma classe derivada, cada construtor deve chamar um construtor de classe base (`MyBase.New`). Se a classe base tem um construtor sem parâmetros que seja acessível a classes derivadas, `MyBase.New` pode ser chamado automaticamente. Caso contrário, um construtor de classe base deve ser chamado com parâmetros, e isso não pode ser feito automaticamente. Nesse caso, a primeira instrução de cada construtor de classe derivada deve chamar um construtor com parâmetros na classe base ou chamar outro construtor na classe derivada que faz um construtor de classe base chamada.  
  
 **ID do erro:** BC30148  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Chamar `MyBase.New` fornecendo os parâmetros necessários, ou chamar um construtor ponto que faz uma chamada tal.  
  
     Por exemplo, se a classe base tem um construtor que é declarado como `Public Sub New(ByVal index as Integer)`, a primeira instrução em derivados construtor de classe pode ser `MyBase.New(100)`.  
  
## <a name="see-also"></a>Consulte também  
 [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

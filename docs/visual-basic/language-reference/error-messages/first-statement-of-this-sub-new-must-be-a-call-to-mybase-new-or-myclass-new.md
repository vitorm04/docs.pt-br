---
title: A primeira instrução &#39;Sub New&#39; deve ser uma chamada para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; (nenhum construtor acessível sem parâmetros)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 3b24385932700a4843ae295bc82ef9529cc86b9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>A primeira instrução &#39;Sub New&#39; deve ser uma chamada para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; (nenhum construtor acessível sem parâmetros)
A primeira instrução deste 'Sub New' deve ser uma chamada para 'MyBase. New' ou 'MyClass. New' porque classe base\<nome base >' de '\<derivedname >' não tem um 'Sub New' acessível que pode ser chamado sem argumentos.  
  
 Em uma classe derivada, cada construtor deve chamar um construtor de classe base (`MyBase.New`). Se a classe base tem um construtor sem parâmetros que seja acessível a classes derivadas, `MyBase.New` pode ser chamado automaticamente. Caso contrário, um construtor de classe base deve ser chamado com parâmetros, e isso não pode ser feito automaticamente. Nesse caso, a primeira instrução de cada construtor de classe derivada deve chamar um construtor com parâmetros na classe base ou chamar outro construtor na classe derivada que faz com que um construtor de classe base chamar.  
  
 **ID do erro:** BC30148  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Chamar `MyBase.New` fornecendo os parâmetros necessários, ou chamar um construtor ponto que faz uma chamada tal.  
  
     Por exemplo, se a classe base tem um construtor que é declarado como `Public Sub New(ByVal index as Integer)`, a primeira instrução em derivada construtor da classe pode ser `MyBase.New(100)`.  
  
## <a name="see-also"></a>Consulte também  
 [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

---
title: A primeira instrução deste ' Sub New ' deve ser uma chamada para 'MyBase.New' ou 'MyClass.New' (nenhum construtor acessível sem parâmetros)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: d29d7609f8f3f38eadda9a9c763f3ba8e6b99e61
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365081"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a>A primeira instrução deste ' Sub New ' deve ser uma chamada para 'MyBase.New' ou 'MyClass.New' (nenhum construtor acessível sem parâmetros)
A primeira instrução deste 'Sub New' deve ser uma chamada para 'MyBase. New' ou 'MyClass. New' porque classe base\<basename >' de '\<derivedname >' não tem um 'Sub New' acessível que pode ser chamado sem argumentos.  
  
 Em uma classe derivada, cada construtor deve chamar um construtor de classe base (`MyBase.New`). Se a classe base tem um construtor sem parâmetros acessível a classes derivadas, `MyBase.New` pode ser chamado automaticamente. Caso contrário, um construtor de classe base deve ser chamado com parâmetros, e isso não pode ser feito automaticamente. Nesse caso, a primeira instrução de cada construtor de classe derivada deve chamar um construtor parametrizado na classe base ou chamar outro construtor na classe derivada que faz um construtor de classe base chamada.  
  
 **ID do erro:** BC30148  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Chamar `MyBase.New` fornecendo os parâmetros necessários ou chamar um construtor de mesmo nível que torna essa chamada.  
  
     Por exemplo, se a classe base tem um construtor que é declarado como `Public Sub New(ByVal index as Integer)`, a primeira instrução em derivado construtor de classe pode ser `MyBase.New(100)`.  
  
## <a name="see-also"></a>Consulte também
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

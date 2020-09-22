---
title: "'<typename>' não pode ser herdado de <type> '<basetypename>' porque ele expande o acesso do <type> base fora do assembly"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 5adb5a74c220c7b2f95ac7370040a7fa2bd34299
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872064"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<typename>' não pode ser herdado de \<type> '\<basetypename>' porque ele expande o acesso do \<type> base fora do assembly

Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.  
  
 Por exemplo, uma `Public` interface herda de uma `Friend` interface ou uma `Protected` classe herda de uma `Private` classe. Isso expõe a classe base ou a interface para acessar além do nível pretendido.  
  
 **ID do erro:** BC30910  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Altere o nível de acesso da classe derivada ou da interface para que seja pelo menos tão restritiva quanto a classe base ou interface.  
  
     - ou -  
  
- Se você precisar do nível de acesso menos restritivo, remova a `Inherits` instrução. Não é possível herdar de uma classe base ou interface mais restrita.  
  
## <a name="see-also"></a>Confira também

- [Instrução Class](../statements/class-statement.md)
- [Instrução Interface](../statements/interface-statement.md)
- [Instrução Inherits](../statements/inherits-statement.md)
- [Níveis de acesso no Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)

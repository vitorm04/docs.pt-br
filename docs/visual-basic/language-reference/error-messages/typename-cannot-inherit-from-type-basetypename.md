---
title: "'<typename>' não pode ser herdado de <type> '<basetypename>' porque ele expande o acesso do <type> base fora do assembly"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764355"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>'\<typename >' não pode herdar de \<tipo > '\<basetypename >' porque ele expande o acesso da base de \<tipo > fora do assembly
Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.  
  
 Por exemplo, uma `Public` interface herda de uma `Friend` interface, ou um `Protected` classe herda de uma `Private` classe. Isso expõe a classe base ou interface para acesso além do nível desejado.  
  
 **ID do erro:** BC30910  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Altere o nível de acesso da classe derivada ou interface seja pelo menos tão restritivo quanto da classe base ou interface.  
  
     - ou -  
  
- Se você exigir o nível de acesso menos restritivo, remova o `Inherits` instrução. Você não pode herdar de uma classe base mais restrito ou interface.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)

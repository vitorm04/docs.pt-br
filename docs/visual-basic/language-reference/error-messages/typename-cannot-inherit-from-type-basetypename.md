---
title: "'<typename>' não pode ser herdado de <type> '<basetypename>' porque ele expande o acesso do <type> base fora do assembly"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 5c019f9d74b11e48aa05a1480b9449fa28488b43
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161836"
---
# <a name="bc30910-typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>BC30910: ' \<typename> ' não pode herdar de \<type> ' \<basetypename> ' porque ele expande o acesso da base \<type> fora do assembly

Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.

 Por exemplo, uma `Public` interface herda de uma `Friend` interface ou uma `Protected` classe herda de uma `Private` classe. Isso expõe a classe base ou a interface para acessar além do nível pretendido.

 **ID do erro:** BC30910

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Altere o nível de acesso da classe derivada ou da interface para que seja pelo menos tão restritiva quanto a classe base ou interface.

     - ou -

- Se você precisar do nível de acesso menos restritivo, remova a `Inherits` instrução. Não é possível herdar de uma classe base ou interface mais restrita.

## <a name="see-also"></a>Veja também

- [Instrução Class](../statements/class-statement.md)
- [Instrução Interface](../statements/interface-statement.md)
- [Instrução Inherits](../statements/inherits-statement.md)
- [Níveis de acesso no Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)

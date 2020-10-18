---
title: O tipo '<typename>' não tem construtores
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 249bcb7020f26c7c43d560e91ef7a34e4dc64470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161173"
---
# <a name="bc30251-type-typename-has-no-constructors"></a>BC30251: o tipo ' \<typename> ' não tem construtores

Um tipo não suporta uma chamada para `Sub New()`. Uma possível causa é um compilador corrompido ou arquivo binário.

 **ID do erro:** BC30251

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Se o tipo estiver em um projeto diferente ou em um arquivo referenciado, reinstale o projeto ou arquivo.

2. Se o tipo estiver no mesmo projeto, recompile o assembly que contém o tipo.

3. Se o erro se repetir, reinstale o compilador Visual Basic.

4. Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.

## <a name="see-also"></a>Veja também

- [Objetos e classes](../../programming-guide/language-features/objects-and-classes/index.md)
- [Fale conosco](/visualstudio/ide/feedback-options)

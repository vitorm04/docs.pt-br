---
title: <type1>'<typename>' deve implementar '<membername>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a036097d778daae59ef3bbd74ab8507cd16e6e24
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161849"
---
# <a name="bc30154-type1typename-must-implement-membername-for-interface-interfacename"></a>BC30154: \<type1> ' \<typename> ' deve implementar ' \<membername> ' para a interface ' \<interfacename> '

' \<typename> ' deve implementar ' \<membername> ' para a interface ' \<interfacename> '. A implementação da propriedade deve ter especificadores ' ReadOnly '/' WriteOnly ' correspondentes.

 Declarações de classe ou estrutura para implementar uma interface, mas não implementa um procedimento, propriedade ou evento definido pela interface. Todos os membros da interface devem ser implementados.

 **ID do erro:** BC30154

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Declare um membro com o mesmo nome e assinatura, conforme definido na interface. Certifique-se de incluir pelo menos `End Function` a `End Sub` instrução, ou `End Property` .

2. Adicione uma `Implements` cláusula ao final da `Function` instrução,, `Sub` `Property` ou `Event` . Por exemplo:

    ```vb
    Public Event ItHappened() Implements IBaseInterface.ItHappened
    ```

3. Ao implementar uma propriedade, verifique se o `ReadOnly` ou o `WriteOnly` é usado da mesma maneira que na definição da interface.

4. Ao implementar uma propriedade, declare `Get` e `Set` procedimentos, conforme apropriado.

## <a name="see-also"></a>Veja também

- [Instrução Implements](../statements/implements-statement.md)
- [Interfaces](../../programming-guide/language-features/interfaces/index.md)

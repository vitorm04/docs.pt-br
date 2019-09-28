---
title: <type1>'<typename>' deve implementar '<methodname>' para interface '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591591"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1 > ' \<typename > ' deve implementar ' \<methodname > ' para a interface ' \<interfacename > '
Uma classe ou estrutura alega implementar uma interface, mas não implementa um procedimento definido pela interface. Todos os membros da interface devem ser implementados.  
  
 **ID do erro:** BC30149  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Declare um procedimento com o mesmo nome e assinatura, conforme definido na interface. Certifique-se de incluir pelo menos a instrução `End Function` ou `End Sub`.  
  
2. Adicione uma cláusula `Implements` ao final da instrução `Function` ou `Sub`. Por exemplo:  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

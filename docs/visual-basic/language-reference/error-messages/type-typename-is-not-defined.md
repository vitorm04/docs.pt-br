---
title: O tipo '<typename>' não está definido
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: c2675d61307d92da1710368668f43af3559060a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825026"
---
# <a name="type-typename-is-not-defined"></a>Tipo de '\<typename >' não está definido
A instrução faz referência a um tipo que não foi definida. Você pode definir um tipo em uma instrução de declaração, como `Enum`, `Structure`, `Class`, ou `Interface`.  
  
 **ID do erro:** BC30002  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que a definição de tipo e sua referência ambos usam a mesma ortografia.  
  
-   Certifique-se de que a definição de tipo é acessível para a referência. Por exemplo, se o tipo é em outro módulo e foi declarado `Private`, mova a definição de tipo para o módulo de referência ou declará-la `Public`.  
  
-   Certifique-se de que o namespace do tipo não é redefinido dentro de seu projeto. Se for, use o `Global` palavra-chave para qualificar totalmente o nome do tipo. Por exemplo, se um projeto define um namespace chamado `System`, o <xref:System.Object?displayProperty=nameWithType> tipo não pode ser acessado, a menos que ele seja totalmente qualificado com o `Global` palavra-chave: `Global.System.Object`.  
  
-   Se o tipo é definido, mas a biblioteca de objetos ou a biblioteca de tipo no qual ele é definido não está registrada no Visual Basic, clique em **adicionar referência** sobre o **projeto** menu e, em seguida, selecione o objeto apropriado biblioteca ou biblioteca de tipos.  
  
-   Certifique-se de que o tipo é em um assembly que é parte do perfil do .NET Framework de destino. Para obter mais informações, consulte [Solução de problemas de erros de definição de destino do .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Consulte também

- [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)

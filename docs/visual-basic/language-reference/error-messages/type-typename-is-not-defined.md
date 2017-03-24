---
title: "Tipo de &quot;&lt;typename&gt;&quot; não está definido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
dev_langs:
- VB
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
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
ms.openlocfilehash: 09aa7c535fd5e17ddcd0e743fb5ec17ebadd4f7d
ms.lasthandoff: 03/13/2017

---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Tipo de '&lt;typename&gt;' não está definido
A instrução faz referência a um tipo que não foi definida. Você pode definir um tipo em uma instrução de declaração, como `Enum`, `Structure`, `Class`, ou `Interface`.  
  
 **ID do erro:** BC30002  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que a definição de tipo e sua referência usam a mesma ortografia.  
  
-   Certifique-se de que a definição de tipo é acessível para a referência. Por exemplo, se o tipo estiver em outro módulo e foi declarado `Private`, mover a definição de tipo para o módulo de referência ou declare- `Public`.  
  
-   Certifique-se de que o namespace do tipo não é redefinido no seu projeto. Se for, use o `Global` palavra-chave para qualificar totalmente o nome do tipo. Por exemplo, se um projeto define um namespace chamado `System`, o <xref:System.Object?displayProperty=fullName>tipo não pode ser acessado, a menos que ele seja totalmente qualificado com o `Global` palavra-chave: `Global.System.Object`.</xref:System.Object?displayProperty=fullName>  
  
-   Se o tipo é definido, mas a biblioteca de objeto ou no qual ele é definido de biblioteca de tipos não está registrada no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], clique em **adicionar referência** sobre o **projeto** menu e, em seguida, selecione a biblioteca de objeto apropriado ou biblioteca de tipos.  
  
-   Certifique-se de que o tipo é em um assembly que é parte do perfil de destino do .NET Framework. Para obter mais informações, consulte [de solução de problemas de direcionamento erros do .NET Framework](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Consulte também  
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Gerenciando referências em um projeto](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)

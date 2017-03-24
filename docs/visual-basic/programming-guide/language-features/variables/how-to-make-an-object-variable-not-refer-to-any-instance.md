---
title: "Como: fazer um objeto variável não se referir a nenhuma instância (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Nothing keyword, variable assignment
- object variables, null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: 9
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
ms.openlocfilehash: a550a164035d8704baba8244dc840f51c8906457
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Como fazer uma variável de objeto não se referir a nenhuma instância (Visual Basic)
Você pode desassociar uma variável de objeto de qualquer instância do objeto definindo-a como [nada](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Para desassociar uma variável de objeto de qualquer instância do objeto  
  
-   Definir a variável `Nothing` em uma instrução de atribuição.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Programação robusta  
 Se seu código tentar acessar um membro de uma variável de objeto que foi definido como `Nothing`, um <xref:System.NullReferenceException>ocorre.</xref:System.NullReferenceException> Se você definir uma variável de objeto para `Nothing` com frequência, ou se for possível, a variável não é inicializada, ele é uma boa ideia colocar os acessos a membros em um `Try...Catch...Finally` bloco.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Se você usar uma variável de objeto para objetos que contêm dados confidenciais, você pode definir a variável `Nothing` quando você não está ativamente lidando com um desses objetos. Isso reduz a chance de códigos mal-intencionados acessem os dados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.NullReferenceException></xref:System.NullReferenceException>   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Atribuição de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Nada](../../../../visual-basic/language-reference/nothing.md)   
 [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Solução de problemas de exceções: System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)

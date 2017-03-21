---
title: "Sub ou função não definida (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
dev_langs:
- VB
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
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
ms.openlocfilehash: 7d32bc9c8f13b245e6333c4460cab541f6e9409e
ms.lasthandoff: 03/13/2017

---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub ou função não definida (Visual Basic)
A `Sub` ou `Function` deve ser definido para ser chamado. Possíveis causas do erro incluem:  
  
-   Digitar incorretamente o nome do procedimento.  
  
-   Tentar chamar um procedimento de outro projeto sem adicionar explicitamente uma referência a esse projeto no **referências** caixa de diálogo.  
  
-   Especificar um procedimento que não é visível para o procedimento de chamada.  
  
-   Declarar uma rotina de biblioteca de vínculo dinâmico (DLL) do Windows ou a rotina de recurso de código Macintosh que não está no recurso de biblioteca ou código especificado.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que o nome do procedimento esteja escrito corretamente.  
  
2.  Localizar o nome do projeto que contém o procedimento que você deseja chamar o **referências** caixa de diálogo. Se ele não aparecer, clique o **procurar** botão para procurá-lo. Marque a caixa de seleção à esquerda do nome do projeto e, em seguida, clique em **Okey**.  
  
3.  Verifique o nome da rotina.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Gerenciando referências em um projeto](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)

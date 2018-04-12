---
title: Sub ou função não definida (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub ou função não definida (Visual Basic)
Um `Sub` ou `Function` deve ser definido para ser chamado. Possíveis causas do erro incluem:  
  
-   Erros de ortografia do nome do procedimento.  
  
-   Tentativa de chamar um procedimento de outro projeto sem adicionar explicitamente uma referência ao projeto no **referências** caixa de diálogo.  
  
-   Especificar um procedimento que não é visível para o procedimento de chamada.  
  
-   Declarando uma rotina de biblioteca de vínculo dinâmico (DLL) do Windows ou a rotina de recurso de código de Macintosh não está no recurso de biblioteca ou de código especificado.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que o nome do procedimento esteja escrito corretamente.  
  
2.  Localizar o nome do projeto que contém o procedimento que você deseja chamar o **referências** caixa de diálogo. Se não aparecer, clique o **procurar** botão para procurar por ele. Marque a caixa de seleção à esquerda do nome do projeto e, em seguida, clique em **Okey**.  
  
3.  Verifique o nome da rotina.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Gerenciando referências em um projeto](/visualstudio/ide/managing-references-in-a-project)  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)

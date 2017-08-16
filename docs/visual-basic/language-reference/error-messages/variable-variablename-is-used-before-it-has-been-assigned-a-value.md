---
title: "Variável &quot;&lt;variablename&gt;&quot; é usada antes de receber um valor | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
dev_langs:
- VB
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 7ad1f392fae2f90e366277b7b531d96011648866
ms.lasthandoff: 03/13/2017

---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>Variável '&lt;variablename&gt;' é usada antes de receber um valor
Variável '\<NOMEDAVARIÁVEL >' é usada antes de receber um valor. Uma exceção de referência nula pode ocorrer em tempo de execução.  
  
 Um aplicativo tem pelo menos um caminho possível pelo seu código que lê uma variável antes que qualquer valor seja atribuído a ele.  
  
 Se nunca tiver sido atribuída um valor uma variável, ela armazena o valor padrão para seu tipo de dados. Para um tipo de dados de referência, o valor padrão é [nada](../../../visual-basic/language-reference/nothing.md). Ler uma variável de referência que tem um valor de `Nothing` pode causar um <xref:System.NullReferenceException>em algumas circunstâncias.</xref:System.NullReferenceException>  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42104  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique sua lógica de fluxo de controle e verifique se que a variável tem um valor válido antes do controle passa para qualquer instrução que lê-lo.  
  
-   Uma maneira de garantir que a variável sempre tem um valor válido é inicializá-la como parte de sua declaração. Consulte "Inicialização" [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Declaração de variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Solução de problemas de Variáveis](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)

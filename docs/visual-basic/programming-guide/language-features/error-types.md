---
title: Tipos de erros (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors, Visual Basic
- run-time errors, types of errors
- syntax errors, Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
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
ms.openlocfilehash: d48756b74baf757f043e68124d8b65c2f613e595
ms.lasthandoff: 03/13/2017

---
# <a name="error-types-visual-basic"></a>Tipos de erro (Visual Basic)
Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], erros (também chamado de *exceções*) se enquadram em uma das três categorias: erros de sintaxe, erros de tempo de execução e erros lógicos.  
  
## <a name="syntax-errors"></a>Erros de sintaxe  
 *Erros de sintaxe* são aqueles que aparecem enquanto você escreve código. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]verifica seu código conforme você digita no **Editor de códigos** janela e avisará se cometer um erro, como digitar incorretamente uma palavra ou usar um elemento de linguagem incorretamente. Erros de sintaxe são o tipo mais comum de erros. Você pode corrigi-los facilmente no ambiente de codificação assim que eles ocorrem.  
  
> [!NOTE]
>  O `Option Explicit` instrução é um meio de evitar erros de sintaxe. Força a declare, com antecedência, todas as variáveis a ser usado no aplicativo. Portanto, quando essas variáveis são usadas no código, qualquer erro tipográfico é detectado imediatamente e pode ser corrigido.  
  
## <a name="run-time-errors"></a>Erros de tempo de execução  
 *Erros de tempo de execução* são aqueles que aparecem somente após você compilar e executar seu código. Essas técnicas envolvem código que pode parecer estar correta, pois ela tem nenhum erro de sintaxe, mas que não será executado. Por exemplo, você pode escrever corretamente uma linha de código para abrir um arquivo. Mas se o arquivo estiver corrompido, o aplicativo não pode executar o `Open` função e ele deixará de ser executado. Você pode corrigir a maioria dos erros de tempo de execução por reescrever o código defeituoso, recompilar e executá-lo novamente.  
  
## <a name="logic-errors"></a>Erros de lógica  
 *Erros de lógica* são aqueles que aparecem depois que o aplicativo estiver em uso. Eles são mais resultados geralmente não desejados ou inesperados em resposta às ações do usuário. Por exemplo, uma chave digitada incorretamente ou outra fora da influência pode fazer com que seu aplicativo pare de funcionar dentro dos parâmetros esperados, ou completamente. Erros lógicos são geralmente o tipo mais difícil para corrigir, pois não é sempre claro onde eles se originam.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Noções básicas do depurador](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)

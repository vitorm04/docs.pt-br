---
title: Tipos de erro (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831560"
---
# <a name="error-types-visual-basic"></a>Tipos de erro (Visual Basic)
No Visual Basic, erros (também chamado de *exceções*) se enquadram em uma das três categorias: erros de sintaxe, erros de tempo de execução e erros lógicos.  
  
## <a name="syntax-errors"></a>Erros de sintaxe  
 *Erros de sintaxe* são aqueles que aparecem enquanto você escreve código. Visual Basic verifica seu código conforme você digita os **Editor de códigos** janela e o alerta se você cometer um erro, como digitar incorretamente uma palavra ou usar um elemento de linguagem incorretamente. Erros de sintaxe são o tipo mais comum de erros. Você pode corrigi-los facilmente no ambiente de codificação, assim que elas ocorrem.  
  
> [!NOTE]
>  O `Option Explicit` instrução é um meio de evitar erros de sintaxe. Isso força você a declara, com antecedência, todas as variáveis a ser usado no aplicativo. Portanto, quando essas variáveis são usadas no código, qualquer erro tipográfico é detectado imediatamente e pode ser corrigido.  
  
## <a name="run-time-errors"></a>Erros de tempo de execução  
 *Erros de tempo de execução* são aqueles que aparecem somente depois que você compilar e executar seu código. Essas técnicas envolvem código que pode parecer estar correta, em que ela tem nenhum erro de sintaxe, mas que não será executado. Por exemplo, você pode escrever uma linha de código para abrir um arquivo corretamente. Mas se o arquivo estiver corrompido, o aplicativo não é possível executar o `Open` função e ele será interrompido. Você pode corrigir a maioria dos erros de tempo de execução por reescrever o código com defeito e, em seguida, recompilar e executá-lo novamente.  
  
## <a name="logic-errors"></a>Erros de lógica  
 *Erros de lógica* são aqueles que aparecem depois que o aplicativo está em uso. Eles são a maioria dos resultados de muitas vezes não desejados ou inesperados em resposta às ações do usuário. Por exemplo, uma chave digitada incorretamente ou outra fora da influência pode fazer com que seu aplicativo para parar de funcionar dentro dos parâmetros esperados, ou completamente. Erros de lógica geralmente são o tipo mais difícil para corrigir, pois não é sempre claro onde eles se originam.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Noções básicas do depurador](/visualstudio/debugger/debugger-basics)

---
title: A variável '<variablename>' é usada antes de receber um valor
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 46551a917aeb794c8d35985076b67a315386f628
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819353"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>Variável '\<variablename >' é usada antes de receber um valor
Variável '\<variablename >' é usada antes de receber um valor. Uma exceção de referência nula poderia resultar em tempo de execução.  
  
 Um aplicativo tem pelo menos um caminho possível pelo seu código que lê uma variável antes de qualquer valor é atribuído a ele.  
  
 Se nunca tiver sido atribuída um valor uma variável, ele contém o valor padrão para seu tipo de dados. Para um tipo de dados de referência, o valor padrão é [nada](../../../visual-basic/language-reference/nothing.md). Leitura de uma variável de referência que tem um valor de `Nothing` pode causar um <xref:System.NullReferenceException> em algumas circunstâncias.  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42104  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique sua lógica de fluxo de controle e verifique se que a variável tem um valor válido antes do controle passa para qualquer instrução que lê-lo.  
  
-   É uma maneira de garantir que a variável sempre tem um valor válido para inicializá-lo como parte de sua declaração. Consulte "Inicialização" no [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Consulte também

- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Declaração de Variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Solução de problemas de Variáveis](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)

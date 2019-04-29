---
title: Instrução Stop (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 80d6734945324f3f517b256051486273f6b687ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783845"
---
# <a name="stop-statement-visual-basic"></a>Instrução Stop (Visual Basic)
Suspende a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar `Stop` instruções em qualquer lugar nos procedimentos para suspender a execução. Usando o `Stop` instrução é semelhante à configuração de um ponto de interrupção no código.  
  
 O `Stop` instrução suspende a execução, mas ao contrário `End`, não feche quaisquer arquivos ou desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).  
  
> [!NOTE]
>  Se o `Stop` instrução for encontrada no código que está em execução fora do ambiente de desenvolvimento integrado (IDE), o depurador é invocado. Isso é verdadeiro independentemente se o código foi compilado no modo de depuração ou de varejo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Stop` instrução para suspender a execução para cada iteração por meio de `For...Next` loop.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)

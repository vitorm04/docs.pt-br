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
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957614"
---
# <a name="stop-statement-visual-basic"></a>Instrução Stop (Visual Basic)
Suspende a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar `Stop` instruções em qualquer lugar em procedimentos para suspender a execução. O uso `Stop` da instrução é semelhante à definição de um ponto de interrupção no código.  
  
 A `Stop` instrução suspende a execução, mas, `End`ao contrário, não fecha nenhum arquivo ou limpa nenhuma variável, a menos que seja encontrado em um arquivo executável compilado (. exe).  
  
> [!NOTE]
> Se a `Stop` instrução for encontrada no código que está sendo executado fora do IDE (ambiente de desenvolvimento integrado), o depurador será invocado. Isso é verdadeiro independentemente de o código ter sido compilado no modo de depuração ou de varejo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a `Stop` instrução para suspender a execução para cada iteração por meio do `For...Next` loop.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)

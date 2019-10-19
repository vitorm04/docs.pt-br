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
ms.openlocfilehash: e9382ee34842fc3a3b4b23f71848bda602c99780
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583219"
---
# <a name="stop-statement-visual-basic"></a>Instrução Stop (Visual Basic)
Suspende a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar `Stop` instruções em qualquer lugar em procedimentos para suspender a execução. O uso da instrução `Stop` é semelhante à definição de um ponto de interrupção no código.  
  
 A instrução `Stop` suspende a execução, mas ao contrário de `End`, ela não fecha nenhum arquivo ou limpa nenhuma variável, a menos que seja encontrada em um arquivo executável compilado (. exe).  
  
> [!NOTE]
> Se a instrução `Stop` for encontrada no código que está sendo executado fora do IDE (ambiente de desenvolvimento integrado), o depurador será invocado. Isso é verdadeiro independentemente de o código ter sido compilado no modo de depuração ou de varejo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a instrução `Stop` para suspender a execução para cada iteração por meio do loop `For...Next`.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)

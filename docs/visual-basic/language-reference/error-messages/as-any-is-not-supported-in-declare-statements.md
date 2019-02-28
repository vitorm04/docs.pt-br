---
title: "'As Any' não é suportado em instruções 'Declare'"
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: b3fb3f208f3396f454388ec0c10406815fa957d8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974790"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a>'As Any' não é suportado em instruções 'Declare'
O `Any` tipo de dados foi usado com `Declare` instruções no Visual Basic 6.0 e versões anteriores, a fim de permitir o uso de argumentos que pode conter qualquer tipo de dados. Visual Basic oferece suporte a sobrecarga, no entanto e assim torna o `Any` obsoleto de tipo de dados.  
  
 **ID do erro:** BC30828  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declarar parâmetros do tipo específico que você deseja usar; Por exemplo.  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2.  Use o <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para especificar `As Any` quando `Void*` é esperado pelo procedimento sendo chamado.  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Passo a passo: fazer chamadas de APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Criando protótipos em código gerenciado](../../../framework/interop/creating-prototypes-in-managed-code.md)

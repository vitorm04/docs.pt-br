---
title: "'As Any' não é suportado em instruções 'Declare'"
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: bdf339e0d91106a6d6527e085608a06b0439951c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274067"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a>'As Any' não é suportado em instruções 'Declare'
O `Any` tipo de dados foi usado com `Declare` instruções no Visual Basic 6.0 e versões anteriores, a fim de permitir o uso de argumentos que pode conter qualquer tipo de dados. Visual Basic oferece suporte a sobrecarga, no entanto e assim torna o `Any` obsoleto de tipo de dados.  
  
 **ID do erro:** BC30828  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declarar parâmetros do tipo específico que você deseja usar; Por exemplo.  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  Use o <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para especificar `As Any` quando `Void*` é esperado pelo procedimento sendo chamado.  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Passo a passo: fazer chamadas de APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Criando protótipos em código gerenciado](../../../framework/interop/creating-prototypes-in-managed-code.md)

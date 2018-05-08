---
title: '&#39;Como qualquer&#39; não há suporte para &#39;Declare&#39; instruções'
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 34beaeb7178645d5a167d1b7b969bb3e4f500e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>&#39;Como qualquer&#39; não há suporte para &#39;Declare&#39; instruções
O `Any` tipo de dados foi usado com `Declare` instruções no Visual Basic 6.0 e versões anteriores para permitir o uso dos argumentos que pode conter qualquer tipo de dados. Visual Basic oferece suporte à sobrecarga, porém e assim torna o `Any` obsoleto de tipo de dados.  
  
 **ID do erro:** BC30828  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Declarar parâmetros do tipo específico que você deseja usar; Por exemplo.  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  Use o <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para especificar `As Any` quando `Void*` é esperado pelo procedimento que está sendo chamado.  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Criando protótipos em código gerenciado](../../../framework/interop/creating-prototypes-in-managed-code.md)

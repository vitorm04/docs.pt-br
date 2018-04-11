---
title: '&#39; Como qualquer &#39; Não há suporte para &#39; Declare &#39; instruções'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59120622688ee38d5b8f45c08dfc3ae40711fb8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>&#39; Como qualquer &#39; Não há suporte para &#39; Declare &#39; instruções
O `Any` tipo de dados foi usado com `Declare` instruções no Visual Basic 6.0 e versões anteriores para permitir o uso dos argumentos que pode conter qualquer tipo de dados. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]oferece suporte à sobrecarga, porém e assim torna o `Any` obsoleto de tipo de dados.  
  
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

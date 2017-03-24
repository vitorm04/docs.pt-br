---
title: "Propriedade &quot;&lt;propertyname&gt;&quot; não retorna um valor em todos os caminhos de código | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
dev_langs:
- VB
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
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
ms.openlocfilehash: e7c94d827761ad26d517b44a06734c5db4480a62
ms.lasthandoff: 03/13/2017

---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Propriedade '&lt;propertyname&gt;' não retorna um valor em todos os caminhos de código
Propriedade '\<propertyname >' não retorna um valor em todos os caminhos de código. Uma exceção de referência nula pode ocorrer em tempo de execução quando o resultado é usado.  
  
 Uma propriedade `Get` procedimento tem pelo menos um caminho possível pelo seu código que não retorna um valor.  
  
 Você pode retornar um valor de uma propriedade `Get` procedimento em qualquer uma das seguintes maneiras:  
  
-   Atribuir o valor ao nome da propriedade e, em seguida, executar um `Exit Property` instrução.  
  
-   Atribuir o valor ao nome da propriedade e, em seguida, execute o `End Get` instrução.  
  
-   Incluir o valor em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Se o controle passa para `Exit Property` ou `End Get` e você não tiver atribuído qualquer valor para o nome da propriedade, o `Get` procedimento retorna o valor padrão da propriedade tipo de dados. Para obter mais informações, consulte "Comportamento" em [declaração de função](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42107  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique sua lógica de fluxo de controle e verifique se que você atribuir um valor antes de cada instrução que produz um retorno.  
  
     É mais fácil garantir que cada retorno do procedimento retorna um valor se você usar sempre o `Return` instrução. Se você fizer isso, a última instrução antes `End Get` deve ser um `Return` instrução.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)

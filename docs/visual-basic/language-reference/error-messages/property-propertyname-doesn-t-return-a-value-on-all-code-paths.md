---
title: A propriedade '<propertyname>' não retorna um valor em todos os caminhos de código
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: a535a6b951dc9872109527f78d7de5f3fcdd3292
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971636"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>Propriedade '\<propertyname >' não retorna um valor em todos os caminhos de código
Propriedade '\<propertyname >' não retorna um valor em todos os caminhos de código. Uma exceção de referência nula pode ocorrer em tempo de execução quando o resultado é usado.  
  
 Uma propriedade `Get` procedimento tem pelo menos um caminho possível pelo seu código que não retorna um valor.  
  
 Você pode retornar um valor de uma propriedade `Get` procedimento em qualquer uma das seguintes maneiras:  
  
- Atribua o valor para o nome da propriedade e, em seguida, executar um `Exit Property` instrução.  
  
- Atribua o valor para o nome da propriedade e, em seguida, execute o `End Get` instrução.  
  
- Incluir o valor em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Se o controle passa para `Exit Property` ou `End Get` e você não tiver atribuído qualquer valor para o nome da propriedade, o `Get` procedimento retorna o valor padrão da propriedade tipo de dados. Para obter mais informações, consulte "Comportamento" em [instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42107  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique sua lógica de fluxo de controle e verifique se que você atribuir um valor antes de cada instrução que faz com que um retorno.  
  
     É mais fácil garantir que cada retorno do procedimento retorna um valor se você usar sempre o `Return` instrução. Se você fizer isso, a última instrução antes `End Get` deve ser um `Return` instrução.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)
